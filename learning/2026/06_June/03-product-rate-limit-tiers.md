# API rate limits restructured to Start / Build / Scale

- **Category:** ① Product release
- **Date:** 2026-06-26  ·  **What it affects:** Claude API rate-limit tiers (all organizations)
- **Sources:** https://knightli.com/en/2026/06/29/claude-api-rate-limits-rpm-itpm-otpm-429/ · https://chatforest.com/builders-log/anthropic-rate-limits-start-build-scale-sonnet-haiku-opus-unified-june-2026-builder-guide/

## In one line
Anthropic collapsed its API rate-limit tiers from four to three — Start, Build, Scale (plus a no-cap Custom) — raised limits across the board, and made Sonnet and Haiku limits match Opus at every tier.

## What actually changed
- Effective **June 26, 2026**: four usage tiers became **three — Start / Build / Scale**, with **Custom** above Scale for organizations that outgrow it.
- Reported monthly spend caps that gate each tier: **Start $500 / Build $1,000 / Scale $200,000 / Custom none** (contact sales).
- **Sonnet 4.x and Haiku 4.5 rate limits now equal Opus 4.x** at every tier — previously the cheaper models were throttled differently.
- Limits are still enforced per organization across three metrics: **RPM** (requests/min), **ITPM** (input tokens/min), **OTPM** (output tokens/min).
- Anthropic states most organizations move to a *higher* tier, **no organization gets lower limits than before**, and **no manual action is required**.

## Why it matters
Rate limits, not price, are often the real ceiling on scaling an agentic workload — a burst of parallel tool calls hits RPM/ITPM long before it hits the monthly budget. Unifying Sonnet/Haiku limits with Opus removes a subtle penalty for using cheaper models at volume: you no longer trade throughput for cost. The three-tier structure is simpler to reason about, and because limits only went up, this is a pure tailwind for anyone previously getting 429s.

## Your point of view
- "Rate limits are a scaling constraint, not a billing footnote — this change quietly raises the throughput ceiling for high-volume agents."
- "Sonnet/Haiku now share Opus's limits, so 'downshift to a cheaper model under load' is now a free lever, not a throughput hit."
- "Nothing to migrate, but you should re-check which tier you're in — you may have headroom you didn't have last week."

## What to do
1. Check your current tier and the new RPM/ITPM/OTPM ceilings in the console; you may be able to remove client-side throttling you added to avoid 429s.
2. If you deferred a Sonnet/Haiku high-volume workload over rate limits, reconsider — the throttle gap is gone.

## Connects to
- [rate limits](../../../dev-surfaces/06-rate-limits.md)
- [cost & unit economics](../../../10-production-ops/51-cost-unit-economics.md)
- [production architecture](../../../10-production-ops/48-production-architecture.md)
