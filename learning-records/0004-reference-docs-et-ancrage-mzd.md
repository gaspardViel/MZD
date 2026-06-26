# Reference docs et ancrage MZD

L'apprenant a compris le problème des IDs hardcodés dans les SKILL.md (connaissance figée sur l'infrastructure, fragile au moindre changement Slack/Notion), et la solution : des reference docs dans `reference/` qui centralisent les IDs et descriptions. Pattern retenu : "document once, cite everywhere" — les skills citent le nom humain du canal/de la base + une note pointant vers le fichier de référence. Claude lit ces fichiers à chaque exécution (contexte injecté, pas mémoire persistante).

**Ce qui a été créé** : `reference/slack-channels.md` (15 canaux réels fetchés depuis l'API Slack) et `reference/notion-structure.md` (base Tâches MZD + Todo list programmation). Tous les skills existants mis à jour pour citer les reference docs.

**Implications** : Leçon 6 peut aborder l'autonomie planifiée — déclencher les skills automatiquement (cron vendredi 17h) via les outils de scheduling Claude Code.
