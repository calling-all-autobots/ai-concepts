# Dev surfaces — usage tier

The operational, platform-facing vocabulary of *building with* an LLM (Large Language Model) — the surfaces and mechanics you meet in a console, an API (Application Programming Interface), or an engineering conversation. This is a deliberate companion to the concept syllabus, which is concept-first and leaves these out on purpose; the practical index for the terms is [USAGE-KEYWORDS.md](../USAGE-KEYWORDS.md).

Each lesson is written to the same standard as the concept book (discourse depth, one analogy, stumper interview questions) but scoped to PM-level *operational* judgment — enough to use the term correctly and defend a tradeoff.

## Lessons

1. [Workbench / Playground](01-workbench-playground.md) — the workbench-to-production gap; a design surface, not a testing one.
2. [Console / dashboard](02-console-dashboard.md) — the ops & governance surface; aggregate health vs. per-request observability.
3. [SDK](03-sdk.md) — the SDK-vs-raw-HTTP tradeoff; the two-pin (model + SDK) reproducibility trap.
4. [API endpoint](04-api-endpoint.md) — statelessness: every call is independent and you resend the whole history.
5. [API key](05-api-key.md) — a bearer secret; blast radius and the store/scope/rotate lifecycle.
6. [Rate limits (TPM / RPM)](06-rate-limits.md) — two independent ceilings; backoff-with-jitter and capacity planning.
7. [Model ID / snapshot / version](07-model-id-versioning.md) — a version pin; reproducibility vs. staying current.
