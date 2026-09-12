# Learning — Anthropic Radar

Digests of **impactful** Anthropic changes, kept clean (minor patch notes are
deliberately excluded). Produced by the [`anthropic-radar`](../.claude/skills/anthropic-radar/SKILL.md)
skill (ongoing, weekly) and the [`radar-sweep`](../.claude/skills/radar-sweep/SKILL.md)
skill (one-off historical backfill).

Each item is a **self-contained knowledge document** — *what changed · why it
matters · a point of view · what to do* — tagged with one category:
**①** product release · **②** new best practice · **③** new way of working.

## Structure (the rule)

```
learning/<year>/<month>/<week>/     ← ongoing weekly runs
learning/<year>/<month>/            ← historical backfill (no weekly sub-folders)
```

Every month folder has a **`monthly-summary.md`** — a *living newsletter* that is
re-swept and rewritten whenever new material lands in that month.

## Browse

- **[2026](2026/README.md)** — Jan → Sep (Sep onward has weekly sub-folders)
- **[2025](2025/README.md)** — Nov, Dec
- **[reference/](reference/model-deprecations.md)** — cross-cutting living docs (e.g. the model-deprecation timeline) + the sweep audit trail

## How it runs (manual)

- **Weekly:** run `/anthropic-radar` in this repo (Mondays). It scans, filters,
  writes that week's nuggets to `learning/<year>/<month>/<week>/`, refreshes that
  month's `monthly-summary.md`, and commits to a `radar/<date>` branch.
- **Backfill:** `/radar-sweep` for a date range (already run for Nov 2025 → Aug 2026).
- A cloud-routine spec exists at [`.claude/routines/`](../.claude/routines/README.md)
  for later experimentation; auto-run is currently off (manual only).
