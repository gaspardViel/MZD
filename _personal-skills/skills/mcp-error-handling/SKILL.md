---
name: mcp-error-handling
description: Use when writing or reviewing a skill that fetches from MCP tools, to add fallback instructions for empty results and errors. Use when a skill has produced hallucinated output because a source returned nothing.
disable-model-invocation: false
---

Add error handling to every MCP fetch in a skill so the agent signals missing context rather than fabricating it.

## Why

When an MCP fetch returns nothing, an agent without explicit fallback instructions will reason on the void — producing plausible-sounding but fabricated output. This is a silent hallucination: the output looks correct but is based on nothing. The fix is not retrying; it is signalling.

## The rule

**Signal, never invent.** An incomplete brief that names its gaps is more useful than a complete brief built on nothing.

## Steps

### 1 — Identify unguarded fetches

Read the SKILL.md. For each MCP read call, check whether there is an explicit instruction for what to do if the result is empty or errors. A guarded fetch looks like:
```
If empty or error → note "[source]: [status]", continue
```
An unguarded fetch has no such instruction.

List every unguarded fetch.

Continue when every fetch is assessed.

### 2 — Add fallback instructions

For each unguarded fetch, add a fallback. Distinguish two cases:

**Empty result (valid state)**
```
If 0 results → note "[Source]: [description of state]" (e.g. "Slack: channel silent for 3 days")
→ this is information, not an error — include it in the output
```

**Error (tool failure)**
```
If error → note "[Source]: unavailable — data not read"
→ omit the corresponding section from the output with explicit mention
```

Change the fetch barrier from:
> Continue when all responses are available

To:
> Continue when all attempts are complete, whether successful or not

Continue when every fetch has a fallback.

### 3 — Add a Sources section to the output

In the final output step, add a Sources header before the analysis:

```
## Output step

Begin with a Sources section:
✅/⚠️ [Source A] — [N items read] or [status if unavailable]
✅/⚠️ [Source B] — [N items read] or [status if unavailable]

Then the analysis.
Omit any section whose source is marked ⚠️ — with an explicit note.
```

Continue when the Sources section is in the output step.

### 4 — Verify the no-invention rule

Check that no step says "if data is missing, use last known" or "estimate" or "assume". Every gap must be named, never filled.
