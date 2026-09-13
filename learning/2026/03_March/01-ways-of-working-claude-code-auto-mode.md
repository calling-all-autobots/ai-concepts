# Claude Code auto mode: a safer way to skip permissions

- **Category:** ③ New way of working
- **Date:** 2026-03-24  ·  **What it affects:** Claude Code (CLI, VS Code, Desktop); permission model for agentic coding
- **Sources:** https://claude.com/blog/auto-mode · https://www.anthropic.com/engineering/claude-code-auto-mode

## In one line
A background classifier vets every tool call in real time, so Claude Code can run long tasks with far fewer approval prompts without you resorting to the all-or-nothing `--dangerously-skip-permissions`.

## What actually changed
Claude Code has three permission postures now. **Default** asks you to approve every file write and bash command. **`--dangerously-skip-permissions`** ("YOLO mode") bypasses all checks and is only safe in a throwaway sandbox. **Auto mode** is the new middle path: before each tool call executes, a background AI classifier inspects it and blocks anything that looks destructive — mass file deletion, sensitive-data exfiltration, malicious code execution — while letting safe operations run unattended. If it blocks something, Claude is told and tries another approach. It deliberately errs toward allowing when intent is ambiguous, so it is a risk reducer, not a guarantee. Enable it in the CLI with `claude --enable-auto-mode`, then cycle modes with Shift+Tab; in Desktop/VS Code toggle it under Settings → Claude Code. Admins can disable it fleet-wide with `"disableAutoMode": "disable"` in managed settings. It launched Mar 24, 2026 as a research preview for the Team plan on Sonnet 4.6 / Opus 4.6, and reached general availability for all users on Jul 10, 2026.

## Why it matters
The real hazard of the old model was approval fatigue: when Claude asks for the hundredth approval, people stop reading and rubber-stamp — so the "safe" default quietly degrades into blind trust. Auto mode moves the vetting from a tired human to a classifier that reviews every call at machine speed and never skims. It is defense-in-depth applied to the harness, not the model.

## Your point of view
- Auto mode is the honest answer to a workflow everyone was already abusing — teams ran `--dangerously-skip-permissions` because default mode was unusable for long tasks.
- Frame it as "blast-radius reduction," not "hands-off autonomy": the classifier can be fooled and leans permissive, so it complements a sandbox rather than replacing one.
- The admin `disableAutoMode` switch is the governance lever — decide the org default deliberately.

## What to do
Use auto mode for long, well-scoped tasks inside a git working tree you can revert; keep `--dangerously-skip-permissions` only for disposable containers. Never point either at production credentials or a directory with secrets. For teams, set the managed-settings default and document when each mode is appropriate.

## Connects to
- [agentic systems](../../../agents/agentic-systems.md)
- [guardrails](../../../safety-trust/guardrails.md)
- [AI security](../../../safety-trust/ai-security.md)
