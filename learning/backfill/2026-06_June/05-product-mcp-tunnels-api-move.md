# MCP Tunnels management API moves to the Claude API

- **Category:** ① Product release
- **Date:** 2026-06-22  ·  **What it affects:** MCP Tunnels management API (`/v1/tunnels`), Managed Agents & Messages API
- **Sources:** https://platform.claude.com/docs/en/release-notes/overview · https://www.infoq.com/news/2026/05/claude-mcp-tunnels/

## In one line
MCP Tunnels — the feature that lets agents reach MCP servers inside a private network without opening inbound firewall rules — got a first-class management API on the Claude API, moving off the Admin API.

## What actually changed
- On **June 22, 2026** the tunnel management API **moved from `/v1/organizations/tunnels` (Admin API) to `/v1/tunnels` (Claude API)**.
- It requires the beta header **`anthropic-beta: mcp-tunnels-2026-06-22`** and the **`workspace:manage_tunnels`** Workload Identity Federation scope.
- The **old Admin API surface stays available during a migration window**.
- What tunnels do (unchanged): you deploy a lightweight gateway that opens an **outbound** encrypted connection to Anthropic, so **Managed Agents and the Messages API can call private MCP servers** without exposing them to the public internet or opening inbound ports. The capability was first shown at Code with Claude London (May 19, 2026) and remains beta.

## Why it matters
Moving tunnel management from the Admin API to the Claude API and scoping it at the workspace level means tunnels become a developer/workspace-owned resource rather than an org-admin-only one — you can provision and manage them from the same surface you build agents on, with WIF scoping instead of admin credentials. For enterprises, tunnels are the sanctioned pattern for "let the agent reach our internal systems" without VPNs or inbound firewall changes, which is usually the blocker for agent adoption behind a corporate perimeter.

## Your point of view
- "Tunnels are how you connect agents to internal MCP servers without punching inbound holes in the firewall — outbound-only is the security-team-friendly pattern."
- "The API move is small but signals productization: workspace-scoped, WIF-gated, on the main Claude API — not an admin afterthought."
- "It's still beta and behind a dated beta header — pin the header and expect churn."

## What to do
1. If you use tunnels, migrate management calls to `/v1/tunnels` with the `anthropic-beta: mcp-tunnels-2026-06-22` header and the `workspace:manage_tunnels` scope before the old surface is retired.
2. For any agent needing internal-system access, evaluate tunnels as the outbound-only alternative to VPN/inbound firewall rules.

## Connects to
- [MCP](../../../06-agents/33-mcp.md)
- [tool calling](../../../06-agents/32-tool-calling.md)
- [API endpoint](../../../dev-surfaces/04-api-endpoint.md)
- [AI security](../../../08-safety-trust/42-ai-security.md)
