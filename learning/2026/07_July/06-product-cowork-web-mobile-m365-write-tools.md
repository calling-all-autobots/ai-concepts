# Cowork reaches web and mobile; Microsoft 365 connector gains write tools

- **Category:** ① Product release
- **Date:** 2026-07-07  ·  **What it affects:** Claude Cowork (web/iOS/Android), Microsoft 365 connector
- **Sources:** https://woyable.com/en/posts/claude-cowork-web-mobile-expansion · https://findskill.ai/blog/claude-cowork-send-email-microsoft-365/

## In one line
Cowork left the desktop app for the web (claude.ai) and mobile (iOS/Android) with sessions running remotely, and the Microsoft 365 connector gained write tools so Claude can draft/send email, manage calendar and mailbox settings, and create/update OneDrive and SharePoint files.

## What actually changed
On 2026-07-07:
- **Cowork on web + mobile (beta, Max plan first).** Cowork sessions now run remotely, with files and session state saved to your Claude account so work follows you across devices. Scheduled tasks can complete with no device online.
- **Write tools for the Microsoft 365 connector.** With them enabled, Claude can "draft, send, and organize email, manage calendar events, update mailbox settings, and create and update files in OneDrive and SharePoint." Guardrails: write tools are **off by default**; every email Claude sends carries an **agent-initiated attribution header**; attachments aren't supported; and **Teams stays read-only**.

## Why it matters
Moving Cowork off the desktop and onto remote-run web/mobile turns it from a machine-bound tool into an always-available agent surface — the "scheduled task completes with no device online" behavior is the tell that these are genuinely server-side agents, not local automations. Adding *write* actions to M365 is the bigger line to cross: reading your inbox is low-stakes; sending email and editing SharePoint files on your behalf is a real side-effecting agent. The off-by-default posture and the attribution header show Anthropic treating write access as a consent-and-traceability problem, not just a capability.

## Your point of view
- The important word is *write*: read connectors inform, write connectors act — this is where connector risk (and value) steps up sharply.
- Off-by-default + agent-initiated email headers + no-attachments + read-only Teams is a sensible blast-radius design; expect to defend those defaults, not loosen them casually.
- Remote-run Cowork sessions make "agent that keeps working while you're away" real for knowledge work, which changes the pitch from assistant to delegate.

## What to do
- Before enabling M365 write tools, decide scope deliberately (email send vs file edit) and communicate that Claude-sent mail is tagged as agent-initiated.
- Treat write-tool enablement as a governance decision: who can turn it on, for which mailboxes/sites.
- Try Cowork on web/mobile for a recurring, schedulable task to see the remote-execution model in practice.

## Connects to
- [Agentic systems](../../../agents/agentic-systems.md)
- [Tool calling](../../../agents/tool-calling.md)
- [Guardrails](../../../safety-trust/guardrails.md)
