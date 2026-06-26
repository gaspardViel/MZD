---
name: brief-hebdo
description: >
  Produit le brief de coordination hebdomadaire de la MZD.
  Utilise quand l'équipe veut un résumé actionnable des tâches
  Notion et des échanges Slack de la semaine.
---

## Contexte à lire avant de commencer

- `reference/slack-channels.md` — IDs des canaux Slack
- `reference/notion-structure.md` — IDs des bases Notion

## Étape 1 — Fetch les tâches Notion de la semaine

Appelle `notion-query-database-view` sur la base de données "Tâches MZD".
→ ID dans reference/notion-structure.md
Filtre par : date d'échéance dans les 7 prochains jours,
ou statut "En cours". Continue quand chaque tâche avec son statut,
son assigné et sa date est dans le contexte.

## Étape 2 — Fetch les messages Slack récents

Appelle `slack_read_channel` sur #échanges-ca-équipe.
→ ID dans reference/slack-channels.md
Pour les 3 derniers jours. Continue quand les fils importants
(décisions, blocages, demandes) sont identifiés dans le contexte.

## Étape 3 — Synthétiser le brief

Sur la base du contexte fetchté (uniquement ce contexte — ne pas
inventer de tâches ou de décisions), rédige un brief structuré :

- **Cette semaine** : 3 priorités maximum, avec la personne responsable
- **Blocages** : ce qui nécessite une décision ou une aide
- **À noter** : informations pertinentes des échanges Slack

Le brief doit être lisible en moins de 2 minutes.

## Critère de complétion

Le brief est complet quand chaque tâche "En cours" ou à échéance
cette semaine est mentionnée, et quand les blocages sont explicites.
