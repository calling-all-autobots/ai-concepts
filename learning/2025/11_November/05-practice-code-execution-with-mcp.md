# Code execution with MCP — let agents call tools as code, not tool calls

- **Category:** ② New best practice
- **Date:** 2025-11-04  ·  **What it affects:** MCP-based agents; the pattern of how tool definitions and intermediate results consume context
- **Sources:** https://www.anthropic.com/engineering/code-execution-with-mcp

## In one line
Instead of loading every MCP tool definition into the prompt and piping every intermediate result back through the model, present MCP servers as a code API the agent imports and calls — cutting a worked example from 150,000 tokens to 2,000 (a 98.7% saving).

## What actually changed
Anthropic laid out a pattern that treats MCP servers as **code, not tool schemas**. Two costs it attacks:

1. **Tool-definition bloat** — every connected tool's definition sits in the context window, raising latency and cost on every turn.
2. **Intermediate-result bloat** — data passes *through* the model repeatedly. Their example: a meeting transcript flowing through twice can consume an extra ~50,000 tokens.

The fix: expose each MCP server as files in a filesystem the agent explores (e.g. `./servers/google-drive/`, `./servers/salesforce/`). The agent imports only the definitions it needs and writes code that calls them directly in a code-execution sandbox:

```ts
import * as gdrive from './servers/google-drive'
const transcript = await gdrive.getDocument({ documentId: 'abc123' })
```

Because filtering and transformation happen **in the sandbox**, only the final, relevant result returns to the model — not the raw payload. Net effect in their example: **150,000 → 2,000 tokens, a 98.7% reduction.**

## Why it matters
This reframes MCP from "a menu of tools the model picks from" to "an API surface the model programs against." It attacks the two structural context costs of tool-heavy agents at once — definitions (loaded lazily via imports) and data (kept in the sandbox). It also composes naturally with loops, conditionals, and error handling, which are awkward to express as a sequence of discrete tool calls. This is the conceptual sibling of the Tool Search Tool and Programmatic Tool Calling that shipped three weeks later on Nov 24 — the same "keep tokens out of context" principle, applied to MCP.

## Your point of view
- MCP's real scaling problem isn't the protocol — it's that naive tool exposure floods context. Code-execution is the escape hatch.
- Prefer "let the agent write code that calls tools" over "let the agent emit many tool calls" whenever a task chains several tools or moves large payloads.
- The 98.7% figure is one example, not a guarantee — but the direction (import-on-demand + filter-in-sandbox) is robust.

## What to do
- For agents wired to several MCP servers, evaluate a code-execution surface: expose servers as importable modules and let the agent import only what it needs.
- Do data filtering/aggregation in the sandbox and return only the distilled result to the model.
- Combine with `defer_loading` / Tool Search (Nov 24) so tool definitions are also discovered on demand.

## Connects to
- [MCP](../../../agents/mcp.md)
- [tool calling](../../../agents/tool-calling.md)
- [agentic systems](../../../agents/agentic-systems.md)
