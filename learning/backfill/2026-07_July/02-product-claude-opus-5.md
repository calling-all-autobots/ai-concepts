# Claude Opus 5: frontier intelligence at unchanged Opus pricing

- **Category:** ① Product release
- **Date:** 2026-07-24  ·  **What it affects:** `claude-opus-5` (API), Claude apps, Claude Code
- **Sources:** https://www.anthropic.com/news/claude-opus-5 · https://www.marktechpost.com/2026/07/24/meet-the-new-claude-opus-5-frontier-class-agentic-coding-and-computer-use-at-unchanged-opus-pricing/

## In one line
Opus 5 (`claude-opus-5`) is Anthropic's new frontier model — 1M-token context as both default and max, extended thinking on by default, and $5/$25 per million tokens, the same price as Opus 4.8.

## What actually changed
- **Pricing held flat while capability jumped:** $5 per million input / $25 per million output — unchanged from Opus 4.8 — with the full 1M context at no long-context premium (a 900k-token request bills at the same per-token rate as a 9k one). Fast mode costs 2x base and runs ~2.5x default speed.
- **Context/output:** 1M-token context window (default and maximum); 128k max output tokens.
- **Thinking on by default:** extended thinking is enabled out of the box, with a per-request `effort` toggle (low / medium / high) to raise reasoning compute on hard problems or lower it for routine work.
- **Benchmarks:** ~96.0% SWE-bench Verified and ~79.2% SWE-bench Pro; Anthropic headlines ARC-AGI 3 "three times as high as the next-best model," OSWorld 2.0 above Fable 5 at ~a third of the cost, and CursorBench within 0.5% of Fable 5 at half the cost per task. Knowledge cutoff May 2026.
- Anthropic frames it as "close to the frontier intelligence of Claude Fable 5 at half the price" and its "most aligned model to date."

## Why it matters
Frontier capability arriving at the *same* price as the prior Opus resets the cost/quality frontier: work that was too expensive to run on a top model may now be viable. Thinking-on-by-default means the reasoning tax is now the baseline, so `effort` becomes your primary cost lever, not an opt-in.

## Your point of view
- The story isn't the benchmark — it's price stability. "Frontier quality at last-gen prices" is the line to bring to a planning meeting.
- Because thinking is on by default, budget for higher token spend unless you deliberately turn `effort` down; treat `effort` as a per-workload dial.
- At half the cost-per-task of Fable 5 on agentic/computer-use benchmarks, Opus 5 is a serious default for coding and agent workloads.

## What to do
- Pin `claude-opus-5` and pilot it against your current Opus/Sonnet workloads; measure quality delta and token cost with `effort` at low vs high.
- Re-run cost models: the 1M context has no premium, so long-context designs get cheaper — but thinking-on-by-default raises per-call tokens.
- Set an `effort` default per use case rather than accepting the model default everywhere.

## Connects to
- [Reasoning models](../../../03-reasoning-generation/18-reasoning-models.md)
- [Context windows](../../../01-foundations/05-context-windows.md)
- [Cost / unit economics](../../../10-production-ops/51-cost-unit-economics.md)
- [Model ID & versioning](../../../dev-surfaces/07-model-id-versioning.md)
