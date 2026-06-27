---
name: fiche-pole
description: >
  Compose a readable pôle fact sheet for MZD volunteers — search the
  pôle's Notion page, fetch its Slack activity, format for non-technical
  audiences. Use when onboarding a volunteer or answering
  "what does pôle X do?"
---

## Contexte à lire avant de commencer

- `reference/slack-channels.md` — canaux Slack des pôles (IDs)

## Étape 0 — Identifier le pôle

Le pôle est nommé dans la demande.
Identifier son canal Slack dans reference/slack-channels.md.
Si aucun canal correspondant → noter "Slack : aucun canal trouvé pour ce pôle", continuer.

## Étape 1 — Fetch (en parallèle)

a) `notion-search` avec le nom du pôle
   → Prendre la page dont le titre correspond le mieux
   Si aucun résultat → noter "Notion : page pôle introuvable", continuer

b) `slack_read_channel` sur le canal du pôle
   → ID dans reference/slack-channels.md
   Pour les 14 derniers jours
   Si silencieux → noter "canal silencieux depuis 14 jours", continuer
   Si erreur → noter "Slack : indisponible", continuer

Continue quand toutes les tentatives sont terminées, qu'elles aient réussi ou non.

## Étape 2 — Composer la fiche

Format accessible — destinataire = bénévole qui découvre la MZD,
aucune connaissance des outils internes.

**[Nom du pôle]**
_[Mission en une phrase — ce que fait le pôle concrètement pour la MZD]_

**Ce qu'on fait**
[2-3 activités concrètes — sans jargon, sans noms d'outils]

**Comment s'investir**
[Action concrète : "rejoins l'espace de discussion #..." ou "contacte [prénom]"]

**Ce qui se passe en ce moment**
[Résumé de l'activité des 14 derniers jours — sans IDs ni références techniques
 Si silencieux → "Le pôle est peu actif en ce moment."]

**Pour aller plus loin**
[Où trouver les infos — canal + documentation — présentés sans nommer les outils]

Règle : aucun acronyme non défini, aucune mention de Notion/Slack comme "outils",
aucun ID visible. Notion = "la documentation", Slack = "l'espace de discussion".

Continue quand la fiche est complète et lisible sans connaissance interne.
