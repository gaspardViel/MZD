---
name: brief-hebdo-actif
description: >
  Produit le brief hebdomadaire MZD ET déclenche des actions
  (tickets Notion, alertes Slack) sur les blocages détectés.
  Utilise chaque vendredi ou avant toute réunion de coordination.
---

## Contexte à lire avant de commencer

Lis ces trois fichiers pour résoudre les noms en IDs :
- `reference/slack-channels.md` — canaux Slack et leurs IDs
- `reference/notion-structure.md` — bases Notion et leurs IDs
- `reference/drive-structure.md` — dossiers Drive et leurs IDs

## Étape 1 — Fetch (en parallèle)

Lance simultanément :

a) `notion-query-database-view` sur la base "Tâches MZD"
   → ID dans reference/notion-structure.md
   Filtre : échéance dans les 7 prochains jours OU statut "En cours"
   Si 0 résultat ou erreur → noter "Notion : aucune tâche trouvée ou indisponible", continuer

b) `slack_read_channel` sur #échanges-ca-équipe
   → ID dans reference/slack-channels.md
   Pour les 3 derniers jours
   Si 0 message → noter "Slack : canal silencieux depuis 3 jours", continuer
   Si erreur → noter "Slack : source indisponible", continuer

c) Dernier CR CA Drive :
   - `search_files` dans le dossier CA de l'année en cours
     → ID du dossier dans reference/drive-structure.md
   - Trier par modifiedTime desc, prendre le premier résultat avec "CA" dans le titre
   - `read_file_content` sur ce fichier
   Si 0 résultat → noter "Drive : aucun CR CA trouvé dans le dossier", continuer sans c)

Continue quand toutes les tentatives sont terminées, qu'elles aient réussi ou non.

## Étape 2 — Analyser et classer

Pour chaque tâche et chaque décision Slack disponibles, classe dans :

- 🔴 **BLOQUÉE** : tâche "En cours" sans activité depuis plus de 5 jours,
  ou mission identifiée sans responsable assigné
- 🟡 **À SURVEILLER** : tâche proche de l'échéance, responsable présent
  mais pas de mise à jour récente
- 🟢 **EN ORDRE** : avancement visible, responsable clair

Si une source est manquante, ne pas classer d'items pour cette source.
Continue quand chaque item disponible est classé.

## Étape 3 — Vérifier l'idempotence avant d'agir

Avant toute action sur un item 🔴, appelle `notion-search` avec le titre
exact "🔴 Alerte — [nom de l'item]".

- Si un ticket existe créé il y a moins de 3 jours : ne pas recréer ni
  renvoyer de message Slack. Marquer l'item comme "déjà traité".
- Si aucun ticket récent n'existe : passer à l'étape 4.

Continue quand chaque item 🔴 a été vérifié.

## Étape 4 — Agir sur les blocages 🔴

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

## Étape 5 — Produire le brief final

Commence par une section "Sources" :
✅/⚠️ Notion — [N tâches lues] ou [aucune tâche] ou [indisponible]
✅/⚠️ Slack — [N messages / 3 jours] ou [silencieux depuis 3 jours] ou [indisponible]
✅/⚠️ Drive CR CA — [date du CR lu] ou [aucun CR trouvé]

Ensuite les sections habituelles :
- **Priorités** : items 🟡 et 🟢 les plus importants (3 maximum),
  avec responsable et échéance
- **Blocages traités** : actions déclenchées à l'étape 4,
  ou mention "déjà traité" pour les items idempotents
- **À noter** : échanges Slack pertinents
- **Contexte CA** : date + 2 décisions clés du dernier CR CA Drive
  (omettre cette section si Drive est manquant — avec mention explicite)

Le brief est complet quand chaque item disponible est mentionné.
