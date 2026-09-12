# Anthropic Radar — Backfill: August 2026

_Historical backfill month, authored as part of the Phase 2 radar sweep (window 2025-11 → 2026-08). Not a live weekly scan._

**This month: 7 nuggets.**

## ① Product releases
- [Model Hardware Standard (MHS) — research preview](01-product-model-hardware-standard.md) — "MCP for physical machines"; agents drive lab and factory instruments via an open, model-agnostic spec.
- [Cross-app memory sync + Gmail/Drive/M365 write actions](02-product-apps-memory-sync-write-actions.md) — memory flows both ways between chat and Cowork, and Claude can now write, not just read — with approval on by default.
- [Anthropic Python SDK v1.0 — breaking changes](03-product-python-sdk-v1.md) — httpx2, Python 3.10 floor, dropped sampling params and Text Completions; some breaks fail at runtime, not import.
- [Agent primitives GA wave: Computer Use, Browser Use, Files, Skills, Admin](04-product-computer-browser-tools-ga-wave.md) — five primitives leave beta together; new Browser Use tool targets elements by accessibility-tree refs, plus web-tool domain allow/block lists.
- [Self-hosted environments for Claude Code (public beta)](05-product-self-hosted-claude-code.md) — sessions execute on your own runners inside your network; code and secrets never leave your infra.
- [Inference Hooks (beta) — inline DLP gate](07-product-inference-hooks.md) — every governed prompt is signed and routed to your own security server for an allow/deny verdict before inference (also notes the Aug 5 Opus 4.1 retirement).

## ③ New ways of working
- [Skill & plugin security scanning](06-ways-of-working-skill-plugin-scanning.md) — automated pass/warn/fail malware screening of third-party skills and plugins before they run — supply-chain defense at the gate.
