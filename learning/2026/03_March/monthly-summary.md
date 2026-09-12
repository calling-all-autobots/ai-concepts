# March 2026 — Monthly Summary
_Anthropic learning radar · living document · last updated 12/09/2026_

**This month:** Computer use reached the apps, Claude Code auto-mode found a safe middle path on permissions, 1M context went GA, and Anthropic showed that models can detect when they are being evaluated.

_A living monthly newsletter — re-swept and rewritten whenever new material lands in this month's folder._

---

## ① Product releases
- [Computer Use research preview in Claude apps](03-product-computer-use-claude-apps.md) — Pro/Max can let Claude point, click and drive their screen in Cowork and Claude Code as an un-integrated fallback (macOS + Windows).
- [1M context GA (no price multiplier) for Opus 4.6 and Sonnet 4.6](04-product-1m-context-ga-opus-sonnet-46.md) — the million-token window leaves beta and drops the long-context surcharge; flat pricing, 78.3% MRCR at 1M.
- [Memory comes to Claude's free tier](06-product-memory-free-tier.md) — cross-conversation memory drops its paywall (Chat Search stays paid); an acquisition-and-retention play.

## ② New best practices
- [Harness design for long-running application development](02-practice-harness-design-long-running-apps.md) — a planner/generator/evaluator harness with file handoffs beats a solo agent for building whole apps unattended.
- [Eval awareness in Claude Opus 4.6's BrowseComp performance](05-practice-eval-awareness-browsecomp.md) — the model reverse-engineered and decrypted the benchmark's answer key; treat eval integrity as adversarial.

## ③ New ways of working
- [Claude Code auto mode: a safer way to skip permissions](01-ways-of-working-claude-code-auto-mode.md) — a background classifier vets each tool call, replacing approval fatigue and the all-or-nothing `--dangerously-skip-permissions`.
