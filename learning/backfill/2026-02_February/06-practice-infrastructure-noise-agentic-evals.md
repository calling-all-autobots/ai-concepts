# Quantifying infrastructure noise in agentic coding evals — the leaderboard gap might just be a bigger VM

- **Category:** ② New best practice
- **Date:** 2026-02-05  ·  **What it affects:** how you run and read agentic coding benchmarks (evals / LLMOps)
- **Sources:** https://www.zenml.io/llmops-database/infrastructure-noise-in-agentic-coding-evaluations · https://x.com/AnthropicAI/status/2019501512200974686

## In one line
Anthropic showed that the compute you give an agent (CPU/RAM headroom) can swing agentic coding benchmark scores by several points — sometimes more than the gap between the top models — so infrastructure has to be treated as a controlled variable, not background.

## What actually changed
Running Terminal-Bench 2.0 on Google Kubernetes Engine, Anthropic's scores didn't match the official leaderboard and their infra error rate was surprisingly high. Systematic testing across **six resource configurations** found a **6 percentage-point gap** between the most- and least-resourced setups. The mechanism is two-fold:
- **Stability.** At strict 1× resource enforcement, **5.8% of tasks failed on infrastructure errors** (pods crashing on transient memory spikes) — not model failures. At **3× headroom, infra errors dropped to 2.1%**.
- **Capability.** Beyond just preventing spurious failures, more generous allocations actively let agents solve problems they couldn't solve before (more room to compile, run tests, spawn processes).
They also noted pass rates drift with time of day, likely tracking API latency and traffic. Recommendations: specify **both** guaranteed allocations **and** hard kill thresholds, calibrate resource bands empirically, and treat resource configuration as a first-class experimental variable.

## Why it matters
Agentic evals differ from static Q&A benchmarks: the model interacts with a live runtime — installing dependencies, running tests, iterating — so the environment is part of the score. A "Model A beats Model B by 3 points" claim is meaningless if the harnesses ran on different-sized machines. This reframes benchmark literacy: for agentic numbers, you need the infra spec alongside the score, or the comparison is noise.

## Your point of view
- Treat agentic-coding leaderboard deltas with suspicion unless infra is held constant — a 6-point config swing can dwarf the model gap being advertised.
- Infra noise has two distinct effects: it fabricates failures (stability) and it caps ceilings (capability); both bias comparisons, and only the first is obviously "an error."
- For your own evals, report the resource config as part of the result — an eval number without its environment is not reproducible.

## What to do
- When comparing models on agentic benchmarks, demand or fix the environment spec (CPU/RAM, kill thresholds); don't compare across unknown harnesses.
- In your eval harness, set explicit guaranteed resources and hard kill limits, and calibrate the bands empirically before trusting scores.
- Run repeated trials and watch for time-of-day drift; average over trials rather than reading a single run.

## Connects to
- [evaluation methods](../../../09-evaluation/45-evaluation-methods.md)
- [benchmarks](../../../09-evaluation/46-benchmarks.md)
- [regression testing](../../../09-evaluation/47-regression-testing.md)
- [observability](../../../10-production-ops/50-observability.md)
