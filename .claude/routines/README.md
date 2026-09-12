# Routines (cloud agent specs)

Cloud routines run on Anthropic's infrastructure on a cron schedule — they have
**no local file by default**, so their definition would be lost or drift. This
folder is their **version-controlled source of truth**: each `*.json` is the exact
body used to create/update the routine, so it's reviewable, re-creatable, and
diffable like everything else.

## How to (re)create a routine from a spec here

Via the `schedule` skill (which wraps the `RemoteTrigger` API) — do NOT curl:

1. Open the spec JSON in this folder.
2. Generate a **fresh** `events[].data.uuid` (a new v4 UUID each create).
3. `RemoteTrigger` `action: "create"` with the body. On success you get a routine
   id → the routine lives at `https://claude.ai/code/routines/{id}`.
4. To change it later, edit the spec here AND `RemoteTrigger` `action: "update"`
   with the same `trigger_id` — keep this file and the live routine in sync.

A cloud routine requires a **connected GitHub account with write access** to the
repo it targets, or creation fails with `401 "Connect your GitHub account…"`.

## Routines

### `anthropic-radar-weekly.json`
- **What:** runs the weekly [`anthropic-radar`](../skills/anthropic-radar/SKILL.md)
  digest — scans Anthropic's sources, keeps only impactful items, writes
  categorized self-contained nuggets, commits them to a `radar/<date>` branch
  (never `main`).
- **Schedule:** Mondays **12:00 IST = 06:30 UTC** (`cron: 30 6 * * 1`).
- **Model:** `claude-sonnet-5`.  **Repo:** `calling-all-autobots/ai-concepts`.
- **Tools:** Bash, Read, Write, Edit, Glob, Grep, WebSearch, WebFetch.
- **Prompt:** self-contained (full methodology embedded), so it doesn't depend on
  the skill being on `main`.
- **Status:** created **disabled** for review — enable after a look, then it runs
  each Monday. Update `enabled: true` in the spec when you enable it live.
