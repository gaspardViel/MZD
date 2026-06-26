# Autonomie planifiée et crons

L'apprenant a compris le pattern CronCreate pour déclencher des skills automatiquement (syntaxe cron 5 champs, heure locale, durable vs in-memory, 7-day expiry). Distinction critique retenue : automatiser les opérations (fetch, analyse, composition), garder la main humaine sur les décisions (envoi, création). Le pattern "brouillon d'abord" (slack_send_message_draft) résout le cas cloture-semaine en cron sans perdre la validation humaine. Prompt de cron robuste = contexte temporel + chemin SKILL.md + reference docs à lire.

**Implications** : Leçon 7 peut aborder Google Drive — compléter les reference docs avec la structure Drive (dossiers CA, programmation, documents partagés) et créer un premier skill de recherche Drive.
