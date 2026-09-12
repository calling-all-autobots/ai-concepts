# Claude Sonnet 4.6 — 1M context (beta), stronger agentic search, web tools GA

- **Category:** ① Product release
- **Date:** 2026-02-17  ·  **What it affects:** model `claude-sonnet-4-6`; web search & web fetch tools; Claude Code
- **Sources:** https://www.anthropic.com/news/claude-sonnet-4-6 · https://docs.claude.com/en/docs/about-claude/models/overview

## In one line
Sonnet 4.6 is the mid-tier upgrade that inherits the 1M-token context (in beta) and much better agentic coding and computer use, at the same $3/$15 price as Sonnet 4.5.

## What actually changed
Released Feb 17, 2026 as `claude-sonnet-4-6`. Pricing is unchanged from Sonnet 4.5: **$3 / $15 per million input/output tokens**. It gains a **1M-token context window (beta)** — a capability that was Opus-exclusive months earlier — plus automatic context compaction (older turns summarized as you approach the limit, instead of hard truncation). Benchmarks: **80.2% SWE-bench Verified** (with prompt modification; standard score averaged over 10 trials) and materially higher OSWorld computer-use scores than prior Sonnets. In Claude Code preference tests, users preferred Sonnet 4.6 over Sonnet 4.5 ~70% of the time, and over Opus 4.5 ~59% of the time. Alongside the model, the **web search and web fetch tools reached general availability**, and they now automatically write and execute code to filter and process search results rather than dumping raw results into context.

## Why it matters
Sonnet is the workhorse tier — where most production traffic actually runs because of price/latency. Getting 1M context and near-frontier agentic-coding quality at unchanged Sonnet pricing shifts the default: many workloads that needed Opus for long context or hard coding can now sit on Sonnet. The web tools going GA (and doing code-based result filtering) is a quiet but real quality lever for grounded/agentic search — less junk in context, cheaper reads.

## Your point of view
- The headline is price/performance, not a new frontier: same $3/$15, but 1M context and ~80% SWE-bench means Sonnet 4.6 is the new sensible default for most agent and coding workloads.
- The "preferred over Opus 4.5 59% of the time" datapoint is the one to quote in a build-vs-cost discussion — it argues against reflexively reaching for the biggest model.
- Web search/fetch GA + code-based result filtering matters for anyone doing grounded retrieval: treat it as a first-class tool now, not a preview.

## What to do
- Re-benchmark your Opus-tier workloads on Sonnet 4.6 before renewing spend; if quality holds, the price gap is large.
- For long-context jobs, enable the 1M beta and lean on automatic compaction instead of custom truncation logic.
- If you use search grounding, adopt the GA web search/fetch tools rather than a bespoke scraper.

## Connects to
- [context windows](../../../01-foundations/05-context-windows.md)
- [retrieval](../../../04-retrieval-knowledge/24-retrieval.md)
- [grounding & citations](../../../04-retrieval-knowledge/27-grounding-citations.md)
- [build vs buy](../../../11-product-strategy/53-build-vs-buy.md)
- [cost & unit economics](../../../10-production-ops/51-cost-unit-economics.md)
