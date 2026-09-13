# Claude Sonnet 5 — cheaper on paper, but a new tokenizer eats ~30% of the win

- **Category:** ① Product release
- **Date:** 2026-06-30  ·  **What it affects:** model `claude-sonnet-5` (Messages API, all surfaces)
- **Sources:** https://simonwillison.net/2026/Jun/30/claude-sonnet-5/ · https://platform.claude.com/docs/en/release-notes/overview

## In one line
Sonnet 5 is Anthropic's new mid-tier model at roughly Opus-4.8 quality for a fraction of the price — but it counts tokens with a new tokenizer that inflates the same text by about 30%, so the headline discount is smaller than it looks.

## What actually changed
- **Model ID:** `claude-sonnet-5`. 1M-token context window, 128K max output.
- **Pricing:** launched at an introductory **$2 / M input, $10 / M output** (later made permanent), against Sonnet 4.6's $3 / $15. Anthropic had originally floated a $3 / $15 standard tier and then dropped it in favour of the lower rates.
- **New tokenizer:** Sonnet 5 adopts the tokenizer introduced with Opus 4.7. The same text now produces **~30% more tokens** than on Sonnet 4.6. It is uneven by content: English ~1.4x, Spanish ~1.33x, Python ~1.27x, simplified Mandarin ~1.01x (basically unchanged).
- **Adaptive thinking on by default.** To turn it off you must pass `"thinking": {"type": "disabled"}`.
- Performance is described as close to Opus 4.8 at a much lower price. Knowledge cutoff January 2026.

## Why it matters
The sticker price fell ~33% on input and ~33% on output, but if your workload is English prose or code, each request now bills ~27–40% more tokens. Net effect: your real per-request cost may be flat or only modestly lower, not the ~33% the price sheet implies. Anyone who budgeted from the old token counts, set spend alerts, or sized a context window in tokens is now working from stale numbers. Thinking-on-by-default also raises output-token volume unless you explicitly disable it.

## Your point of view
- "Sonnet 5 is a genuine price cut, but re-measure before you claim a number — the tokenizer change claws back a big chunk of it."
- "Model-to-model cost comparisons are now meaningless unless both are counted with the same tokenizer. Compare on *dollars per real task*, not per-token rates."
- "It's close to Opus 4.8 quality at ~1/3 the input price — for most agent and RAG workloads this is the new default, not Opus."

## What to do
1. Re-run the token counting API against `claude-sonnet-5` on representative prompts before comparing costs to 4.6.
2. Reset spend alerts and per-request budgets to the new token counts.
3. Decide explicitly on thinking: leave it on for hard reasoning, disable it for cheap extraction/classification to control output tokens.

## Connects to
- [tokenization](../../../foundations/tokenization.md)
- [cost & unit economics](../../../production-ops/cost-unit-economics.md)
- [model ID & versioning](../../../dev-surfaces/model-id-versioning.md)
- [reasoning models](../../../reasoning-generation/reasoning-models.md)
