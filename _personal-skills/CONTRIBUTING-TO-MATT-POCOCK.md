# Contribution proposée à mattpocock/skills

Issue à soumettre sur https://github.com/mattpocock/skills/issues

---

## Titre suggéré

`[skill idea] mcp-context-patterns — patterns for skills that use MCP tools`

## Corps de l'issue

Hi Matt,

I've been using your framework to build coordination skills for a non-profit (Notion + Slack + Drive via MCP tools). In the process I found three patterns that aren't covered in `writing-great-skills` but feel like natural extensions of it — specifically for skills that fetch context from external tools via MCP.

### Pattern 1 — Reference docs as external reference for MCP IDs

Your framework documents **external reference** for pushing content out of SKILL.md. I found a specific application: a `reference/` directory that acts as the single source of truth for MCP tool IDs (Notion database IDs, Slack channel IDs, Drive folder IDs).

Without this, skills hardcode IDs — a duplication and maintenance problem. With it, each skill reads the reference file and resolves names to IDs at runtime. When an item moves, one file changes.

This is your **single source of truth** principle applied to MCP tool configuration.

### Pattern 2 — Parallel fetch

Skills that fetch from multiple MCP sources often write sequential steps (fetch Notion, then fetch Slack, then fetch Drive). These sources are independent — they can be launched simultaneously.

The signal in SKILL.md is the word **simultaneously**, followed by a barrier: "Continue when all attempts are complete, whether successful or not" (not "when all responses are available" — which blocks on failure).

This maps onto your **completion criterion** concept: the criterion shifts from a positive result to a completed attempt.

### Pattern 3 — Error handling: signal, never invent

When a fetch returns nothing, an agent without explicit fallback instructions may fabricate context — a silent hallucination. The pattern: each fetch has a fallback instruction ("note [source]: unavailable, continue") and the output begins with a Sources section (✅/⚠️ per source).

This is a direct corollary of your "never trust parametric knowledge" principle: if the context wasn't fetched, don't reason on it.

---

I've implemented these as three installable skills at gaspardViel/skills if you want to see them in practice. Happy to write them up in whatever format fits your repo best — standalone skills, an addition to `writing-great-skills`, or a new `mcp-patterns` reference doc.
