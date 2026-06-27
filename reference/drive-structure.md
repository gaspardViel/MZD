# Structure Google Drive MZD

> Source vérité pour les IDs de dossiers et fichiers Drive MZD.
> Citer ce fichier dans les skills. Mettre à jour si un dossier est déplacé ou renommé.
> Pour trouver un fichier, utiliser `search_files` avec le titre — ne jamais deviner un ID.

---

## Dossiers CA (Comptes-rendus du Conseil d'Administration)

> Les CR CA sont des Google Docs, organisés par année.
> Nomenclature : `YYYY_MM_DD CA` (ex. `2026_04_01 CA`)

### Dossier racine — CA Bande de Sauvages
- **ID** : `0B7GjLmI_o-M-aU80dTk5bWdzOHM`
- **Type** : Dossier racine CA (contient un sous-dossier par année)
- **Owner** : `bandedesauvages.interne@gmail.com`

### Sous-dossiers par année
| Année | ID du dossier |
|-------|---------------|
| 2026  | `1flx8G4bDXDz-PpEu47RulpZwN_XUTdqq` |
| 2025  | `1BYIZfmSNz-FZwmdh2RfggnFOuf28tEpM` |
| 2024  | `1BSeA2bv028aIeFMfaZq8u0w09Cbfsc5G` |

### Exemples — CR CA récents (2026)
- `2026_04_01 CA` — ID : `1jWRpk1C0AUJbGi5i6SVCJr5_D5HFq36idsFz9Ur935w`
- `2026_01_29 CA` — ID : `1doX2bdfWgP40JeFipVTkiZtHDFgn23NJ8Ii3utVVhZU`

### Pattern — chercher les CR CA dans un skill
```
Pour lister les CR CA de l'année en cours :
→ search_files(query: "parentId = '1flx8G4bDXDz-PpEu47RulpZwN_XUTdqq'")
→ trier par modifiedTime desc pour avoir le plus récent

Pour lire un CR CA spécifique :
→ get_file_metadata(fileId) pour vérifier
→ read_file_content(fileId) pour le contenu
```

---

## Gouvernance Partagée

### Dossier racine — Gouvernance Partagée
- **ID** : `1K5TwrjMjxyLKFHGhqjSTtmjSHqDujfsA`
- **Owner** : `maisonduzd@gmail.com`
- **Usage** : Documents de gouvernance des pôles MZD

### Documents clés
- **Cadrage gouvernance des pôles** (Google Doc)
  - ID : `1eH27Nb-g_lF7NmiJxQdWrUfcowbjyXaBtssG3-GTnM0`
  - Usage : référence sur la gouvernance partagée, rôles des pôles
- **Tableaux Gouvernance** (Google Sheets)
  - ID : `1v-cIN-4L5rfqc4OfBhLegY7HtmDVF9O75_APrjml2tY`
  - Usage : suivi structuré des instances de gouvernance

### Sous-dossiers
- `Journées Gouvernance Partagée` — `1jnbNcZvEo8CrROYjqYYt0q-TPIcz8opO`
- `Ressources Gouvernance Partagée` — `1PRb48jf8t-hTu1hYSPlHSpXanRSYWWyb`

---

## Bénévoles

### Créneaux bénévoles partagé [MZD]
- **ID** : `1KJQxsp_G31Hn7WeRnXbykR5-ZUVzoge6l5kkYNgKH-Y`
- **Type** : Google Sheets
- **Owner** : `infocniid@gmail.com`
- **Usage** : Planning des créneaux bénévoles (boutique, café, etc.)
- **Dernière modification** : 2026-06-26 (actif)

---

## Documents ponctuels partagés

### Candidatures CA 2026
- **ID** : `1tL9jcYPwXX3YBkJwkQEEE80XHaTies20QizUKulaz20`
- **Type** : Google Slides
- **Owner** : `maisonduzd@gmail.com`

---

## Pattern — rechercher dans Drive depuis un skill

```
## Étape 1 — Chercher par titre (quand l'ID est inconnu)
search_files(query: "title contains 'nom du document'")

## Étape 2 — Chercher dans un dossier spécifique
search_files(query: "parentId = 'ID_DU_DOSSIER'")

## Étape 3 — Lire le contenu
read_file_content(fileId: "ID_DU_FICHIER")
```

**Règle** : Ne jamais hardcoder un ID Drive directement dans un SKILL.md.
Les IDs changent si un fichier est déplacé. Le skill doit d'abord `search_files`,
puis lire le fichier trouvé — sauf pour les documents ancrés dans ce fichier de référence.

---

## Relation Drive / Notion

| Besoin | Outil recommandé |
|--------|-----------------|
| Tâches structurées, statuts, filtres | Notion (bases de données) |
| Documents longs, CR CA, présentations | Drive |
| CR CA récents (2026+) | **Notion** — voir `notion-structure.md` |
| CR CA anciens (≤ 2025) | **Drive** — voir dossiers CA ci-dessus |
| Créneaux bénévoles | Drive (Google Sheets) |
| Todo programmation | Notion — voir `notion-structure.md` |
