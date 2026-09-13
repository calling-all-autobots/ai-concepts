# Code execution tool gains REPL state persistence

- **Category:** ① Product release
- **Date:** 2026-06-18  ·  **What it affects:** code execution tool `code_execution_20260120` (Messages API + all SDKs)
- **Sources:** https://platform.claude.com/docs/en/release-notes/overview

## In one line
The code execution tool now keeps REPL state alive across cells within a session — variables, imports and data survive from one code block to the next — via the `code_execution_20260120` version, with no beta header required.

## What actually changed
- New tool version **`code_execution_20260120`** adds **REPL state persistence**: set the tool's `type` to `code_execution_20260120` and **no beta header** is needed.
- It is the **minimum version required for programmatic tool calling** (where the model writes code that calls your tools rather than emitting many separate tool-use blocks).
- **Available on:** Claude Fable 5, Claude Mythos 5, Claude Opus 4.5 and newer, Claude Sonnet 4.5 and newer.
- **SDK support:** Python, TypeScript, Go, Java, Ruby, PHP, and C#.
- A **90-second per-cell execution limit** was disclosed as part of the same update.

## Why it matters
Without persistence, every code step is a cold start: the model has to re-import libraries, re-load data, and re-derive intermediate results each cell, burning tokens and latency. Persistent REPL state makes multi-step data work behave like a real notebook — load a dataframe once, then keep querying it — which is exactly what analytical and agentic code workflows need. Making it the floor for programmatic tool calling matters because that pattern (code that orchestrates tools) is how you cut the token cost of chatty many-tool agents; REPL persistence lets that generated code accumulate state instead of rebuilding it.

## Your point of view
- "REPL persistence turns code execution from a stateless calculator into a stateful notebook — big win for multi-step analysis and agent efficiency."
- "It's also a prerequisite: if you want programmatic tool calling, you must be on `code_execution_20260120`."
- "Mind the 90-second-per-cell limit — long jobs must be chunked across cells, which is fine now that state carries over."

## What to do
1. Upgrade the tool `type` to `code_execution_20260120` (drop any old beta header) and update SDKs.
2. Rewrite multi-step code workflows to load data/imports once and reuse them across cells instead of per-call.
3. Split any step that could exceed 90 seconds into smaller cells.

## Connects to
- [tool calling](../../../agents/tool-calling.md)
- [agentic systems](../../../agents/agentic-systems.md)
- [SDK](../../../dev-surfaces/sdk.md)
- [inference optimization](../../../production-ops/inference-optimization.md)
