# Skill & plugin security scanning (supply-chain defense)

- **Category:** ③ New way of working
- **Date:** 2026-08-06  ·  **What it affects:** third-party skills and plugins installed into Claude, Claude Cowork, and Enterprise plugin marketplaces
- **Sources:** https://support.claude.com/en/articles/15927065-get-started-with-skill-and-plugin-scanning · https://venturebeat.com/security/anthropic-skill-scanners-passed-every-check-malicious-code-test-file · https://cyberscoop.com/anthropic-claude-code-security-automated-security-review/

## In one line
Anthropic now automatically scans third-party skills and plugins for malicious content when they're uploaded or edited, returning pass / warn / fail before the code can run in your org.

## What actually changed
A security check runs automatically whenever a third-party skill or plugin is uploaded or edited, reviewing its contents for signs of malicious behavior. It completes in the background, typically in one to two minutes, and returns one of three verdicts: **pass** (installs normally), **warn** (couldn't be fully verified — works but shows a caution banner requiring acknowledgment), or **fail** (malicious content detected — blocked, cannot be used). Scanning happens in a secure, isolated environment separate from normal Claude sessions; the scanned copy is deleted afterward, with only the result and basic metadata retained, and results are cached so re-uploading an identical skill returns instantly. It's available on Enterprise plans across Claude, Claude Cowork, and Enterprise plugin marketplaces. Stated limitation: it detects malicious *design*, not skills that merely behave unexpectedly without malicious intent — and reporting (VentureBeat) showed scanners can be evaded when the payload rides in via an unexpected vector like a test file.

## Why it matters
Skills and plugins are executable code and instructions that enter the agent's context — a classic software supply-chain surface, and a live one: audits of third-party marketplaces have found double-digit percentages of skills with vulnerabilities and dozens with confirmed malicious payloads. Automated scanning shifts the trust model from "install and hope" to "screened at the gate," which is table stakes once agents run third-party extensions with real permissions.

## Your point of view
- Treat skills/plugins exactly like npm/PyPI dependencies — they're a supply-chain vector, and scanning is necessary but not sufficient.
- The pass/warn/fail gate is a genuine control, but "pass" is not "safe": evasion via test files and unexpected-but-not-malicious behavior both slip through. Defense in depth still applies.
- The isolate-scan-then-delete design is the privacy-right way to do it; it's a good pattern to point to when others ask how to vet third-party agent code.

## What to do
- On Enterprise, keep scanning on and treat **warn** as "review before acknowledging," not a rubber stamp.
- Pair scanning with runtime containment — least-privilege tool/connector scopes and human-in-the-loop on side-effectful actions — so a slipped-through skill has a small blast radius.
- Maintain an allowlist of vetted skills/plugins for sensitive workspaces rather than open install.

## Connects to
- [AI security](../../../08-safety-trust/42-ai-security.md)
- [guardrails](../../../08-safety-trust/41-guardrails.md)
- [MCP](../../../06-agents/33-mcp.md)
