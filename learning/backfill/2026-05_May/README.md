# Anthropic Radar — Backfill: May 2026

_Historical backfill month (part of the Nov 2025 → Aug 2026 radar sweep). Not a live weekly digest._

**6 nuggets** — 5 product releases, 1 new best practice.

## ① Product releases
- [Claude Opus 4.8 + Dynamic Workflows research preview](01-product-opus-4-8-dynamic-workflows.md) — new frontier model (1M ctx + high effort by default) that plans a job and runs hundreds of parallel subagents in one Claude Code session.
- [MCP Tunnels + self-hosted sandboxes](03-product-mcp-tunnels-self-hosted-sandboxes.md) — run Managed Agent execution on your own compute and reach private MCP servers with no public endpoint.
- [Claude Platform on AWS](04-product-claude-platform-on-aws.md) — Anthropic's native platform (APIs, console, day-one betas) inside your AWS account, billed via one AWS invoice.
- [Multi-agent orchestration + Outcomes + Dreaming](05-product-multi-agent-orchestration-outcomes-dreaming.md) — platform-level fan-out (20 subagents/25 threads), a rubric-driven grader loop, and between-sessions memory consolidation.
- [Workload Identity Federation](06-product-workload-identity-federation.md) — kill the static API key: short-lived, scoped tokens from your existing IdP, per-workload service accounts and audit trails.

## ② New best practices
- [How we contain Claude](02-practice-how-we-contain-claude.md) — contain capable agents with deterministic environmental boundaries (sandbox/VM/egress), not probabilistic model-layer defenses; size isolation to the audience's blast radius.
