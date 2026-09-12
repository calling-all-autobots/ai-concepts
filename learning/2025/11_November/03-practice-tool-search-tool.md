# Advanced tool use: the Tool Search Tool (on-demand tool discovery)

- **Category:** ② New best practice
- **Date:** 2025-11-24  ·  **What it affects:** tool/MCP-heavy agents on the Claude Developer Platform (beta header `advanced-tool-use-2025-11-20`)
- **Sources:** https://www.anthropic.com/engineering/advanced-tool-use

## In one line
Instead of loading every tool definition into the prompt up front, mark tools `defer_loading: true` and let Claude search for the ones it needs — cutting tool-definition context from ~72K tokens to ~500 while *improving* tool-selection accuracy.

## What actually changed
Anthropic shipped three "advanced tool use" features (beta). The headline is the **Tool Search Tool**:

- **Mechanism:** tools tagged `"defer_loading": true` are kept out of the initial prompt; Claude calls a search tool (`"type": "tool_search_tool_regex_20251119"`, regex/BM25-based) to discover and load only the definitions it needs, on demand.
- **Token impact:** ~72K tokens for 50+ MCP tools drops to **~500 tokens upfront — an ~85% reduction.** One comparison preserved 191,300 tokens of usable context vs 122,800 the traditional way.
- **Accuracy, not just savings:** with Tool Search enabled, tool-selection accuracy rose from **49% → 74% on Opus 4, and 79.5% → 88.1% on Opus 4.5.** Fewer definitions in context means less to confuse the model.
- **Caching-safe:** because deferred tools are never in the initial prompt, prompt caching isn't broken.

Two companion features shipped alongside: **Programmatic Tool Calling** (Claude writes code that calls tools and filters outputs before they hit context — average 43,588 → 27,297 tokens, a 37% cut on complex research; gated by `"allowed_callers": ["code_execution_20250825"]`), and **Tool Use Examples** (`"input_examples"` arrays showing realistic calls — accuracy 72% → 90% on complex parameter handling).

## Why it matters
As agents connect to dozens of MCP servers, tool definitions quietly become the biggest fixed cost in every request — paid on every turn, before any work happens. The counter-intuitive finding is that *loading fewer tools makes the model better*, not just cheaper: a smaller, relevant tool set reduces mis-selection. This flips the instinct to "expose everything just in case."

## Your point of view
- Tool bloat is now a solved context problem — but only if you opt in with `defer_loading`. Exposing 50 tools eagerly is an anti-pattern.
- The accuracy gain (79.5%→88.1% on Opus 4.5) is the real story: this is a quality lever disguised as a cost optimization.
- Pair it with Programmatic Tool Calling when a task chains many tools — keep intermediate results in the code sandbox, not the context window.

## What to do
- Audit your agent's tool count; if it exceeds ~10–15, set `defer_loading: true` on the long tail and add the Tool Search Tool.
- Add `input_examples` to any tool with fiddly optional/combination parameters.
- For multi-tool research/data tasks, evaluate Programmatic Tool Calling so outputs are filtered in-sandbox before entering context.

## Connects to
- [tool calling](../../../06-agents/32-tool-calling.md)
- [MCP](../../../06-agents/33-mcp.md)
- [agentic systems](../../../06-agents/34-agentic-systems.md)
