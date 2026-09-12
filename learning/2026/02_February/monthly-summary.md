# February 2026 — Monthly Summary
_Anthropic learning radar · living document · last updated 12/09/2026_

**This month:** Two frontier models in one month (Opus 4.6, Sonnet 4.6), automatic prompt caching, Claude Code Remote Control, and parallel-agent engineering coming of age.

_A living monthly newsletter — re-swept and rewritten whenever new material lands in this month's folder._

---

## ① Product releases
- [Claude Code Remote Control](01-product-claude-code-remote-control.md) — steer a live local coding session from your phone or browser; code and tools stay local.
- [Automatic prompt caching](02-product-automatic-prompt-caching.md) — one top-level `cache_control`, no manual breakpoints (and Sonnet 3.7 & Haiku 3.5 retired the same day).
- [Claude Sonnet 4.6](03-product-claude-sonnet-4-6.md) — 1M context (beta) and near-frontier agentic coding at unchanged $3/$15 pricing; web search/fetch tools go GA.
- [Claude Opus 4.6](04-product-claude-opus-4-6.md) — new flagship with four-level `effort` dial (replacing `budget_tokens`), adaptive thinking, and a context-compaction API.

## ② New best practices
- [Quantifying infrastructure noise in agentic coding evals](06-practice-infrastructure-noise-agentic-evals.md) — compute headroom can swing benchmark scores by ~6 points; treat infra as a controlled variable.

## ③ New ways of working
- [Building a C compiler with a team of parallel Claudes](05-ways-of-working-c-compiler-parallel-claudes.md) — 16 agents, ~100K lines, and a reusable playbook for multi-agent orchestration on a shared codebase.
