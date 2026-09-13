# Workload Identity Federation — killing the static Claude API key

- **Category:** ① Product release
- **Date:** 2026-05-06 (introduced; GA 2026-06-17)  ·  **What it affects:** Claude Platform authentication; API/SDK/Claude Code CLI
- **Sources:** https://claude.com/blog/workload-identity-federation · https://platform.claude.com/docs/en/manage-claude/workload-identity-federation

## In one line
Instead of a permanent Anthropic API key baked into your workload, Workload Identity Federation (WIF) lets that workload authenticate with the identity it *already has* (AWS IAM role, GCP/Kubernetes service account, Azure/Entra managed identity, GitHub Actions token, Okta/OIDC) and receive short-lived, scoped tokens per request.

## What actually changed
- **The problem it removes:** long-lived static API keys that never expire, get copied into env files and CI, and leak. WIF replaces them with **short-lived tokens (minutes, not never)**, scoped per request.
- **How it works:** a **federation rule** binds an external identity to a **service account**; at request time Claude Platform verifies the incoming **OIDC token**, matches its claims against your rules, and issues a short-lived access token within that service account's role scope. Every exchange is logged to an audit trail.
- **Service accounts:** new to the platform — each workload gets its **own named identity, roles, and audit trail** instead of sharing one key.
- **Providers:** any OIDC-compliant IdP, with native paths for **AWS IAM, Google Cloud, Kubernetes, Microsoft Entra ID, GitHub Actions, SPIFFE, and Okta**.
- **Timeline & migration:** introduced in May 2026, reached **general availability June 17, 2026**. API keys keep working alongside WIF, so you migrate **one workload at a time**. (Note: the candidate list dates this May 6; the official blog documents the June 17 GA and does not describe a formal May beta — treat May as the introduction window and June 17 as GA.)

## Why it matters
Static API keys are the single most common way LLM credentials leak — committed to repos, pasted in logs, shared across services with no per-workload attribution. WIF makes the credential ephemeral and ties every call to a real identity with its own audit trail, so a leaked token is near-worthless in minutes and you can actually answer "which workload made this call?" It's table-stakes security hygiene arriving for AI infrastructure.

## Your point of view
- "Static keys are a liability, not a convenience. WIF makes an exfiltrated credential expire before it's useful and gives you per-workload attribution."
- "The real win is service accounts + audit trails — you finally get identity, least-privilege scoping, and traceability instead of one shared secret."
- "Because keys still work alongside WIF, there's no reason to delay: migrate highest-risk workloads (CI, prod services) first."

## What to do
- Inventory where static Anthropic keys live (CI, prod services, notebooks) and rank by blast radius.
- Stand up a service account per workload and a federation rule against your existing IdP (AWS IAM / Entra / GitHub Actions / Okta); migrate one workload at a time.
- Set short token lifetimes and route the audit trail into your existing logging/SIEM.

## Connects to
- [API key](../../../dev-surfaces/api-key.md) · [AI security](../../../safety-trust/ai-security.md) · [privacy & PII](../../../safety-trust/privacy-pii.md) · [production architecture](../../../production-ops/production-architecture.md)
