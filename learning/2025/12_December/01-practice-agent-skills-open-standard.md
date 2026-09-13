# Agent Skills become an open standard

- **Category:** ② New best practice
- **Date:** 2025-12-18  ·  **What it affects:** Agent Skills (the `SKILL.md` folder format), Claude.ai / Claude Code / Agent SDK / Claude Developer Platform, and any third-party agent that adopts the spec
- **Sources:** https://agentskills.io  ·  https://agentskills.io/specification  ·  https://github.com/agentskills/agentskills  ·  https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/

## In one line
The Agent Skills format Anthropic shipped in October is now a published open standard at agentskills.io, so a skill you write once runs on Claude, ChatGPT/Codex, GitHub Copilot, Cursor, Gemini CLI and dozens of other agents.

## What actually changed
A Skill is a folder with a required `SKILL.md` (YAML front-matter of at least `name` and `description`, plus instructions) and optional `scripts/`, `references/`, and `assets/`. Agents use **progressive disclosure**: at startup they load only each skill's name + description; when a task matches, they read the full `SKILL.md`; only then do they execute bundled scripts or open referenced files. That keeps many skills on hand for a tiny context cost.

On Dec 18, 2025 Anthropic moved this from a Claude-only feature to an **open standard**: a formal spec plus a reference SDK at agentskills.io, an open GitHub repo (`agentskills/agentskills`) accepting outside contributions, and a client showcase. Adopters already include GitHub Copilot, VS Code, OpenAI's ChatGPT/Codex, Cursor, Google's Gemini CLI, JetBrains Junie, Databricks, Snowflake, Block's Goose, and many more. Anthropic also announced **enterprise deployment controls** — admins can enforce which skills are available, gate sensitive capabilities, and monitor skill usage org-wide — plus partner-built skills from Canva, Stripe, Notion, and Zapier.

## Why it matters
This is the MCP playbook applied to agent capabilities: don't build a moat, define the substrate everyone builds on. For a PM it means procedural knowledge — a compliance checklist, a brand-deck format, a data-pipeline recipe — becomes a **portable, version-controlled artifact** that isn't locked to one vendor. It also reframes "prompt libraries" as governed assets with access control and audit, which is what enterprises actually need.

## Your point of view
- "Skills are the reusable unit of agent know-how — write once, run on any compliant agent. We should author skills, not per-tool prompts."
- "The open standard de-risks vendor lock-in: our internal skills survive a model or platform switch."
- "Progressive disclosure is the trick — dozens of skills cost almost no context until one is actually needed."

## What to do
- Standardize internal agent knowledge as `SKILL.md` folders in version control rather than scattered prompts.
- Read the spec at agentskills.io/specification and pilot one high-value workflow skill; test it in Claude Code and one non-Anthropic client to prove portability.
- If you're on Enterprise, plan for the new admin controls: who authors, who approves, which skills touch sensitive systems.

## Connects to
- [MCP](../../../agents/mcp.md) — the sibling open standard (tools/data access) that Skills complement.
- [Agentic systems](../../../agents/agentic-systems.md) — Skills are how you give an agent repeatable, specialized competence.
- [Tool calling](../../../agents/tool-calling.md) — Skills often bundle scripts the agent runs, layered on top of tool use.
