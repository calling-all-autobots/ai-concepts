# Claude Opus 4.6 — adaptive thinking, four `effort` levels, and a context-compaction API

- **Category:** ① Product release
- **Date:** 2026-02-05  ·  **What it affects:** model `claude-opus-4-6`; Messages API (`effort`, compaction, adaptive thinking); fast mode
- **Sources:** https://www.anthropic.com/news/claude-opus-4-6 · https://docs.claude.com/en/docs/about-claude/models/overview

## In one line
Opus 4.6 is the new flagship: a 1M-token context (beta), 128K output, a four-level `effort` dial that replaces the old thinking-token budget, and a built-in context-compaction feature so agents can run long without blowing the window.

## What actually changed
Released Feb 5, 2026 as `claude-opus-4-6`. **Pricing $5 / $25 per million input/output tokens** (a premium band of $10 / $37.50 applies to requests over 200K tokens; US-only inference is 1.1× pricing). **1M-token context window (beta)** and **128K max output tokens**. Key API changes:
- **`effort` parameter** with four levels — `low`, `medium`, `high` (default), `max` — to calibrate reasoning depth per task. This replaces the previous `budget_tokens` approach, which is now deprecated.
- **Adaptive thinking** — the model itself decides when deeper reasoning is worthwhile rather than always thinking or never thinking.
- **Context compaction** — automatically summarizes and replaces older context when the conversation approaches a configurable threshold (the model's own BrowseComp setup used a 50,000-token threshold), enabling long-horizon agent runs.
- **Fast mode** followed on Feb 7, 2026 — a lower-latency serving option for the same model.

Benchmarks: **81.42% SWE-bench Verified** (with prompt modification), the top score on Terminal-Bench 2.0, leads frontier models on Humanity's Last Exam, and on long-context retrieval (MRCR v2) scores 76% vs Sonnet 4.5's 18.5%.

## Why it matters
Two structural shifts. First, `effort` turns reasoning depth into a first-class, per-request cost/quality knob — you pay for deep thinking only where it earns its keep, and `budget_tokens` is on the way out so code needs updating. Second, context compaction moves "don't overflow the window" from bespoke app-side plumbing into the platform, which is exactly what long-running agents need. The MRCR jump (76% vs 18.5%) is the quiet standout: long-context retrieval that actually works, not just a big number on the spec sheet.

## Your point of view
- Opus 4.6 is a "controllability" release as much as a capability one: `effort` + adaptive thinking + compaction are about running agents predictably and cost-effectively, not just scoring higher.
- Migrate off `budget_tokens` now — it is deprecated; standardize on `effort` and default to `high`, dropping to `low/medium` for cheap tasks and `max` only for the hardest.
- The long-context retrieval delta (76% vs 18.5% MRCR) is the datapoint to cite when someone claims "big context windows don't really work."

## What to do
- Replace any `budget_tokens` usage with the `effort` parameter; tune per route.
- For long agent runs, turn on context compaction and set a threshold instead of writing your own truncation/summarization.
- Use fast mode (Feb 7) for latency-sensitive paths where you still want Opus quality.

## Connects to
- [reasoning models](../../../03-reasoning-generation/18-reasoning-models.md)
- [chain of thought](../../../03-reasoning-generation/17-chain-of-thought.md)
- [context windows](../../../01-foundations/05-context-windows.md)
- [cost & unit economics](../../../10-production-ops/51-cost-unit-economics.md)
- [benchmarks](../../../09-evaluation/46-benchmarks.md)
