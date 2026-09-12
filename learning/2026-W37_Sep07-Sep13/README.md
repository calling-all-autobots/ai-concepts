# Anthropic Radar — Week of Sep 07–13, 2026 (2026-W37)

_Scanned 12/09/2026. Sources confirmed against the official announcement, pricing docs, and Developer Platform release notes._
_**First run** — 4-week look-back (Aug 15 – Sep 13) to backfill, then weekly from here._

**This scan: 3 impactful items** (1 product · 0 new best-practice · 2 ways of working). Each nugget below is a self-contained read — what changed, why it matters, a point of view, and what to do.

## ① Product releases
- [Claude Fable 5.1 & Mythos 5.1](01-product-fable-mythos-51.md) — new top-tier models: 1M context, 128k output, always-on thinking, **cache reads at ¼ price**.

## ② New best practices
- **Nothing new this scan.** No Anthropic engineering post published in the look-back window. (See first-run foundations below.)

## ③ New ways of working
- [`ant apply` — agents/skills/memory as code](02-ways-of-working-ant-apply.md) — declarative, lockfile-backed agent config (GitOps for agents).
- [Managed Agents `auto` permission mode](03-ways-of-working-managed-agents-auto.md) — server-side tool-call evaluation.

## 📚 First-run foundations (older, but you may have missed these)
_Not new this week — flagged once because they changed how people build. Won't reappear._
- **Effective context engineering for AI agents** (2025-09-29) — smallest set of high-signal tokens; avoid bloated tool sets; just-in-time retrieval; compaction/note-taking for long tasks. → https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
- **Effective harnesses for long-running agents** (2025-11-26) — a JSON feature-list with pass/fail flags + a `claude-progress.txt` alongside git history so a fresh context window can resume work. → https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents

## Excluded this scan (kept clean)
- **Claude Code v2.1.260 / .268 / .269** (Sep 4–11) — point releases; `claude plugin eval`, `/output-style`, agent map, fullscreen diff, gateway pricing parity. Tooling polish/new-knobs, no capability class change. _(Flag `claude plugin eval` if you do plugin work.)_
- **Smart reports (beta) for Enterprise** (Sep 10) — usage/cost analytics; Enterprise admin feature, not core to concept study.
- **`ant beta:sessions connect` CLI** (Sep 10) — attach terminal to live sessions; dev convenience.
- **Per-message effort on Google Cloud** (Sep 3) — availability/parity, not a new capability.
- **Commerce agent blueprint** (Sep 2) — reference implementations (retail/travel/telecom/ticketing); a sample, not a capability. _(Surface if you want vertical-agent patterns.)_
