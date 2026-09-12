# July 2026 — Monthly Summary
_Anthropic learning radar · living document · last updated 12/09/2026_

**This month:** Opus 5 pushed SWE-bench toward ~96% at unchanged pricing, the MCP 2026-07-28 spec went stateless, and memory moved to categorized mid-conversation entries.

_A living monthly newsletter — re-swept and rewritten whenever new material lands in this month's folder._

---

## ① Product releases
- [Claude Opus 5](02-product-claude-opus-5.md) — frontier model at unchanged $5/$25 Opus pricing, 1M context, thinking on by default.
- [Managed Agents: effort, lifecycle webhooks, session seeding](03-product-managed-agents-effort-webhooks.md) — persist `effort` on the agent, react to environment/memory-store events without polling, seed sessions with up to 50 events.
- [Admin API user-management endpoints (beta)](04-product-user-management-admin-api.md) — manage Claude Enterprise members, invites, groups, and roles as code.
- [Updated memory system](05-product-updated-memory-system.md) — memory becomes individual, categorized, editable entries read mid-conversation instead of a daily summary.
- [Cowork on web/mobile + M365 write tools](06-product-cowork-web-mobile-m365-write-tools.md) — remote-run Cowork sessions everywhere; Claude can now send email and edit OneDrive/SharePoint (off by default).

## ② New best practices
- [MCP 2026-07-28 spec](01-practice-mcp-2026-07-28-spec.md) — stateless request/response core, governed MCP Apps/Tasks extensions, and OAuth/OIDC-hardened enterprise auth.
