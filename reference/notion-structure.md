# Structure Notion MZD

> Source vérité pour les IDs et URLs des pages et bases de données Notion.
> Citer ce fichier dans les skills. Mettre à jour si une page est déplacée.

---

## Bases de données

### Tâches MZD
- **ID** : `16cfbbdc-800b-4601-89ba-c9625112b49d`
- **Usage** : Toutes les tâches de coordination MZD
- **Statuts clés** : En cours, À débloquer, Terminé
- **Skills qui l'utilisent** : `brief-hebdo`, `brief-hebdo-actif`
- **Requête type** : filter échéance ≤ 7j ou statut = "En cours"

---

## Pages clés

### Todo list programmation
- **URL** : `https://app.notion.com/p/78fe668be5574b86b723dc95fcd60cf9`
- **ID** : `78fe668b-e557-4b86-b723-dc95fcd60cf9`
- **Usage** : Publications Instagram/stories, événements à programmer
- **Skills qui l'utilisent** : `cloture-semaine`, `check-programmation` (à venir)

---

## Comptes-rendus CA

> Les CR CA sont des pages Notion créées après chaque réunion du CA.
> Utiliser `notion-search "CR CA"` pour lister les plus récents.

### Exemple — CR CA du 24/06/2026
- **ID** : `385db23f-3dfb-804b-8d88-d778786eea44`

---

## Pattern — créer un ticket d'alerte

Quand `brief-hebdo-actif` détecte un blocage 🔴, il crée une page dans la base Tâches MZD :

```
Titre : 🔴 Alerte — [nom de la tâche]
Statut : À débloquer
Parent : base Tâches MZD (ID ci-dessus)
```

**Vérifier l'idempotence** avant de créer :
```
notion-search "🔴 Alerte — [nom]"
→ si résultat < 3 jours → ne pas recréer
```

---

## Usage dans les skills

Pour référencer une base ou page dans un SKILL.md :

```
Fetche les tâches ouvertes.
→ base "Tâches MZD", voir reference/notion-structure.md pour l'ID.
```

Ne jamais hardcoder un ID Notion directement dans un SKILL.md.
