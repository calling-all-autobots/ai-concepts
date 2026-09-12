# `ant apply` — manage agents as code

- **Category:** ③ New way of working
- **Date:** 2026-09-03  ·  **What it affects:** how agents/skills/memory get deployed (Developer Platform CLI)
- **Sources:** [Developer Platform release notes](https://docs.claude.com/en/release-notes/overview)

## In one line
Anthropic shipped **Terraform-for-agents**: you describe your agents, skills, memory stores, and deployments in files in your repo, run `ant apply`, review the diff, and it makes reality match the files — with a lockfile so it never creates duplicates.

## What actually changed
- A new CLI command that **"creates and updates agents, environments, skills, memory stores, and deployments from files in your repository."**
- It follows the **plan-then-apply** model: you run it, it shows the proposed changes, you approve, it executes.
- It writes a **`claude-lock.json`** lockfile. Per the docs: *"Commit the `claude-lock.json` lockfile it writes so that later runs, on your machine or in CI, update the same resources instead of creating new ones."* That lockfile is what makes runs idempotent — the same config updates the same resources instead of spawning copies.
- The whole agent configuration surface (previously clicked together in a console) becomes **files you can diff, review in a PR, and run in CI/CD.**

## Why it matters
This changes what "shipping an agent" *is*. Console-configured agents have the same problems hand-configured servers had a decade ago: no version history, no code review, no reproducibility between dev and prod, and no rollback — config drifts and nobody can say why. `ant apply` moves agents into the **infrastructure-as-code** discipline the rest of software already standardized on. For a PM this is the difference between "someone changed the agent and we're not sure what or when" and "every change to the agent is a reviewed, revertible commit." It also makes agents **CI-native** — they can be deployed by the same pipeline as the app, gated by the same evals.

## Your point of view
- "Agent config should live in the repo, not a console — `ant apply` finally makes that the paved path, and we should adopt it before our agent setup becomes un-auditable tribal knowledge."
- "The **lockfile is the important part**: it's what turns 'run a command' into 'reproducible deployment,' and it's why this is real IaC and not just a scripted button."
- "This is a **governance win, not just a dev-convenience** — reviewable, revertible agent changes are exactly what you want before you trust an agent in production."
- "It pairs naturally with **evals-as-CI**: config-as-code means an agent change is a PR, and a PR can be gated on your eval suite."

## What to do
1. **Adopt it for any agent we ship** — put agent/skill/memory definitions in the repo and make `ant apply` the only way they change (no more manual console edits).
2. **Commit `claude-lock.json`** and treat it like `package-lock.json` — it's what guarantees CI and local runs touch the same resources.
3. **Wire `ant apply` into the deploy pipeline** so agent changes go through the same review + eval gate as code changes.
4. In the meantime, **stop making one-off console edits** to anything you'll later want under version control — those become the drift you'll have to reconcile.

## Connects to
[Build vs. buy](../../../../11-product-strategy/53-build-vs-buy.md) · [Production LLM architecture](../../../../10-production-ops/48-production-architecture.md) · [Regression testing / evals-as-CI](../../../../09-evaluation/47-regression-testing.md) · [Agentic systems](../../../../06-agents/34-agentic-systems.md)
