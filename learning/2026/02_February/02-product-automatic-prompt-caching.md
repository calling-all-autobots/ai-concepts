# Automatic prompt caching — one `cache_control`, no manual breakpoints

- **Category:** ① Product release
- **Date:** 2026-02-19  ·  **What it affects:** Messages API prompt caching (`cache_control`)
- **Sources:** https://docs.claude.com/en/docs/build-with-claude/prompt-caching · https://www.anthropic.com/news/prompt-caching

## In one line
You can now turn on prompt caching by adding a single top-level `cache_control` to the request, and Anthropic automatically places the cache breakpoint on the last cacheable block — no more hand-placing breakpoints on individual content blocks.

## What actually changed
Before this, using prompt caching meant manually attaching `cache_control` to each content block you wanted cached, and you were limited to a handful of explicit breakpoints — fiddly, and easy to get wrong in multi-turn chats. Automatic caching adds one top-level `cache_control` setting; the system applies the breakpoint to the last cacheable block, and the cache point moves forward as the conversation grows. That makes the accumulated conversation a stable, reusable prefix — a natural fit for chat-style and agentic loops where the prefix keeps extending. The economics are unchanged: cache writes cost ~1.25× base input tokens, cache reads ~0.1× — a ~90% discount on the cached prefix. (Note on TTL: through early March 2026 the platform default TTL was 1 hour, then reverted to 5 minutes around March 6–7, so during February the longer window was in effect.)

Same-day housekeeping worth pinning to memory: **Claude Sonnet 3.7 and Claude Haiku 3.5 were both retired on 2026-02-19** — calls to those model IDs now error, so pin to a current model (e.g. `claude-sonnet-4-6`) and check the deprecations page rather than trusting an old ID to keep working.

## Why it matters
Manual breakpoint placement was a real source of "why is my cache not hitting" bugs, especially in agents where the prompt grows every turn. Automatic caching removes the footgun and makes the highest-leverage cost lever in the API (a ~90% read discount on stable context) trivial to switch on. For a PM, this is a cost-and-latency story: long system prompts, tool schemas, and RAG context become cheap-to-reuse by default.

## Your point of view
- This is a "make the good thing the easy thing" change — caching was always the biggest cost lever; now it is one field instead of careful block surgery.
- The mental model to teach: the cached prefix is a moving window that extends forward each turn, so it rewards keeping stable content (system prompt, tools, docs) at the front and volatile content at the back.
- TTL is a moving target — verify the current default before promising savings, and be explicit about it in cost models.

## What to do
- Add a single top-level `cache_control` to chat/agent requests and confirm cache-read tokens in the usage response.
- Order prompts prefix-stable-first (system prompt, tool defs, retrieved docs) then the changing turn, to maximize hits.
- Audit code and jobs for retired model IDs (`claude-3-7-sonnet*`, `claude-3-5-haiku*`) and repoint them.

## Connects to
- [prompt caching](../../../05-prompting/31-prompt-caching.md)
- [KV caching](../../../05-prompting/30-kv-caching.md)
- [cost & unit economics](../../../10-production-ops/51-cost-unit-economics.md)
- [model ID & versioning](../../../dev-surfaces/07-model-id-versioning.md)
