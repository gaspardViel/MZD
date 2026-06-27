---
name: mcp-reference-docs
description: Use when setting up a new project that uses MCP tools (Notion, Slack, Drive, etc.) and you need to create reference docs for tool IDs, or when a skill hardcodes an ID that should be centralised.
disable-model-invocation: false
---

Create or update a `reference/` directory that acts as the single source of truth for all MCP tool IDs used in this project's skills.

## Why

MCP tools rely on IDs (database IDs, channel IDs, folder IDs) that change when items are moved or renamed. Hardcoding these IDs in SKILL.md files creates duplication and makes maintenance fragile. A `reference/` file centralises each ID in one place — skills point to it, never past it.

## Steps

### 1 — Audit the project

Read every SKILL.md in `.agents/skills/`. List every hardcoded ID or tool-specific identifier (Notion database IDs, Slack channel IDs, Drive folder IDs, API endpoints).

Continue when every hardcoded ID is listed.

### 2 — Group by tool

Create one reference file per tool:
- `reference/notion-structure.md` — Notion database IDs, page IDs, query patterns
- `reference/slack-channels.md` — Slack channel names and IDs
- `reference/drive-structure.md` — Drive folder IDs, key file IDs, naming conventions

For each file, use this structure:
```
# [Tool] Structure — [Project Name]

> Single source of truth for [tool] IDs.
> Cite this file in skills. Update if an item is moved or renamed.

## [Section]
- **ID**: `the-id`
- **Usage**: what this is used for
- **Skills that use it**: `skill-name`

## Pattern — using this file in a skill
[code example showing how to reference the file, not the ID]
```

Continue when each file is written.

### 3 — Update skills to use the reference files

For each skill that had hardcoded IDs:
- Add the relevant reference file(s) to the "Context to read first" section
- Replace hardcoded IDs with prose instructions: "→ ID in reference/notion-structure.md"

Continue when no SKILL.md contains a hardcoded MCP tool ID.

### 4 — Document the update pattern

Add to each reference file:
```
## Maintenance
When an item is moved or renamed in [tool], update the ID here.
All skills that reference this file will pick up the change automatically.
```
