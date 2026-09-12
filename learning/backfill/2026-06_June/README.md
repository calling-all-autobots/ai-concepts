# Anthropic Radar — Backfill: June 2026

_Historical backfill month (part of the Nov 2025 → Aug 2026 radar sweep). Not a live weekly scan._

**7 nuggets** — all Product releases. A model-heavy month: two new model lines (Sonnet 5; Fable 5 / Mythos 5), two new surfaces (Claude Science, Claude Tag), and three platform changes (rate-limit tiers, MCP Tunnels API, code-execution REPL persistence). Note: Sonnet 4 & Opus 4 retirements from this window are folded into the central "Model deprecation timeline" nugget, not repeated here.

## ① Product releases
- [Claude Sonnet 5](01-product-claude-sonnet-5.md) — cheaper on paper ($2/$10), but a new tokenizer inflates the same text ~30%, eating much of the discount.
- [Claude Science](02-product-claude-science.md) — a research workbench wrapping existing models around 60+ scientific databases; workflow, not a new model.
- [Rate limits → Start / Build / Scale](03-product-rate-limit-tiers.md) — four tiers become three, limits rise, and Sonnet/Haiku now match Opus.
- [Claude Tag (Slack)](04-product-claude-tag-slack.md) — one shared @Claude teammate per channel, replacing the old per-user Claude in Slack app.
- [MCP Tunnels API move](05-product-mcp-tunnels-api-move.md) — tunnel management moves to `/v1/tunnels` on the Claude API for reaching private MCP servers.
- [Code-execution REPL persistence](06-product-code-execution-repl-persistence.md) — `code_execution_20260120` keeps notebook state across cells and unlocks programmatic tool calling.
- [Claude Fable 5 & Mythos 5](07-product-fable-5-mythos-5.md) — first public Mythos-class model, priced $10/$50, with a new `stop_reason: "refusal"` you must handle.
