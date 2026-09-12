# Claude Fable 5 & Mythos 5 — the first public Mythos-class model, with a `refusal` stop reason

- **Category:** ① Product release
- **Date:** 2026-06-09  ·  **What it affects:** models `claude-fable-5` and Claude Mythos 5 (Messages API)
- **Sources:** https://www.anthropic.com/news/claude-fable-5-mythos-5 · https://platform.claude.com/docs/en/build-with-claude/refusals-and-fallback · https://techcrunch.com/2026/06/09/anthropics-claude-fable-5-is-a-version-of-mythos-the-public-can-access-today/

## In one line
Fable 5 is Anthropic's first publicly available Mythos-class model — its most capable public model ever — made shippable by running safety classifiers that can end a response with a new `stop_reason: "refusal"`; Mythos 5 is the restricted, higher-risk sibling.

## What actually changed
- Announced **June 9, 2026**. **Fable 5 = the public Mythos-class model** (ID `claude-fable-5`); **Mythos 5 = restricted** (government-adjacent cybersecurity use).
- **Pricing: $10 / M input, $50 / M output** for both.
- **Tokenizer:** the Opus-4.7 tokenizer — same text produces **~30% more tokens** than pre-4.7 models; measure with the token counting API against `claude-fable-5`.
- **New `refusal` stop reason:** when a classifier declines, the Messages API returns **`stop_reason: "refusal"` as a successful HTTP 200** (not an error). `stop_details.category` names the policy area — documented values include **`cyber`, `bio`, `frontier_llm`, `reasoning_extraction`**. You are **not billed** for a request refused before any output is generated.
- **Safeguards:** classifier-based, covering cybersecurity, biology/chemistry, and distillation; tuned conservatively to trigger in **under ~5% of sessions**. In high-risk areas the model blocks and **falls back to Opus 4.8**.
- **Export saga:** on June 12 the U.S. government barred non-U.S. nationals from both models and access was revoked; Commerce lifted the ban June 30 and access resumed July 1.

## Why it matters
The headline capability comes bundled with a new failure mode your code must handle gracefully: a 200 response that contains a refusal, not content. If your integration assumes any 200 = usable output, it will break silently. The classifier layer (and Opus-4.8 fallback) is the mechanism that let Anthropic release a frontier-class model publicly at all — safety is packaged as an API contract, not just model behaviour. At $10/$50 plus ~30% more tokens, this is a premium model; it is not the default for routine work.

## Your point of view
- "Fable 5's real developer news is the `refusal` stop reason — handle `stop_reason: "refusal"` explicitly, don't treat 200 as success."
- "You're not billed for pre-output refusals, and refused high-risk requests fall back to Opus 4.8 — design your UX around both."
- "At $10/$50 with the 30%-more-tokens tokenizer, reserve Fable 5 for genuinely frontier tasks; use Sonnet 5 for the rest."

## What to do
1. Add explicit handling for `stop_reason: "refusal"` (read `stop_details.category`) and design a user-facing fallback path.
2. Re-cost prompts under the Opus-4.7 tokenizer before adopting; expect ~30% more tokens on top of the $10/$50 rate.
3. Confirm export/eligibility rules for your users given the national-security restrictions.

## Connects to
- [guardrails](../../../08-safety-trust/41-guardrails.md)
- [responsible AI](../../../08-safety-trust/44-responsible-ai.md)
- [tokenization](../../../01-foundations/01-tokenization.md)
- [model ID & versioning](../../../dev-surfaces/07-model-id-versioning.md)
