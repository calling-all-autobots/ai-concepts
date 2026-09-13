# MCP Tunnels (research preview) + self-hosted sandboxes (public beta)

- **Category:** ① Product release
- **Date:** 2026-05-19  ·  **What it affects:** Claude Managed Agents; Messages API; enterprise agent infrastructure
- **Sources:** https://www.infoq.com/news/2026/05/claude-mcp-tunnels/ · https://9to5mac.com/2026/05/19/anthropic-enhances-claude-managed-agents-with-two-new-privacy-and-security-features/

## In one line
Two infrastructure options for Claude Managed Agents that keep enterprise data inside the enterprise: **self-hosted sandboxes** (run tool execution on your own compute) and **MCP tunnels** (agents reach private MCP servers without exposing them to the public internet).

## What actually changed
- **Self-hosted sandboxes (public beta):** tool/code execution runs on customer-controlled infrastructure — your own compute or managed providers (**Cloudflare, Daytona, Modal, Vercel**). Anthropic still runs orchestration, context handling, and recovery logic; only the *execution* moves into your environment.
- **MCP tunnels (research preview, gated — request access):** Managed Agents and the **Messages API** connect to **private MCP servers** over an encrypted connection established by a **lightweight gateway**. Agents can use internal databases, private APIs, knowledge bases, and ticketing systems as tools with **no inbound firewall changes and no public endpoints**; traffic stays end-to-end encrypted.
- Both are pre-GA (protocol/schema may shift); the research preview is open to Managed Agents customers, tunnels behind a gate.

## Why it matters
The biggest blocker to enterprise agents isn't capability — it's data residency and network exposure. Until now, letting a hosted agent touch an internal system meant either shipping data to Anthropic's execution environment or punching a hole to the public internet. Self-hosted sandboxes answer "where does the code run?" and MCP tunnels answer "how does the agent reach my private systems?" without a DMZ. This directly operationalizes the containment thesis from the same month's "How we contain Claude": keep execution and connectivity inside boundaries you control.

## Your point of view
- "This is the unlock for regulated buyers: you can adopt Managed Agents while keeping execution and internal-system access inside your own perimeter."
- "Note the split: Anthropic keeps the *brain* (orchestration, context, recovery), you keep the *hands* (execution) and the *reach* (tunnels). That's the hosted-agent trust boundary made explicit."
- "It's still preview — tunnels are gated and the protocol may change — so architect for it but don't hard-wire the current schema."

## What to do
- If a hosted-agent adoption stalled on data residency or network exposure, re-open it: pilot self-hosted sandboxes on Cloudflare/Modal/Vercel/Daytona or your own compute.
- Request MCP-tunnel access for the internal systems (DBs, ticketing, private APIs) you want agents to reach, and validate the gateway model with security before committing.
- Track the tunnel protocol for GA-breaking changes.

## Connects to
- [MCP](../../../agents/mcp.md) · [tool calling](../../../agents/tool-calling.md) · [AI security](../../../safety-trust/ai-security.md) · [production architecture](../../../production-ops/production-architecture.md)
