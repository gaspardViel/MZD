---
name: skills-improve-base
description: >
  Pass d'amélioration sur l'ensemble du corpus skills —
  charge le Lessons Context, puis invoque skills-improve
  sur chaque skill dans .agents/skills/.
  Améliore structure et optimisations de tous les skills.
disable-model-invocation: true
---

## Étape 1 — Charger le Lessons Context

Invoque `fetch-technical-lessons`.

Continue quand le Lessons Context est en contexte.

## Étape 2 — Construire la queue

Liste tous les répertoires dans `.agents/skills/` qui contiennent un `SKILL.md`.

Exclure `writing-great-skills` — c'est la référence canonique, pas une cible d'amélioration.

Continue quand la queue est complète et visible.

## Étape 3 — Améliorer chaque skill

Pour chaque skill dans la queue, invoque `skills-improve` sur ce skill.

Trace le résultat immédiatement : `✅ amélioré` / `✔ inchangé` / `⚠️ erreur [raison]`.

Continue quand chaque skill de la queue est traité.

## Étape 4 — Rapport de pass

```
## Pass d'amélioration — [N skills traités]

✅ Améliorés : [liste avec finding principal]
✔ Inchangés : [liste]
⚠️ Erreurs : [liste avec raison]

Patterns les plus fréquents : [top 3 modes d'échec rencontrés]
Leading words ajoutés : [liste consolidée]
```

Critère : chaque skill de la queue apparaît dans le rapport ; aucun skill non traité.
