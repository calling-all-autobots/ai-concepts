# Claude Cowork → generally available

- **Category:** ① Product release
- **Date:** 2026-04-09  ·  **What it affects:** Claude Cowork desktop agent (macOS + Windows); all paid plans; enterprise admin controls
- **Sources:** https://9to5mac.com/2026/04/09/anthropic-scales-up-with-enterprise-features-for-claude-cowork-and-managed-agents/ · https://www.eweek.com/news/claude-cowork-general-availability-enterprise-controls/

## In one line
Cowork — the agentic knowledge-work app that reads your files, works across your apps, and delivers finished work — left preview and went generally available on macOS and Windows to all paid plans, with six enterprise-management features.

## What actually changed
Cowork's path: macOS public beta in January, Windows in February, **GA on Apr 9, 2026**. It lives as a dedicated tab inside the Claude desktop app (next to Chat and Code) and shifts Claude "from conversation partner to colleague" — reading local files and folders, working across applications, running scheduled tasks, and returning finished work. GA added **six enterprise features**: role-based access controls (admins group users via SCIM and gate which Claude capabilities each group gets), group spend limits, usage analytics, expanded **OpenTelemetry** support (Cowork is described as the first desktop agent with native OTel, exporting activity logs to SIEM tools like Splunk, Datadog, or Elastic), a Zoom MCP connector, and per-tool/connector controls.

Note: the same news wave (Apr 8-9) also put **Managed Agents into public beta** — Cowork is the app that went GA; Managed Agents did not (see nugget 06).

## Why it matters
The GA signal is that Anthropic considers desktop agentic knowledge-work ready for real enterprise rollout, and the six features are exactly the governance controls a security/IT team demands before letting an agent touch local files and connected apps: identity-scoped access, spend caps, and auditable telemetry. OpenTelemetry-native logging into existing SIEMs is the detail that makes Cowork adoptable inside a regulated org rather than a shadow-IT tool.

## Your point of view
- "Cowork GA is Anthropic's enterprise knowledge-work play — the story isn't the agent, it's the admin controls that make it deployable."
- "Native OpenTelemetry into Splunk/Datadog is the unlock for security sign-off; that's what I'd lead with to IT."
- "It's Windows + macOS and on all paid plans now, so 'we're waiting for GA' is no longer an excuse to not pilot it."

## What to do
- If you evaluated Cowork in beta, restart the pilot on GA and wire it into your SCIM identity provider and SIEM via OpenTelemetry from day one.
- Set group spend limits and per-tool connector controls before broad rollout.
- Use usage analytics to find which teams actually get value before expanding seats.

## Connects to
- [agentic systems](../../../06-agents/34-agentic-systems.md)
- [product strategy](../../../11-product-strategy/)
- [production architecture](../../../10-production-ops/48-production-architecture.md)
