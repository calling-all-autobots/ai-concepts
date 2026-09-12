# Model deprecation & retirement timeline (Nov 2025 – Aug 2026)

- **Category:** ① Product release (lifecycle)
- **Date:** span 2025-11 → 2026-08  ·  **What it affects:** any app pinned to a specific `claude-*` model ID
- **Sources:** [Model deprecations](https://docs.claude.com/en/docs/about-claude/model-deprecations) · [Models overview](https://docs.claude.com/en/docs/about-claude/models/overview) · platform.claude.com API release notes

## In one line
Across these ten months Anthropic retired almost the entire Claude 3 and Claude 4 line-up — if you pinned a model ID and stopped watching, some of your code is now calling a model that returns errors.

## What actually changed
A rolling wave of deprecations (announced) → retirements (endpoint stops serving):

| Date | Event |
|---|---|
| 2025-12-19 | Claude Haiku 3.5 **deprecation announced** |
| 2026-01-05 | **Claude Opus 3 retired** (`claude-3-opus-20240229`) |
| 2026-01-16 | Opus 4 & 4.1 marked deprecated in the app model selector |
| 2026-02-19 | **Claude Sonnet 3.7 and Haiku 3.5 retired** (same day automatic prompt caching shipped) |
| 2026-04-14 | Sonnet 4 & Opus 4 **deprecation announced** (retire Jun 15) |
| 2026-04-20 | **Claude Haiku 3 retired** |
| 2026-04-30 | **1M-token context beta retired** for Sonnet 4.5 / Sonnet 4 (>200K now errors) |
| 2026-06-05 | Opus 4.1 **deprecation announced** (retire Aug 5) |
| 2026-06-15 | **Claude Sonnet 4 and Opus 4 retired** |
| 2026-08-05 | **Claude Opus 4.1 retired** |

"Deprecated" = still works but on notice; "retired" = requests fail. Anthropic's stated policy is a **≥60-day** window between the two.

## Why it matters
A pinned model ID is a dependency with an expiry date, and the failure is silent until it isn't: nothing in your code changes, then one day the endpoint 410s and a production path breaks. The pace here — roughly one retirement a month — means "set it and forget it" is not a viable posture. The 1M-context-beta retirement is the sneaky one: it's not a model retirement but a *capability* retirement, so a request that worked at 300K tokens suddenly errors even though the model still exists. Retirements also force a re-validation, not just a string swap: a newer model changes outputs, tokenization, and cost, so anything you'd regression-tested against the old snapshot needs re-checking.

## Your point of view
- "A pinned model ID is technical debt with a due date — treat model lifecycle as a standing operational risk, not a one-off migration."
- "The ≥60-day deprecation window is your migration budget; if you're not subscribed to the deprecations feed, you're spending it without knowing."
- "Capability retirements (like the 1M beta) bite even when the model survives — pin and test the *feature*, not just the model."
- "Every model swap is a re-eval, never a find-and-replace — the new model is a new dependency."

## What to do
1. **Inventory every pinned `claude-*` ID** in your code, configs, and prompts; map each to its deprecation/retirement date from the official deprecations page.
2. **Subscribe to the deprecations page / API release notes** so the ≥60-day clock is visible (this is exactly what the weekly radar now watches).
3. **Set a fallback** (`fallbacks` / model-chain where supported) so a retired model degrades gracefully instead of hard-failing.
4. **Re-run your eval suite before migrating**, not after the incident — pin the model version and treat the upgrade as a tested change.

## Connects to
[Model ID / versioning](../../dev-surfaces/07-model-id-versioning.md) · [Regression testing](../../09-evaluation/47-regression-testing.md) · [Production architecture](../../10-production-ops/48-production-architecture.md) · [Cost & unit economics](../../10-production-ops/51-cost-unit-economics.md)
