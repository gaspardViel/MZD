---
name: cloture-semaine
description: >
  Clôture de semaine MZD complète : brief actif + résumé programmation
  + message récapitulatif posté sur Slack #info-generale.
  À lancer chaque vendredi vers 17h.
---

## Étape 1 — Exécuter le brief hebdomadaire actif

Exécute toutes les étapes de `brief-hebdo-actif` dans l'ordre :

1. Fetch tâches Notion (notion-query-database-view, base "Tâches MZD")
2. Fetch messages Slack #info-generale (C02085Z5CHL, 3 derniers jours)
3. Classifier chaque item : 🔴 bloqué / 🟡 à surveiller / 🟢 en ordre
4. Vérifier l'idempotence (notion-search "🔴 Alerte —") pour chaque item 🔴
5. Créer les tickets Notion 🔴 et envoyer les alertes Slack non idempotentes
6. Produire le brief structuré

Continue quand le brief est produit et toutes les actions de l'étape 5
sont confirmées ou marquées "déjà traité".

## Étape 2 — Fetch la todo liste programmation

Appelle `notion-fetch` sur la page "Todo list programmation".
→ URL dans reference/notion-structure.md

Identifie uniquement :
- Les tâches ouvertes (non cochées) avec une deadline dans les 14 prochains jours
- Les publications Instagram/stories non encore programmées pour la semaine suivante

Continue quand ces éléments sont dans le contexte.

## Étape 3 — Composer le message de clôture

Sur la base du brief (étape 1) et des tâches prog (étape 2),
et uniquement depuis ce contexte fetchté, rédige un message Slack
de clôture de semaine :

```
🗓️ *Clôture de semaine — [date]*

*Priorités semaine prochaine*
• [priorité 1 — responsable]
• [priorité 2 — responsable]
• [priorité 3 — responsable]

🔴 *Blocages traités*
• [item — action déclenchée] ou "Aucun blocage cette semaine"

📢 *Com à programmer*
• [publication ou story à planifier]

Bon week-end à toutes et tous 🌿
```

Message : 15 lignes maximum, ton direct et bienveillant.

## Étape 4 — Envoyer sur Slack

Avant d'envoyer, montre le message à l'utilisateur et attends sa confirmation.

Envoie sur #échanges-ca-équipe (canal CA).
→ ID dans reference/slack-channels.md

Option : proposer à l'utilisateur de créer les tickets Notion 🔴 correspondants
aux blocages traités (appelle notion-create-pages si l'utilisateur répond "oui").

Critère : confirmation d'envoi reçue de l'API Slack.
