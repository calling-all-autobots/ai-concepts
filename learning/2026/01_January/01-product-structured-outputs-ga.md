# Structured Outputs GA: schema conformance is now guaranteed, no beta header

- **Category:** ① Product release
- **Date:** 2026-01-29 (announced GA late Jan; the Claude blog post dates the GA milestone 2026-02-04) · **What it affects:** Claude Developer Platform Messages API (`output_config.format`), Amazon Bedrock
- **Sources:** https://claude.com/blog/structured-outputs-on-the-claude-developer-platform · https://platform.claude.com/docs/en/build-with-claude/structured-outputs · https://aws.amazon.com/about-aws/whats-new/2026/02/structured-outputs-available-amazon-bedrock/

## In one line
Claude can now be forced to return JSON that always matches your schema (or your tool definition) via constrained decoding, and it left beta — no beta header, GA-supported models.

## What actually changed
Structured Outputs, in public beta since 2025-11-14, went generally available in late January 2026 (the official blog post stamps the GA milestone 2026-02-04; release aggregators cite Jan 29 — the transition straddles the month boundary). The concrete changes:
- The request field moved from the beta `output_format` to **`output_config.format`**, and the beta header is no longer required. The API still accepts the old `output_format` for a transition window, but the Python SDK v1.0+ rejects it with a `TypeError` — you must pass `output_config`.
- GA adds support for **more complex schemas** than the beta allowed.
- Guarantee mechanism is **constrained decoding**: responses are always valid JSON (no `JSON.parse()` failures), field types and `required` fields are enforced, and no retries are needed for schema violations.
- Works two ways: JSON output (you pass a `json_schema`) or strict tool-call conformance.
- Performance model: the first request with a new schema pays a **grammar-compilation** latency cost; compiled grammars are **cached for 24 hours**, so later calls are much faster. The cache invalidates if you change the schema or tool set.
- Cost note: input tokens are slightly higher because a system prompt describing the format is injected, and changing `output_config.format` invalidates the prompt cache for that thread.
- GA models include `claude-opus-4-5`, `claude-sonnet-4-5`, `claude-haiku-4-5` (plus later 4.6/5-class models). On Bedrock it covers Opus 4.6, Sonnet 4.6, Sonnet 4.5, Opus 4.5, Haiku 4.5.

## Why it matters
Anyone building agents, extraction pipelines, or tool-calling flows previously wrote defensive parsing, retries, and validators to handle Claude occasionally drifting from the schema. Constrained decoding removes that entire failure class at the decode step, not with a post-hoc check. For agent reliability this is foundational: a tool call that always conforms means fewer broken multi-step trajectories.

## Your point of view
- "Schema conformance is now a decode-time guarantee, not a prompt-and-pray hope — we can delete our JSON-repair and retry code."
- "It's not free: budget for first-call grammar-compilation latency and keep schemas stable to keep the 24-hour grammar cache and prompt cache warm."
- "Migration is a real task — `output_format` → `output_config.format`; SDK v1.0+ hard-fails the old field, so pin and test before upgrading."

## What to do
- Move any beta usage to `output_config.format` and drop the beta header; audit SDK version (v1.0+ breaks `output_format`).
- Delete bespoke JSON-repair/retry logic guarding schema violations; keep validators only for business rules.
- Keep JSON schemas and tool sets stable across calls to benefit from grammar + prompt caching; expect a one-time latency hit per new schema.

## Connects to
- [structured outputs](../../../03-reasoning-generation/20-structured-outputs.md)
- [tool calling](../../../06-agents/32-tool-calling.md)
- [model ID versioning](../../../dev-surfaces/07-model-id-versioning.md)
- [regression testing](../../../09-evaluation/47-regression-testing.md)
