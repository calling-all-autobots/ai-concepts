# June 2026 — Monthly Summary
_Anthropic learning radar · living document · last updated 12/09/2026_

**This month:** Sonnet 5 cut the price of near-frontier work (watch the tokenizer inflation), Fable 5 & Mythos 5 opened the Mythos-class line, and MCP tunnels + REPL persistence deepened the agent stack.

_A living monthly newsletter — re-swept and rewritten whenever new material lands in this month's folder._

---

## ① Product releases
- [Claude Sonnet 5](01-product-claude-sonnet-5.md) — cheaper on paper ($2/$10), but a new tokenizer inflates the same text ~30%, eating much of the discount.
- [Claude Science](02-product-claude-science.md) — a research workbench wrapping existing models around 60+ scientific databases; workflow, not a new model.
- [Rate limits → Start / Build / Scale](03-product-rate-limit-tiers.md) — four tiers become three, limits rise, and Sonnet/Haiku now match Opus.
- [Claude Tag (Slack)](04-product-claude-tag-slack.md) — one shared @Claude teammate per channel, replacing the old per-user Claude in Slack app.
- [MCP Tunnels API move](05-product-mcp-tunnels-api-move.md) — tunnel management moves to `/v1/tunnels` on the Claude API for reaching private MCP servers.
- [Code-execution REPL persistence](06-product-code-execution-repl-persistence.md) — `code_execution_20260120` keeps notebook state across cells and unlocks programmatic tool calling.
- [Claude Fable 5 & Mythos 5](07-product-fable-5-mythos-5.md) — first public Mythos-class model, priced $10/$50, with a new `stop_reason: "refusal"` you must handle.
