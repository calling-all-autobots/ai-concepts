# Building a C compiler with a team of parallel Claudes — a real multi-agent orchestration playbook

- **Category:** ③ New way of working
- **Date:** 2026-02-05  ·  **What it affects:** multi-agent / parallel agent orchestration on shared codebases
- **Sources:** https://www.anthropic.com/engineering/building-c-compiler · https://www.infoq.com/news/2026/02/claude-built-c-compiler/

## In one line
Anthropic's Nicholas Carlini let 16 Claude (Opus 4.6) agents work in parallel, mostly unsupervised, to build a 100,000-line C compiler in Rust — and the write-up is really a field guide to what makes many agents on one codebase actually work.

## What actually changed
The experiment: 16 parallel Claude instances, running Opus 4.6, tasked with writing a Rust C compiler from scratch that could compile the Linux kernel. Over ~2 weeks, ~2,000 Claude Code sessions, ~$20,000 in API cost, and ~2 billion input / 140 million output tokens, they produced ~100,000 lines that compiled Linux 6.9 on x86, ARM, and RISC-V (plus QEMU, FFmpeg, SQLite, PostgreSQL, Redis) with a ~99% pass rate on most compiler test suites. Coordination mechanics: a bare git repo, one Docker container per agent with the repo mounted at `/upstream`, text files in `current_tasks/` used as a lock-file mechanism to claim work, and git conflicts forcing resolution when two agents grabbed the same task. Hard-won lessons:
- **The verifier must be near-perfect.** Agents optimize whatever you measure, so a weak test suite gets gamed; strong tests are the steering wheel.
- **Fresh containers need orientation.** Extensive READMEs and frequently-updated progress files let an agent re-derive "where are we" on each new session.
- **Break monoliths into parallelizable units.** A single "compile the kernel" task paralyzed agents; using GCC as a known-good oracle let agents work file-by-file independently.
- **Specialize agents** — separate ones for dedup, performance, code quality, and docs.
Limits: the task hit Opus 4.6's ceiling (e.g. 16-bit x86 codegen fell back to GCC), and new features frequently broke existing functionality.

## Why it matters
This is the most concrete public evidence to date that "throw more parallel agents at it" can produce real, large software — but only inside a harness that supplies verification, shared state, task-claiming, and re-orientation. The compiler is almost a side effect; the reusable asset is the orchestration pattern.

## Your point of view
- The bottleneck in multi-agent work is not model IQ, it is the harness: verifier quality, task decomposition, and shared coordination state decide success.
- "Agents optimize the verifier" is the load-bearing insight — invest in tests/oracles before adding more agents; a known-good oracle (here, GCC) is often what unlocks parallelism.
- Cost is real ($20K, 2B tokens) — parallel agent swarms are a capability, not a default; reserve them for well-specified, verifiable problems.

## What to do
- Before parallelizing, build a near-perfect verifier and, where possible, a known-good oracle to check against.
- Give agents persistent shared state: a task-claim mechanism (lock files/queue), git for merge conflicts, and living README/progress files.
- Decompose big goals into independently verifiable units and assign specialized roles rather than cloning one generalist.

## Connects to
- [multi-agent systems](../../../06-agents/37-multi-agent.md)
- [planning & orchestration](../../../06-agents/36-planning-orchestration.md)
- [agentic systems](../../../06-agents/34-agentic-systems.md)
- [agent memory](../../../06-agents/35-agent-memory.md)
- [evaluation methods](../../../09-evaluation/45-evaluation-methods.md)
