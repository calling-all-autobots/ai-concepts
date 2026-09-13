# Cross-app memory sync + Gmail/Drive/M365 write actions

- **Category:** ① Product release
- **Date:** 2026-08-25  ·  **What it affects:** Claude apps (chat + Cowork) memory; Google Workspace and Microsoft 365 connectors
- **Sources:** https://9to5mac.com/2026/08/25/anthropic-update-unifies-memory-feature-across-claude-cowork-and-chat/ · https://techcrunch.com/2026/08/25/claude-cowork-finally-remembers-what-you-told-the-app-in-chat/ · https://explainx.ai/blog/claude-gmail-drive-workspace-connectors-august-2026

## In one line
Claude's memory now flows both ways between chat and Cowork, and Claude can now write — send Gmail, manage Drive files, update OneDrive/SharePoint — not just read.

## What actually changed
Two related moves. First (Aug 25), memory was unified across the main chat interface and Cowork (Anthropic's computer-use agent): what Claude learns in chat is available when Cowork runs a cloud task, and vice-versa. Memory is on by default on Free, Pro, and Max across web, desktop, and mobile. Second, write actions landed for connectors. On Aug 18 Claude gained the ability to send emails in Gmail and manage files in Google Drive; the Microsoft 365 connector gained write tools (send email, update OneDrive/SharePoint files) on Jul 7, having been read-only before. Every write action ships with human-in-the-loop approval on by default; on Team/Enterprise, owners choose whether members can skip per-action confirmation.

## Why it matters
Read-only assistants summarize; write-capable assistants act, which is a categorically higher trust and risk tier. Sending an email or overwriting a shared file is irreversible and side-effectful — exactly the class of action that needs a confirmation gate. Cross-app memory raises the stakes: an agent that remembers across surfaces and can also take real actions is more useful and a larger blast radius for prompt injection or a bad memory.

## Your point of view
- The approval-on-by-default posture is the right call and the story here: Anthropic is treating write actions as a permissioned, human-in-the-loop tier, not a silent capability.
- Cross-app memory is what makes Cowork feel like one assistant instead of many — but it also means one poisoned memory can influence actions everywhere.
- For enterprise buyers, the real question is admin control: who can turn off per-action confirmation, and is that logged?

## What to do
- If you build on Claude connectors, design flows assuming approval prompts exist by default; don't architect for silent writes.
- Enterprise admins: review the Team/Enterprise setting that lets members skip per-action confirmation, and keep it off unless a workflow truly warrants it.
- Treat memory + write-action combos as a security surface — audit what memories can influence side-effectful tools.

## Connects to
- [agent memory](../../../agents/agent-memory.md)
- [AI security](../../../safety-trust/ai-security.md)
- [guardrails](../../../safety-trust/guardrails.md)
