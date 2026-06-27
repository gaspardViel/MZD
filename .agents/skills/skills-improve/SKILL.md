---
name: skills-improve
description: >
  Audit and sharpen a skill — diagnose failure modes,
  strengthen completion criteria and leading words,
  correct information hierarchy violations.
  Use when asked to improve, audit, or refactor a specific skill.
---

Prend en paramètre le nom du skill à améliorer (ex : `brief-hebdo-actif`).

## Étape 1 — Lire

Lis `SKILL.md` et tous les fichiers disclosed du skill cible (sibling `.md` dans le même dossier).

Lis `.agents/skills/writing-great-skills/SKILL.md` comme référence canonique.

Si un Lessons Context est déjà en contexte (chargé par `fetch-technical-lessons` ou `skills-improve-base`), utilise-le ; sinon, lis `.agents/skills/writing-great-skills/GLOSSARY.md`.

Continue quand tous les fichiers du skill cible et la référence canonique sont en contexte.

## Étape 2 — Audit

Passe chaque ligne du skill en revue contre les cinq modes d'échec :

- **Sédiment** : ligne qui n'est plus justifiable par le comportement actuel du skill.
- **Sprawl** : responsabilité hors du scope — test : peut-on décrire le skill en une phrase sans "ET aussi" ?
- **Complétion prématurée** : étape sans "Continue quand…" vérifiable et exhaustif.
- **No-op** : instruction que le modèle respecterait par défaut — test : sa suppression change-t-elle le comportement ?
- **Duplication** : même sens exprimé à deux endroits.

Audite ensuite la description (si model-invoked) :
- Leading word en tête de description ?
- Chaque branche est-elle distincte (pas de synonymes qui nomment la même branche) ?

Audite l'information hierarchy :
- Les étapes sont-elles en tête du fichier, la référence derrière des pointers ?
- Les fichiers disclosed sont-ils justifiés par des branches ?

Continue quand chaque section est auditée et chaque finding noté avec son mode d'échec.

## Étape 3 — Sharpen

Pour chaque finding :

- **Sédiment / no-op / duplication** → supprime.
- **Complétion prématurée** → ajoute un critère "Continue quand…" vérifiable et exhaustif.
- **Sprawl** → déplace hors du skill si une branche ne concerne pas tous les runs.
- **Leading word manqué** (prose qui approxime un concept pretraîné) → identifie le mot pretraîné le plus précis, remplace la prose.
- **Description mal ordonnée** → front-load le leading word principal.

Écris le ou les fichiers améliorés.

Continue quand chaque finding est résolu — corrigé, supprimé, ou conservé avec raison explicite.

## Étape 4 — Rapport

```
## [skill-name] — amélioration

Modes d'échec corrigés : [liste avec finding compact]
Leading words ajoutés/sharpened : [liste]
Critères de complétion ajoutés : [liste]
Conservé intentionnellement : [liste avec raison]
```

Si aucun finding : `[skill-name] — inchangé, aucun mode d'échec détecté.`
