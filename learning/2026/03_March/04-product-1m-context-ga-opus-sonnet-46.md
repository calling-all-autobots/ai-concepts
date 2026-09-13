# 1M context GA (no price multiplier) for Opus 4.6 and Sonnet 4.6

- **Category:** ① Product release
- **Date:** 2026-03-13  ·  **What it affects:** Claude Opus 4.6 and Sonnet 4.6 context limits and pricing; Platform, Foundry, Vertex AI
- **Sources:** https://claude.com/blog/1m-context-ga · https://www.anthropic.com/news/claude-opus-4-6

## In one line
The 1M-token context window left beta for Opus 4.6 and Sonnet 4.6 — and, critically, dropped the long-context price surcharge so a 900K-token request bills at the same per-token rate as a small one.

## What actually changed
The 1 million-token context window became generally available for both Opus 4.6 and Sonnet 4.6 on Mar 13, 2026. The headline is pricing: it is now **standard, flat pricing across the full window** — $5 / $25 per million input/output tokens for Opus 4.6 and $3 / $15 for Sonnet 4.6 — with **no >200K multiplier**. Under the earlier beta, prompts over 200K tokens were billed at a premium (roughly $10 / $37.50 per million). Media handling scaled up too: a single request can carry up to **600 images or PDF pages**, up from 100. On quality, Opus 4.6 scores **78.3% on MRCR v2 at 1M tokens**, the highest among frontier models at that length — meaning the window is usable, not just nominally available. It shipped simultaneously on the Claude Platform, Microsoft Foundry, and Google Cloud Vertex AI.

## Why it matters
Beta long context carried two taxes: a price multiplier that made big prompts economically painful, and uncertainty about whether recall held up deep in the window. Removing the multiplier makes whole-codebase, whole-corpus, and long-transcript prompts economically ordinary rather than exceptional. The MRCR score matters because a large window with poor mid-context recall is a trap — you pay for tokens the model ignores. Flat pricing plus verified recall changes the build-vs-retrieve calculus for many workloads.

## Your point of view
- The removed multiplier is the real news — 1M tokens was technically available before; now it is affordable, which is what actually changes architecture decisions.
- Big context does not retire RAG: retrieval is still cheaper and lower-latency for most queries. Reach for 1M when the task genuinely needs global reasoning over a large body, not as a lazy substitute for retrieval.
- Check recall benchmarks (MRCR-style), not just the window size, before trusting the far end of any long-context model.

## What to do
Re-estimate costs for long-context workloads at the new flat rate before deciding between stuffing context and building retrieval. Use the 600-page media limit for large document/PDF pipelines. Keep RAG for high-QPS or latency-sensitive paths where a huge prompt is wasteful.

## Connects to
- [context windows](../../../foundations/context-windows.md)
- [RAG](../../../retrieval-knowledge/rag.md)
- [cost & unit economics](../../../production-ops/cost-unit-economics.md)
- [benchmarks](../../../evaluation/benchmarks.md)
