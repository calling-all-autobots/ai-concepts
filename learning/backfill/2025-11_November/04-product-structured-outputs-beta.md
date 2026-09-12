# Structured Outputs (public beta) — guaranteed schema conformance

- **Category:** ① Product release
- **Date:** 2025-11-14  ·  **What it affects:** Claude Developer Platform API (beta header `structured-outputs-2025-11-13`); Sonnet 4.5, Opus 4.1 at launch
- **Sources:** https://claude.com/blog/structured-outputs-on-the-claude-developer-platform · https://platform.claude.com/docs/en/build-with-claude/structured-outputs

## In one line
A public beta that *guarantees* Claude's output matches your JSON schema (or tool definition) — not "asked nicely to," but enforced during generation — so you can delete the retry/validation/repair code around the model.

## What actually changed
Structured Outputs enforces a schema instead of hoping for one. It runs in two modes:

- **Strict JSON output** — supply a JSON schema in the request; the response is guaranteed to be valid JSON matching it.
- **Strict tool use** — tool-call arguments are guaranteed to conform to the tool's declared input schema.

Under the hood it is **constrained decoding**: Claude compiles your schema into a grammar and restricts token generation so no token that would break the schema can be emitted. The compiled schema is **cached for 24 hours** to avoid recompiling on every call.

- **Beta header:** `anthropic-beta: structured-outputs-2025-11-13`.
- **Launch models:** Sonnet 4.5 and Opus 4.1 (Haiku 4.5 added later).
- **Trajectory:** this beta reached **general availability on 2026-02-04** for Sonnet 4.5, Opus 4.5, and Haiku 4.5 — so treat it as a stable direction, not an experiment.

## Why it matters
Most "get JSON out of an LLM" code is defensive scaffolding: prompt begging, parse, validate, retry on failure, repair malformed output. Constrained decoding removes the failure mode at the source — the model *cannot* produce output that violates the schema — which eliminates a whole class of parse errors and failed tool calls and lets you drop the fallback logic. That reliability is what makes LLM output safe to feed directly into downstream systems.

## Your point of view
- This is the difference between "usually valid JSON" and "provably valid JSON" — the latter is what you need to put an LLM in a pipeline without a human check.
- It's constrained decoding, not better prompting: the guarantee is structural, so retry/repair code becomes dead weight you should delete.
- Schema conformance guarantees *shape*, not *correctness* — the fields will be present and typed, but their values can still be wrong. Keep semantic validation.

## What to do
- For any integration parsing Claude's JSON, adopt the beta header and remove manual JSON-repair/retry loops.
- Keep schemas stable to benefit from the 24-hour compiled-schema cache.
- Since it's now GA (Feb 2026), plan to make structured outputs your default for machine-consumed responses — but retain value-level validation.

## Connects to
- [structured outputs](../../../03-reasoning-generation/20-structured-outputs.md)
- [tool calling](../../../06-agents/32-tool-calling.md)
- [sampling & decoding](../../../03-reasoning-generation/16-sampling-decoding.md)
