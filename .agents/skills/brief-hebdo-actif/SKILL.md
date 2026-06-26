---
name: brief-hebdo-actif
description: >
  Produit le brief hebdomadaire MZD ET déclenche des actions
  (tickets Notion, alertes Slack) sur les blocages détectés.
  Utilise chaque vendredi ou avant toute réunion de coordination.
---

## Contexte à lire avant de commencer

Lis ces deux fichiers pour résoudre les noms en IDs :
- `reference/slack-channels.md` — canaux Slack et leurs IDs
- `reference/notion-structure.md` — bases Notion et leurs IDs

## Étape 1 — Fetch les tâches Notion

Appelle `notion-query-database-view` sur la base "Tâches MZD".
Filtre : échéance dans les 7 prochains jours OU statut "En cours".
Continue quand chaque tâche (statut, assigné, date, dernière modification)
est dans le contexte.

## Étape 2 — Fetch les messages Slack

Appelle `slack_read_channel` sur #échanges-ca-équipe.
→ ID dans reference/slack-channels.md
Pour les 3 derniers jours.
Identifie : décisions prises, missions sans responsable, blocages exprimés.
Continue quand les fils pertinents sont dans le contexte.

## Étape 3 — Analyser et classer

Pour chaque tâche et chaque décision Slack, classe-la dans une des trois
catégories (uniquement depuis le contexte fetchté — ne pas inventer) :

- 🔴 **BLOQUÉE** : tâche "En cours" sans activité depuis plus de 5 jours,
  ou mission identifiée sans responsable assigné
- 🟡 **À SURVEILLER** : tâche proche de l'échéance, responsable présent
  mais pas de mise à jour récente
- 🟢 **EN ORDRE** : avancement visible, responsable clair

Continue quand chaque item du contexte est classé.

## Étape 4 — Vérifier l'idempotence avant d'agir

Avant toute action sur un item 🔴, appelle `notion-search` avec le titre
exact "🔴 Alerte — [nom de l'item]".

- Si un ticket existe créé il y a moins de 3 jours : ne pas recréer ni
  renvoyer de message Slack. Marquer l'item comme "déjà traité" pour le
  rapport.
- Si aucun ticket récent n'existe : passer à l'étape 5.

Continue quand chaque item 🔴 a été vérifié.

## Étape 5 — Agir sur les blocages 🔴

Pour chaque item 🔴 non déjà traité :

a) Appelle `notion-create-pages` dans la base "Tâches MZD" :
   - Titre : "🔴 Alerte — [nom de l'item bloqué]"
   - Statut : "À débloquer"
   - Description : contexte du blocage et action attendue

b) Appelle `slack_send_message` sur #échanges-ca-équipe
   (→ ID dans reference/slack-channels.md) :
   - 3 lignes maximum
   - Format : "🔴 *[Nom du blocage]* — [responsable] · Action attendue : [quoi] · [lien Notion]"

Critère : chaque item 🔴 non déjà traité a un ticket Notion ET
un message Slack confirmés avant de passer à l'étape suivante.

## Étape 6 — Produire le brief final

Rédige le brief structuré (uniquement depuis le contexte fetchté) :

- **Priorités** : items 🟡 et 🟢 les plus importants (3 maximum),
  avec responsable et échéance
- **Blocages traités** : liste des actions déclenchées à l'étape 5,
  ou mention "déjà traité" pour les items idempotents
- **À noter** : informations pertinentes des échanges Slack

Le brief est complet quand chaque item classé est mentionné et quand
toutes les actions de l'étape 5 sont confirmées ou marquées "déjà traité".
