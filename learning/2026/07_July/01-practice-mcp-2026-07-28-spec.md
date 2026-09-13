# MCP 2026-07-28 spec: a stateless core, governed extensions, and hardened auth

- **Category:** ② New best practice
- **Date:** 2026-07-28  ·  **What it affects:** Model Context Protocol (MCP) servers, connectors, Claude MCP support
- **Sources:** https://blog.modelcontextprotocol.io/posts/2026-07-28/ · https://claude.com/blog/bringing-mcp-2026-07-28-to-claude

## In one line
MCP dropped its stateful session handshake for a plain request/response model, so an MCP server is now an ordinary HTTP workload you can run serverless, behind a round-robin load balancer, with no sticky sessions.

## What actually changed
The 2026-07-28 revision removes the initialization handshake and protocol-level sessions. Every request now carries what the server needs to process it, so any request can land on any instance. Three things follow:
- **Stateless core.** MCP moves from a bidirectional, stateful protocol to request/response. Servers no longer need shared session storage, which unlocks serverless/edge deployment and horizontal scaling.
- **Governed extensions framework.** MCP Apps (servers render interactive UI directly in the conversation) and Tasks (a proper lifecycle for long-running work) now ship as versioned extensions alongside Enterprise-Managed Authorization and OAuth Client Credentials.
- **Auth hardening.** Core authorization now tracks production OAuth 2.0 / OIDC: issuer validation, client credentials bound to their authorization server, and an Enterprise-Managed Authorization extension that lets an org gate MCP access through Okta or Microsoft Entra ID.

Anthropic is rolling support across Claude products (MCP Apps in-conversation UI, enterprise-managed auth with zero-touch provisioning, a connector observability dashboard, and MCP tunnels in research preview). The ecosystem cited 400M monthly SDK downloads, a 4x jump on the year.

## Why it matters
The old stateful model forced sticky sessions and per-connection state — awkward on serverless and a scaling tax at volume. Statelessness makes MCP servers behave like any other stateless microservice: cheaper to run, trivially scalable, and far easier to secure because there's no session state to hijack. The auth changes move MCP from "works in a demo" to "passes an enterprise security review."

## Your point of view
- This is a migration, not a patch: stateful servers built pre-2026-07-28 will need reworking, so treat it as a breaking protocol shift.
- Statelessness is the headline for scale, but the OAuth/Entra hardening is what actually unblocks enterprise adoption.
- MCP Apps blur the line between "tool" and "mini-app" — an MCP server can now own UI inside Claude, which changes how you think about connector UX.

## What to do
- Audit any MCP servers you own for reliance on the init handshake or session state; plan a rewrite to request/response.
- If you serve enterprises, adopt Enterprise-Managed Authorization so admins provision access via their existing IdP.
- Re-deploy stateless servers on serverless/edge to cut idle cost.

## Connects to
- [MCP](../../../agents/mcp.md)
- [AI security](../../../safety-trust/ai-security.md)
- [SDK](../../../dev-surfaces/sdk.md)
