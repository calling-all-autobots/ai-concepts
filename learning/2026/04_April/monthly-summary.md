# April 2026 — Monthly Summary
_Anthropic learning radar · living document · last updated 12/09/2026_

**This month:** The agent platform landed: Managed Agents (public beta, `ant` CLI), Cowork GA, agent memory, plus Opus 4.7 (92.3% SWE-bench) and Claude Design.

_A living monthly newsletter — re-swept and rewritten whenever new material lands in this month's folder._

---

## ① Product releases
- [Agent Memory for Managed Agents → public beta](01-product-agent-memory-managed-agents.md) — hosted agents get durable, categorized cross-session memory the platform manages, under the same `managed-agents-2026-04-01` header.
- [Claude Design (research preview)](02-product-claude-design.md) — talk to Claude to make prototypes, slides, and one-pagers; powered by Opus 4.7's stronger vision.
- [Claude Opus 4.7](03-product-opus-4-7.md) — SWE-bench Verified 92.3% at the same $5/$25 price, ~3x higher image resolution, new `xhigh` effort, and advisory Task Budgets.
- [Claude Cowork → GA](05-product-cowork-ga.md) — the desktop knowledge-work agent goes GA on macOS + Windows with six enterprise controls (RBAC, spend limits, native OpenTelemetry).
- [Managed Agents (public beta) + the `ant` CLI](06-product-managed-agents.md) — a fully managed agent harness (sandbox, tools, state, tracing) plus a CLI that versions API resources as YAML.

## ③ New ways of working
- [Routines in Claude Code](04-ways-of-working-routines-claude-code.md) — configure a Claude Code automation once and run it on a schedule/API/event in the cloud, laptop-independent; "cron for Claude Code."
- [Scaling Managed Agents: decouple the brain from the hands](07-ways-of-working-scaling-managed-agents.md) — split reasoning, execution, and the session log into three interfaces; state lives in a durable external log so compute becomes disposable.
