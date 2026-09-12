# Claude Fable 5.1 & Mythos 5.1

- **Category:** ① Product release
- **Date:** 2026-09-01  ·  **What it affects:** the frontier model you build on (`claude-fable-5-1`)
- **Sources:** [Anthropic announcement](https://www.anthropic.com/claude-fable-and-mythos-5-1) · [Pricing](https://platform.claude.com/docs/en/about-claude/pricing) · [What's new](https://platform.claude.com/docs/en/models/fable-5-1/whats-new-fable-5-1)

## In one line
Anthropic's new frontier models are meaningfully better at agentic coding and science **and cheaper to run** — same sticker price as 5.0, but a 75% cache-read cut that lands as ~25–45% real savings on the workloads we actually build.

## What actually changed
- **Capability jump, not a point bump.** Terminal-Bench 4.0 (agentic coding) **42.0% → 55.8%**; Terminal-Bench-Science **24.7% → 52.6%** (more than doubled); CursorBench 70.5% → 73.4%. The science gains are real-world: ~50% protein-design hit rate across 12 targets (vs. a typical 10–15%), deep-learning models optimized up to 2.5×.
- **Pricing (per 1M tokens):** input **$10**, output **$50** — unchanged from Fable 5. The change is **cache reads: $1.00 → $0.25 (–75%)**. Cache writes $12.50 (5-min) / $20 (1-hr). Batch halves everything to $5 / $25. US-only inference is 1.1×.
- **Net effect Anthropic quotes:** "~25% [cheaper] for typical workloads… up to ~45% for complex coding and highly agentic tasks."
- **Bigger envelope:** 1M-token context at a **flat price across the whole window**, and **128k max output** (~70% more output headroom than before).
- **Fable vs. Mythos:** *identical underlying model.* **Fable = generally available** (`claude-fable-5-1`). **Mythos = restricted** to vetted orgs in cybersecurity and life sciences, with more permissive safeguards. You will almost always mean Fable.
- **Migration notes:** ~60% fewer false-positive interventions from the cyber safeguards; and an **anti-distillation change disables manual context editing for new API accounts** — worth knowing if you build one.

## Why it matters
The story of 5.1 is **the cost curve, not the capability curve.** A 75% cache-read cut disproportionately rewards exactly the patterns we lean on — agent loops, long multi-turn chats, and RAG over a stable corpus — because those re-read a large cached prefix on every call. That's why "same per-token price" still becomes 25–45% cheaper end-to-end: the savings come from *where* tokens are spent, not the headline rate. It also quietly shifts build-vs-buy math: a workload that was marginal on unit economics last month may clear the bar now with no code change.

## Your point of view
- "5.1 is a **cost release wearing a capability release's clothes** — the cache-read cut is the headline for anyone running agents or long context."
- "**Restructure prompts to maximize the cached prefix** and you capture most of the 45%; leave them as-is and you only get ~25%. The savings are a design choice, not a freebie."
- "Fable vs. Mythos is a *safeguards/access* split, not a quality split — don't let anyone tell you Mythos is 'the better model.'"
- "The doubling on Terminal-Bench-Science signals the real frontier movement is in **agentic, tool-using, long-horizon work**, not chat."

## What to do
1. **Switch to `claude-fable-5-1`** for new work; it's a drop-in with better numbers at equal or lower cost.
2. **Re-cost your top 2–3 workloads** with cache reads at $0.25 — anything cache-heavy just got cheaper; update any estimate that assumed $1.00.
3. **Order prompts stable-prefix-first** (system + tools + long context up top, variable input last) to maximize cache hits and bank the larger discount.
4. If you spin up a **new API account**, note that manual context editing is off (anti-distillation) — design around it rather than being surprised.

## Connects to
[Prompt caching](../../05-prompting/31-prompt-caching.md) · [Cost & unit economics](../../10-production-ops/51-cost-unit-economics.md) · [Context windows](../../01-foundations/05-context-windows.md) · [Model ID / versioning](../../dev-surfaces/07-model-id-versioning.md)
