---
name: mcp-parallel-fetch
description: Use when writing or reviewing a skill that fetches from multiple MCP sources (Notion + Slack + Drive, etc.) to check whether the fetches are sequential when they could be parallel.
disable-model-invocation: false
---

Rewrite sequential MCP fetches as a single parallel fetch step.

## Why

Sequential fetches accumulate latency: three 3-second fetches take 9 seconds. Independent fetches — sources that don't need each other's results to start — take only as long as the slowest one. The rule: reads are parallelisable; actions that depend on analysis are not.

## Steps

### 1 — Identify fetch steps

Read the SKILL.md. List every step that calls an MCP read tool (`notion-query-database-view`, `slack_read_channel`, `search_files`, `read_file_content`, etc.).

Continue when every fetch step is listed.

### 2 — Check for dependencies

For each pair of fetches, ask: does fetch B need fetch A's result to start?
- If no → they are parallelisable
- If yes → they must stay sequential (note why)

Also check: do any action steps (writes, sends) appear before all reads are complete? Flag these as ordering errors.

Continue when every fetch is classified.

### 3 — Rewrite as a parallel step

Merge all parallelisable fetches into one step:

```
## Step N — Fetch (in parallel)

Launch simultaneously:
a) [first MCP read tool + parameters]
   If empty or error → note "[source]: unavailable", continue
b) [second MCP read tool + parameters]
   If empty or error → note "[source]: unavailable", continue
c) [third MCP read tool + parameters]
   If empty or error → note "[source]: unavailable", continue

Continue when all attempts are complete, whether successful or not.
```

Key changes from sequential:
- The word **simultaneously** is the signal to the agent
- Each source has a fallback instruction (note, continue)
- The barrier is "attempts complete", not "responses available"

Continue when the rewritten step is in SKILL.md.

### 4 — Verify action ordering

Confirm that all action steps (writes, sends, creates) appear after the analysis step, which appears after the fetch step. No action should run before all reads are complete.
