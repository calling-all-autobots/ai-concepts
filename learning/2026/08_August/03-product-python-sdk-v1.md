# Anthropic Python SDK v1.0 — breaking changes

- **Category:** ① Product release
- **Date:** 2026-08-20  ·  **What it affects:** `anthropic` Python SDK (0.x → 1.x); every Python service calling the Claude API
- **Sources:** https://github.com/anthropics/anthropic-sdk-python/releases/tag/v1.0.0 · https://github.com/anthropics/anthropic-sdk-python/blob/main/CHANGELOG.md · https://www.digitalapplied.com/blog/anthropic-anthropic-python-sdk-v1-breaking-change-migration

## In one line
The official Python SDK hit 1.0 — a real migration event, not a routine bump, with several changes that fail at runtime rather than at import.

## What actually changed
Published Aug 20, 2026. The headline breaks: the HTTP layer moves from `httpx` to `httpx2`; the minimum Python is now 3.10; the legacy Text Completions API is removed; the `temperature`, `top_p`, and `top_k` parameters are dropped from Messages methods; the tool runner's client-side `compaction_control` is removed; and `AnthropicBedrock` now errors when no region is set instead of guessing. The official `MIGRATION.md` enumerates eleven categories of change. Because some of these (e.g. a dropped sampling param, a missing Bedrock region) fail at call time, not at import, a service can pass CI and still break in production. On Aug 21, Claude Code v2.1.239 added a `/claude-api upgrade` command that automates migrating a codebase from `anthropic` 0.x to 1.x.

## Why it matters
This is a version-pinning and dependency-hygiene lesson made concrete. A pinned `anthropic>=0.x` that resolves to 1.0 on the next build can silently ship breakage. The runtime-failure category is the dangerous one: green tests are not proof of safety when the removed surface (a sampling knob, a Bedrock region) only executes on a real request path.

## Your point of view
- Pin exact SDK versions in production and upgrade deliberately — "latest" is how a breaking 1.0 sneaks in.
- Read `MIGRATION.md` before bumping; the eleven categories are the checklist, and the httpx2 swap plus the dropped sampling params are the ones most likely to bite.
- Dropping `temperature`/`top_p`/`top_k` from Messages signals Anthropic steering callers toward thinking/effort-based control over raw sampling — worth noting in how you tune outputs.

## What to do
- Audit your dependency file: pin `anthropic` to a known-good version now.
- When you migrate, run `/claude-api upgrade` in Claude Code as a first pass, then diff against `MIGRATION.md` manually — especially any code setting `temperature`/`top_p`/`top_k` or constructing `AnthropicBedrock` without a region.
- Add an integration test that actually hits the API path, since import-time and unit tests won't catch these.

## Connects to
- [SDK](../../../dev-surfaces/03-sdk.md)
- [model ID & versioning](../../../dev-surfaces/07-model-id-versioning.md)
- [sampling & decoding](../../../03-reasoning-generation/16-sampling-decoding.md)
