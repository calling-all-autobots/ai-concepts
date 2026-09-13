# Claude Opus 4.8 + Dynamic Workflows research preview

- **Category:** ① Product release
- **Date:** 2026-05-28  ·  **What it affects:** model `claude-opus-4-8`; Claude Code (Enterprise/Team/Max)
- **Sources:** https://www.anthropic.com/news/claude-opus-4-8 · https://platform.claude.com/docs/en/about-claude/models/whats-new-claude-4-8

## In one line
A new frontier model (`claude-opus-4-8`) that defaults to a 1M-token context and high effort, plus "Dynamic Workflows" — Claude Code planning a job and running *hundreds* of parallel subagents in one session to do codebase-scale work end to end.

## What actually changed
- **Model:** `claude-opus-4-8`, released 41 days after Opus 4.7. Pricing unchanged from the Opus tier: **$5/M input, $25/M output** (regular); fast mode is **$10/M / $50/M** at **2.5x** speed — and fast mode is now ~3x cheaper than on earlier models.
- **Defaults:** **1M-token context is the default** (no beta header, standard pricing); **128k max output**; **effort defaults to "high,"** with `xhigh` and `max` now selectable, and effort control exposed even on claude.ai.
- **Benchmarks:** SWE-bench Verified **90.2%**, Online-Mind2Web **84%**, first model to clear 10% all-pass on the Legal Agent Benchmark. Reported ~**4x less likely** than Opus 4.7 to let a code flaw pass without flagging it.
- **Dynamic Workflows (research preview):** Claude plans the work, spawns **hundreds of parallel subagents in a single Claude Code session**, verifies outputs against the existing test suite, and reports back. Anthropic's headline use case is migrations across **hundreds of thousands of lines** from kickoff to merge. Available in Claude Code for **Enterprise, Team, and Max** plans.

## Why it matters
This is the item you lost track of. Dynamic Workflows is a step change in *orchestration granularity*: instead of you manually fanning out subagents, the model itself decomposes a large task, parallelizes it massively, and self-verifies. The unit of delegation moves from "a prompt" to "a project." Combined with high-effort defaults and a 1M context that no longer needs a flag, the friction of pointing Claude at a whole repo drops sharply — but so does your visibility into what hundreds of concurrent agents are doing.

## Your point of view
- "Opus 4.8 didn't change the price — it changed the defaults. 1M context and high effort out of the box means the *median* request now costs and thinks more; budget for it."
- "Dynamic Workflows is the first credible 'give it the whole migration' feature. It's research-preview and plan-gated, so treat it as a pilot, not production."
- "Massive parallel subagents raise a governance question: verification and blast-radius control become the bottleneck, not model capability."

## What to do
- Pin `claude-opus-4-8` explicitly and re-baseline latency/cost dashboards — high-effort + 1M defaults will move both.
- If on Enterprise/Team/Max, pilot Dynamic Workflows on one contained migration with a strong test suite as the acceptance bar; watch spend closely.
- Set effort deliberately (`high`/`xhigh`/`max`) per workload rather than accepting the default everywhere.

## Connects to
- [multi-agent](../../../agents/multi-agent.md) · [planning & orchestration](../../../agents/planning-orchestration.md) · [agentic systems](../../../agents/agentic-systems.md)
- [context windows](../../../foundations/context-windows.md) · [reasoning models](../../../reasoning-generation/reasoning-models.md) · [cost & unit economics](../../../production-ops/cost-unit-economics.md)
