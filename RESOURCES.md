# Ressources

Sources classées par confiance et pertinence pour la mission.

---

## Tier 1 — Sources primaires (dans ce repo)

- **`.agents/skills/writing-great-skills/SKILL.md`** — La définition de référence des principes d'ingénierie des skills chez Matt Pocock : _context load_, _leading words_, _completion criterion_, _duplication_. À lire avant d'écrire le moindre skill.
- **`.agents/skills/teach/SKILL.md`** — Le skill utilisé pour cette session : illustre comment un skill bien écrit structure l'état et le comportement de l'agent.
- **`skills-lock.json`** — Inventaire des 35 skills installés : carte de ce qui existe déjà.

## Tier 1 — Documentation officielle (web)

- **Claude Code documentation** — https://code.claude.com/docs — Architecture MCP, hooks, settings.json, slash commands. Source de vérité pour tout ce que Claude Code peut faire.
- **Model Context Protocol (MCP) spec** — https://modelcontextprotocol.io — Protocole qui permet aux skills de parler à Notion, Slack, Drive. Comprendre MCP = comprendre pourquoi le "fetch-first" fonctionne.

## Tier 2 — Références vivantes (outils actifs)

- **MCP Notion** (`mcp__Notion__*`) — Les tools actifs dans cette session : `notion-fetch`, `notion-search`, `notion-query-database-view`, etc. Voir la liste complète dans le system prompt.
- **MCP Slack** (`mcp__Slack__*`) — `slack_read_channel`, `slack_search_public_and_private`, `slack_read_thread`, etc.
- **MCP Google Drive** (`mcp__Google_Drive__*`) — `read_file_content`, `search_files`, `list_recent_files`, etc.

## Tier 3 — Contexte MZD (à construire)

- Structure de l'espace Notion MZD (à documenter dans `reference/notion-structure.html`)
- Canaux Slack utilisés par la MZD (à documenter dans `reference/slack-channels.html`)
- Dossiers Drive clés de la MZD (à documenter dans `reference/drive-structure.html`)
