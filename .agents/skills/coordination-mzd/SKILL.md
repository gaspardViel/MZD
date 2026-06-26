---
name: coordination-mzd
description: >
  Router pour tous les skills de coordination de la MZD.
  Utilise quand tu ne sais pas quel skill appeler,
  ou pour avoir une vue d'ensemble des outils disponibles.
disable-model-invocation: true
---

# Coordination MZD — carte des skills

Tu veux coordonner le travail de la MZD. Voici quel skill utiliser
selon ta situation.

## Lecture seule — tu veux comprendre l'état de la semaine

→ `/brief-hebdo`

Fetche les tâches Notion + messages Slack et produit un résumé.
Aucune action déclenchée. Idéal le vendredi matin ou avant une réunion.

## Action — tu veux que Claude agisse sur les blocages

→ `/brief-hebdo-actif`

Même fetch que brief-hebdo, mais crée des tickets Notion 🔴 et envoie
des alertes Slack pour chaque blocage détecté. Vérifie l'idempotence
avant d'agir. Idéal le vendredi midi ou en début de semaine.

## Clôture complète de fin de semaine

→ `/cloture-semaine`

Séquence orchestrée : brief actif + todo programmation + message Slack
de clôture posté sur #info-generale. À lancer chaque vendredi vers 17h.

## Programmation — tu veux gérer les événements et la com

→ `/check-programmation` *(à venir)*

Fetche la todo list programmation, identifie les publications en retard
et les événements sans billetterie, et envoie une alerte à l'équipe com.

## Bail — tu veux suivre l'avancement du dossier

→ `/suivi-bail` *(à venir)*

Fetche les CR CA liés au bail et le canal Slack #bail, produit un
état des lieux et identifie la prochaine action requise.

## Tu ne sais pas quel skill utiliser ?

Décris ta situation en une phrase et Claude t'orientera vers le bon skill.
