# November 2025 — Monthly Summary
_Anthropic learning radar · living document · last updated 12/09/2026_

**This month:** Opus 4.5 set a new coding bar (80.9% SWE-bench) and added the `effort` dial, while the platform learned to fight context bloat — Tool Search Tool, code-execution-with-MCP, and the long-running-agent harness.

_A living monthly newsletter — re-swept and rewritten whenever new material lands in this month's folder._

---

## ① Product releases
- [Claude Opus 4.5 — first model over 80% on SWE-bench Verified](02-product-claude-opus-4-5.md) — 80.9% SWE-bench at $5/$25 per M, plus an `effort` knob that hits Sonnet-4.5 quality with 76% fewer tokens.
- [Structured Outputs (public beta) — guaranteed schema conformance](04-product-structured-outputs-beta.md) — constrained decoding makes JSON/tool output provably match your schema, so you can delete the retry/repair code.

## ② New best practices
- [Effective harnesses for long-running agents](01-practice-long-running-agent-harnesses.md) — externalize durable state to a feature-list JSON + `claude-progress.txt` + git so any fresh session resumes cleanly.
- [Advanced tool use: the Tool Search Tool](03-practice-tool-search-tool.md) — `defer_loading: true` cuts tool-definition context ~85% (72K→500 tokens) and lifts tool-selection accuracy to 88.1% on Opus 4.5.
- [Code execution with MCP](05-practice-code-execution-with-mcp.md) — expose MCP servers as an importable code API and filter in-sandbox; a worked example drops from 150,000 to 2,000 tokens.
