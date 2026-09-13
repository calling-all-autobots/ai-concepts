# Model Hardware Standard (MHS) — research preview

- **Category:** ① Product release
- **Date:** 2026-08-27  ·  **What it affects:** a new open protocol for AI agents to drive physical lab and factory instruments
- **Sources:** https://www.anthropic.com/news/model-hardware-standard-research-preview · https://www.cnbc.com/2026/08/27/anthropic-pushes-into-physical-world-with-new-standard-to-help-ai-agents-operate-machines.html

## In one line
Anthropic opened a research preview of the Model Hardware Standard — "MCP for physical machines" — a shared spec that lets a Claude agent operate microscopes, liquid handlers, and robotic arms.

## What actually changed
MHS is an open, model-agnostic specification that does for physical devices what the Model Context Protocol did for software tools: it standardizes how an agent discovers, addresses, and safely commands hardware. In the preview an agent can operate multiple lab/manufacturing instruments in parallel and run intricate procedures — routine drug-discovery experiments, laser calibration on a quantum computer. Anthropic claims it collapses hardware-integration time from weeks or months to hours or minutes. It began as a collaboration with HHMI Janelia Research Campus; early adopters include Genentech, Carnegie Mellon, QuEra Computing, Tetsuwan Scientific, and University of Washington labs. Access is gated to a first cohort of scientific labs and advanced manufacturers; Anthropic says it will open-source the full spec and that MHS is not tied to Claude models.

## Why it matters
This is Anthropic extending the "agent + open protocol" playbook from the digital world into the physical one. The strategic tell is the analogy to MCP: Anthropic wants to own the interface standard, not just the model. If MHS gets traction, "agent controls a robot arm" stops being bespoke integration work and becomes a protocol call, the way MCP made "agent calls a tool" routine.

## Your point of view
- MHS is a land-grab for the physical-agent interface layer, mirroring the MCP strategy: whoever defines the standard shapes the ecosystem regardless of which model wins.
- Model-agnostic and open-source-to-come is a deliberate adoption play — standards spread when they aren't a single vendor's lock-in.
- For most software PMs this is a horizon signal, not a roadmap item: real-world-facing products (bio, manufacturing, robotics) should watch it; pure-software teams should note the pattern.

## What to do
- If you touch lab automation, robotics, or scientific/manufacturing workflows, request preview access and evaluate MHS before building custom instrument integrations.
- Otherwise, file this as evidence that Anthropic's protocol strategy (MCP, now MHS) is a durable pattern — expect more "open standard, model-agnostic" moves and factor that into build-vs-buy thinking.

## Connects to
- [MCP](../../../agents/mcp.md)
- [agentic systems](../../../agents/agentic-systems.md)
- [build vs buy](../../../product-strategy/build-vs-buy.md)
