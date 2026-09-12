# Harness design for long-running application development

- **Category:** ② New best practice
- **Date:** 2026-03-24  ·  **What it affects:** how you scaffold agents that build whole applications autonomously
- **Sources:** https://www.anthropic.com/engineering/harness-design-long-running-apps

## In one line
For agents that build a whole app unattended, the surrounding harness — a planner/generator/evaluator loop that hands off context through files — can matter as much as the base model.

## What actually changed
Anthropic published its recipe for long-running, autonomous application development. The core is a three-agent structure inspired by GANs: a **Planner** turns a brief prompt into a detailed spec (scope and high-level design, not implementation detail); a **Generator** builds features incrementally; and an **Evaluator** actually exercises the app via Playwright, checks it against an agreed contract, and returns detailed critique. Two failure modes drive the design. **Context anxiety**: as the context window fills, models (e.g. Sonnet 4.5) declare tasks done prematurely — the fix is context *resets* between sessions with structured handoff artifacts written to files, not compaction, so intent survives without dragging every stale token forward. **Self-flattery**: an agent grading its own work almost always praises it, so separating the doer from the judge is a strong lever. Concrete techniques: **sprint contracts** (generator and evaluator negotiate "what done looks like" before coding), explicit **grading criteria** (quality, originality, craft, functionality), and **file-based communication** for clean handoffs. In a retro-game-maker test, a solo agent took 20 min / $9 and shipped broken gameplay; the full harness took 6 hours / $200 and produced a working game. And crucially: "every component in a harness encodes an assumption about what the model can't do" — as Claude improved to 4.6, sprint decomposition became unnecessary and was removed.

## Why it matters
This reframes agent building. The model is one component; reliability at the multi-hour scale comes from context engineering and adversarial separation of roles. It also warns against over-engineering: harness complexity is a debt that a better model makes obsolete.

## Your point of view
- Separate the generator from the evaluator — self-grading is worthless; an independent judge with explicit criteria is the quality engine.
- Prefer context resets with file handoffs over compaction for very long tasks: you keep intent, not token sludge.
- Revisit your scaffolding every model upgrade and delete the crutches the new model no longer needs.
- The 6hr/$200 vs 20min/$9 gap is the honest cost of autonomous quality — budget for it.

## What to do
When building an app-building agent, split it into planner/generator/evaluator, wire the evaluator to a real browser-driver, define grading rubrics up front, and pass state through readable artifact files. Audit the harness at each model bump for components you can remove.

## Connects to
- [multi-agent](../../../06-agents/37-multi-agent.md)
- [planning & orchestration](../../../06-agents/36-planning-orchestration.md)
- [agentic systems](../../../06-agents/34-agentic-systems.md)
- [context windows](../../../01-foundations/05-context-windows.md)
