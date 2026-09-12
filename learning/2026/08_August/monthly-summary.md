# August 2026 — Monthly Summary
_Anthropic learning radar · living document · last updated 12/09/2026_

**This month:** The agent primitives — computer use, browser, Files, Skills, Admin — went GA in one wave, alongside Inference Hooks, self-hosted Claude Code, and supply-chain scanning for skills and plugins.

_A living monthly newsletter — re-swept and rewritten whenever new material lands in this month's folder._

---

## ① Product releases
- [Model Hardware Standard (MHS) — research preview](01-product-model-hardware-standard.md) — "MCP for physical machines"; agents drive lab and factory instruments via an open, model-agnostic spec.
- [Cross-app memory sync + Gmail/Drive/M365 write actions](02-product-apps-memory-sync-write-actions.md) — memory flows both ways between chat and Cowork, and Claude can now write, not just read — with approval on by default.
- [Anthropic Python SDK v1.0 — breaking changes](03-product-python-sdk-v1.md) — httpx2, Python 3.10 floor, dropped sampling params and Text Completions; some breaks fail at runtime, not import.
- [Agent primitives GA wave: Computer Use, Browser Use, Files, Skills, Admin](04-product-computer-browser-tools-ga-wave.md) — five primitives leave beta together; new Browser Use tool targets elements by accessibility-tree refs, plus web-tool domain allow/block lists.
- [Self-hosted environments for Claude Code (public beta)](05-product-self-hosted-claude-code.md) — sessions execute on your own runners inside your network; code and secrets never leave your infra.
- [Inference Hooks (beta) — inline DLP gate](07-product-inference-hooks.md) — every governed prompt is signed and routed to your own security server for an allow/deny verdict before inference (also notes the Aug 5 Opus 4.1 retirement).

## ③ New ways of working
- [Skill & plugin security scanning](06-ways-of-working-skill-plugin-scanning.md) — automated pass/warn/fail malware screening of third-party skills and plugins before they run — supply-chain defense at the gate.
