# Claude Opus 4.5 — first model over 80% on SWE-bench Verified

- **Category:** ① Product release
- **Date:** 2025-11-24  ·  **What it affects:** `claude-opus-4-5` (flagship model); Claude Developer Platform, Claude Code, Claude apps
- **Sources:** https://www.anthropic.com/news/claude-opus-4-5 · https://platform.claude.com/docs/en/build-with-claude/effort

## In one line
Anthropic's new flagship, positioned as "the best model in the world for coding, agents, and computer use," and the first model to cross 80% on SWE-bench Verified — while dropping the Opus price to $5/$25 per million tokens.

## What actually changed
- **SWE-bench Verified: 80.9%** — the first model over the 80% line, ahead of GPT-5.1-Codex-Max (77.9%), Sonnet 4.5 (77.2%), and Gemini 3 Pro (76.2%). For scale, Claude 3.5 Sonnet was 49%.
- **Price cut:** $5 / M input, $25 / M output — roughly a third of the previous Opus 4.1 price ($15/$75), narrowing the gap to Sonnet-tier economics for a frontier model. 200K context window.
- **`effort` parameter:** a new API control trading capability against latency/cost. At **medium effort, Opus 4.5 matches Sonnet 4.5's best SWE-bench score while using 76% fewer output tokens.** Default is `high`.
- **Longer agent runs:** ships with **context compaction** and a **memory tool** so agents can keep working past a single context window.
- Other gains cited: Aider Polyglot +10.6% over Sonnet 4.5; Vending-Bench +29%; leads 7 of 8 languages on SWE-bench Multilingual.

## Why it matters
Two things move together here: a capability record *and* a price cut. Crossing 80% SWE-bench with an $5/$25 model changes the build-vs-buy math for coding agents — the frontier tier is now affordable enough to sit in an inner loop, not just a special-case call. The `effort` knob is the sleeper feature: "76% fewer tokens at Sonnet-4.5-equivalent quality" means you can dial one model from cheap-and-fast to max-capability instead of maintaining a model-routing zoo.

## Your point of view
- Opus 4.5 is the moment frontier coding quality stopped being a premium-only decision — the price/capability curve bent hard.
- `effort` is a first-class cost lever. Don't switch models for cost; tune effort on one model and measure quality-per-token.
- The 80% headline matters less than the economics: same-or-better results at a fraction of prior Opus cost is what unlocks agent workloads.

## What to do
- Re-baseline any coding/agent eval on `claude-opus-4-5`, sweeping `effort` (medium vs high) and recording quality *and* output-token cost per level.
- Where you route Sonnet-for-cost, test whether Opus 4.5 at medium effort beats it on both quality and spend.
- For long agent tasks, enable the memory tool + context compaction rather than hand-rolling context management.

## Connects to
- [reasoning models](../../../03-reasoning-generation/18-reasoning-models.md)
- [agent memory](../../../06-agents/35-agent-memory.md)
- [agentic systems](../../../06-agents/34-agentic-systems.md)
