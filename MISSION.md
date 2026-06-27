# Mission : rendre la MZD lisible et vivante pour ses bénévoles

## Pourquoi

La Maison du Zéro Déchet a une structure réelle — des pôles, des instances de direction,
des canaux d'information, des processus de coordination. Mais cette structure est difficile
à lire de l'extérieur : un nouveau bénévole ne sait pas facilement où sont les informations,
comment s'investir, qui décide quoi, ni quand et où se prennent les décisions.

L'objectif est d'utiliser Claude Code pour produire du contenu qui rende cette structure
**visible, accessible et vivante** — brief hebdomadaire, fiches de process, résumés de CA,
guides d'orientation — en lisant le contexte réel de la MZD depuis Notion, Slack et Drive.

## Le succès ressemble à…

- Les pôles commencent à vivre : les bénévoles savent ce qui se passe dans leur pôle
  et comment contribuer
- Un bénévole qui arrive identifie clairement où sont les informations,
  comment s'investir, et qui contacter
- La structure de gouvernance est lisible : les instances (CA, réunions de pôle,
  journées bénévoles) sont connues et leur rôle est compris
- La charge administrative du CA est allégée : Claude produit les briefs,
  résumés et alertes — le CA se concentre sur les décisions

## Comment

Méthode Matt Pocock appliquée au contexte MZD réel :
**fetch → raisonne → agit**. Claude ne sait rien de la MZD par lui-même —
tout contexte utile est injecté depuis Notion, Slack et Drive avant de raisonner.

Séquence de construction :
1. **Brief hebdomadaire automatique** — posté sur Slack chaque vendredi,
   à destination de toute l'équipe
2. **Fiches de process** — rédigées depuis les docs existants,
   pour rendre les procédures accessibles aux bénévoles
3. **Résumés de CR CA** — synthèses accessibles des comptes-rendus du CA
4. **Contenus de structure** — guides d'orientation, carte des pôles,
   présentation des instances de gouvernance

## Contraintes

- Gaspard est le seul opérateur Claude pour l'instant —
  les bénévoles sont les destinataires des outputs, pas les utilisateurs de l'outil
- Les MCP tools Notion, Google Drive et Slack sont actifs dans cet environnement
- Les skills Matt Pocock sont installés dans `.agents/skills/` — référence vivante
- S'appuyer sur les canaux existants (Slack, Notion, Drive) plutôt qu'en créer de nouveaux

## Hors périmètre (pour l'instant)

- Former les bénévoles à utiliser Claude Code directement
- Développement d'un backend ou d'une API custom
- Intégration avec des outils autre que Notion, Drive, Slack
