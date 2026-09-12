# Agent primitives GA wave: Computer Use, Browser Use, Files, Skills, Admin

- **Category:** ① Product release
- **Date:** 2026-08-19  ·  **What it affects:** Claude Developer Platform tool types — computer use, the new browser use tool, Files API, Skills API, Admin user-management API; web-tool domain controls
- **Sources:** https://platform.claude.com/docs/en/agents-and-tools/tool-use/browser-use-tool · https://www.digitalapplied.com/blog/claude-platform-betas-ga-computer-use-files-skills · https://thenewstack.io/anthropic-browser-use-tool/

## In one line
Five agent-building primitives left beta on the same day (Aug 19–20), and a genuinely new Browser Use tool shipped that drives the web via the accessibility tree instead of guessing pixel coordinates.

## What actually changed
Going GA together: **computer use**, the **Files API**, the **Agent Skills / Skills API**, and the **Admin API** user-management endpoints for Claude Enterprise. The new piece is **Browser Use** — a separate client toolset with type `browser_toolset_20260801` (not a rename of computer use). It reads a page's accessibility tree and returns elements tagged with references like `[ref_2]`; Claude targets elements by `ref` (surviving layout shifts) with pixel coordinates as a fallback. It ships 31 member tools (27 on by default — navigate, click, type, `read_page`, `find`, `form_input`, tab management; 4 off by default — `javascript_exec`, `file_upload`, `read_console`, `read_network`), supports **batch actions** (multiple calls per turn, stop at first failure), and needs no beta header. It runs on the Claude API and Vertex AI, is ZDR-eligible, and is **not** available on AWS/Bedrock or Microsoft Foundry. Alongside, `web_search`/`web_fetch` gained `allowed_domains`/`blocked_domains` lists (use one or the other, not both; subdomains included; org-level ceiling set in Console → Privacy). Note: **Opus 4.1 (`claude-opus-4-1-20250805`) was retired Aug 5**, so pin GA tool work to current models (`claude-opus-5`, `claude-sonnet-5`, `claude-opus-4-8`).

## Why it matters
"GA" is a production-support signal: SLAs, stability commitments, and no beta-header churn. Browser Use matters most — accessibility-tree targeting is far more reliable and cheaper than screenshot-and-coordinate computer use for web tasks, because refs survive re-renders and don't burn tokens on images. Domain allow/block lists are the guardrail that makes autonomous web agents deployable: they bound where an agent can reach.

## Your point of view
- Prefer Browser Use over computer use for anything that lives in a webpage — semantic refs beat coordinate-guessing on reliability and cost; keep computer use for multi-app/native-UI work.
- Domain allowlists blunt the obvious exfiltration leaks but not clever ones (a permitted domain can still be abused) — treat them as a floor, not a full defense.
- The Bedrock/Foundry exclusion is a real portability constraint for regulated shops standardized on those clouds.

## What to do
- Delete now-unneeded beta headers for the five GA'd surfaces; confirm each against release notes before removing.
- For web automation, migrate to `browser_toolset_20260801` and design around refs from `read_page`/`find`; enable the 4 optional members only when required.
- Set `allowed_domains` on production web agents and an org-level ceiling in Console → Privacy.

## Connects to
- [tool calling](../../../06-agents/32-tool-calling.md)
- [agentic systems](../../../06-agents/34-agentic-systems.md)
- [AI security](../../../08-safety-trust/42-ai-security.md)
- [model ID & versioning](../../../dev-surfaces/07-model-id-versioning.md)
