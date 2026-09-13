# Inference Hooks (beta) — inline DLP gate for Claude Enterprise

- **Category:** ① Product release
- **Date:** 2026-08-05  ·  **What it affects:** Claude Enterprise — chat, Claude Code, Cowork, MCP connectors, and plugins
- **Sources:** https://thenextweb.com/news/anthropic-inference-hooks-dlp-claude-enterprise · https://clauding.de/en/posts/claude-enterprise-inference-hooks-dlp/ · https://waxell.ai/blog/claude-inference-hooks-inline-dlp

## In one line
Inference hooks route every governed prompt (and tool call) through the customer's own security server for an allow-or-deny verdict before Claude runs inference — an enterprise data-loss-prevention checkpoint in front of the model.

## What actually changed
Announced Aug 5, 2026 for Claude Enterprise. When enabled, Anthropic sends a **signed HTTPS POST** carrying the conversation transcript to the organization's configured AI-security-server endpoint; the org's server inspects it and returns **allow** or **deny** before inference proceeds. Requests are signed per the **Standard Webhooks** specification once the org generates its signing secret, so the receiver can verify the request genuinely came from Anthropic. One configuration covers chat, Claude Code, Cowork, MCP connectors, and plugins. Two real limits: the verdict is **binary** — the server can pass a prompt fully or block it fully, but cannot rewrite or redact parts of it; and despite broader launch wording, Anthropic's technical docs state **response-/tool-side enforcement is planned, not yet available** — so treat "tool responses are checked before returning to the model" as aspirational for now. (Context: the flagship **Opus 4.1 model was retired the same day, Aug 5** — `claude-opus-4-1-20250805` was removed from the API; migrate to Opus 4.8.)

## Why it matters
This hands enterprises a hard gate they control, in their own infrastructure, before sensitive data reaches the model — the DLP pattern security teams already run for email and SaaS, now applied to AI prompts. Because it's signed and centrally configured across every surface, it's an auditable, uniform control rather than per-app bolt-ons. The binary-verdict limit is the catch: real DLP usually wants redaction, and "block the whole prompt" is a blunt instrument that will frustrate users if tuned too aggressively.

## Your point of view
- This is the feature that lets a security-conscious enterprise say yes to Claude: the veto lives on their server, signed and verifiable.
- Binary allow/deny with no redaction means you'll trade false-positive friction against leak risk — plan for tuning, not set-and-forget.
- Don't rely on response-side inspection yet; per Anthropic's own docs it's roadmap, so design controls around prompt-side blocking today.

## What to do
- If you run Claude Enterprise with DLP needs, stand up an endpoint, generate the signing secret, and verify Standard Webhooks signatures on every request before trusting the transcript.
- Start in monitor/allow-mostly mode to measure false positives before switching to hard deny.
- Track when response-side enforcement ships; until then, put sensitive-data controls on the prompt path.

## Connects to
- [AI security](../../../safety-trust/ai-security.md)
- [guardrails](../../../safety-trust/guardrails.md)
- [privacy & PII](../../../safety-trust/privacy-pii.md)
