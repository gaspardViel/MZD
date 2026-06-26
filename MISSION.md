# Mission : Claude Code comme coordinateur de la MZD

## Pourquoi

La Maison du Zéro Déchet (MZD) coordonne son travail à travers Notion, Google Drive et Slack.
L'objectif est de maîtriser Claude Code pour qu'il agisse comme un coordinateur intelligent : lire l'état réel de l'organisation dans ces outils, raisonner dessus, et déclencher des actions — en appliquant la logique d'ingénierie des skills de Matt Pocock, qui dit que les LLMs ne savent rien de nos données internes et que tout contexte utile doit être **injecté** depuis les vrais outils.

## Le succès ressemble à…

- Écrire un skill Claude Code qui lit les tâches Notion de la MZD, analyse les messages Slack de la semaine, et produit un brief de coordination actionnable
- Savoir quand un LLM peut raisonner depuis son savoir paramétrique vs quand il faut impérativement fetcher le contexte depuis Notion/Slack/Drive avant de lui poser une question
- Composer des skills MZD robustes : chaque skill commence par "fetch context", puis raisonne, puis agit
- Avoir confiance pour déboguer quand Claude hallucine (parce qu'il a raisonné sans contexte)

## Contraintes

- Les MCP tools Notion, Google Drive, et Slack sont déjà actifs dans cet environnement
- Les skills Matt Pocock sont installés dans `.agents/skills/` — ils sont la référence vivante
- Priorité sur des skills utilisables immédiatement par l'équipe MZD, pas sur la théorie LLM abstraite

## Hors périmètre (pour l'instant)

- Développement d'un backend ou d'une API custom
- Formation de l'équipe MZD à Python ou à l'ingénierie LLM en profondeur
- Intégration avec des outils autre que Notion, Drive, Slack
