---
name: fetch-technical-lessons
description: >
  Distil all learning-records into a structured Lessons Context —
  use before a skill audit pass or to review accumulated technical insights.
---

Lis chaque fichier dans `learning-records/` par ordre croissant (0001 → dernier).

Pour chaque fichier, extrais : titre, insight clé (première phrase), leading words (termes en gras), implications.

Continue quand chaque fichier est lu.

Distille un **Lessons Context** structuré en quatre sections :

**Modes d'échec** — pour chaque pathologie documentée : nom, test diagnostique, remède.

**Steering** — leading words identifiés dans le corpus ; formules de critères de complétion ("Continue quand…") ; signaux de legwork.

**Patterns structurels** — fetch parallèle, gestion d'erreurs (section Sources), pattern router, reference docs, règles d'information hierarchy.

**Invocation** — règles model-invoked vs user-invoked ; arbitrage context load / cognitive load ; règle side-effects.

Critère : chaque fichier dans `learning-records/` est représenté dans le Lessons Context.
