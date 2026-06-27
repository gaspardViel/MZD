# Gouvernance partager

**Leçon 15** — Skill `gouvernance-partager` : fetcher la structure de gouvernance MZD depuis Notion et produire un document de référence partageable pour les bénévoles.

## Insights clés

**Données stables vs dynamiques.** La gouvernance (instances, rôles, composition du CA) change rarement — c'est fondamentalement différent des tâches hebdomadaires. Ce n'est pas le même skill, ce n'est pas le même pattern, ce n'est pas la même fréquence. Confondre les deux produit soit un document obsolète (si on le rafraîchit trop peu), soit du bruit superflu (si on le génère chaque semaine).

**Pattern orient vs pattern triage.** `brief-hebdo-actif` : fetch → classer → alerter (éphémère). `gouvernance-partager` : fetch → synthétiser → publier (durable). La différence est dans la durée de vie de l'output — pas dans la technique. Le pattern influe sur le critère de complétion et sur ce qu'on inclut ou exclut.

**Critère de complétion étendu pour les documents stables.** Un document de référence est "complet" quand il contient sa date de génération et ses sources Notion. Le lecteur doit pouvoir évaluer la fraîcheur lui-même. La date n'est pas cosmétique — c'est la signature de fiabilité du document.

**Séparation stricte structure / opérationnel.** `gouvernance-partager` décrit la structure (instances, rôles, périmètres). `brief-hebdo-actif` décrit le contexte opérationnel (tâches, blocages, alertes). Aucun chevauchement. Si les deux sources s'y mettent, le résumé de gouvernance devient obsolète en quelques jours.

**Timing conditionné à Notion, pas au monde réel.** Lancer `gouvernance-partager` avant que Notion soit mis à jour produit un document incorrect. La règle : le skill reflète Notion au moment de son exécution — pas le vote de l'AG, pas la décision orale. Attendre que la source soit à jour avant de lancer le skill.

## Implications

Ce skill est l'entrée de la séquence "contenus de structure" de la mission. L'étape suivante naturelle : créer un `resume-cr-ca` — skill qui fetche les comptes-rendus de CA depuis Notion et produit des synthèses accessibles pour les bénévoles.
