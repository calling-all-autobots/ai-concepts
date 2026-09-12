# Anthropic Radar — Backfill: February 2026

_Historical backfill month (part of the Nov 2025 → Aug 2026 radar sweep). Not a live weekly scan — reconstructed from official sources._

**This month: 6 nuggets** — 4 product releases, 1 new best practice, 1 new way of working.

## ① Product releases
- [Claude Code Remote Control](01-product-claude-code-remote-control.md) — steer a live local coding session from your phone or browser; code and tools stay local.
- [Automatic prompt caching](02-product-automatic-prompt-caching.md) — one top-level `cache_control`, no manual breakpoints (and Sonnet 3.7 & Haiku 3.5 retired the same day).
- [Claude Sonnet 4.6](03-product-claude-sonnet-4-6.md) — 1M context (beta) and near-frontier agentic coding at unchanged $3/$15 pricing; web search/fetch tools go GA.
- [Claude Opus 4.6](04-product-claude-opus-4-6.md) — new flagship with four-level `effort` dial (replacing `budget_tokens`), adaptive thinking, and a context-compaction API.

## ② New best practices
- [Quantifying infrastructure noise in agentic coding evals](06-practice-infrastructure-noise-agentic-evals.md) — compute headroom can swing benchmark scores by ~6 points; treat infra as a controlled variable.

## ③ New ways of working
- [Building a C compiler with a team of parallel Claudes](05-ways-of-working-c-compiler-parallel-claudes.md) — 16 agents, ~100K lines, and a reusable playbook for multi-agent orchestration on a shared codebase.
