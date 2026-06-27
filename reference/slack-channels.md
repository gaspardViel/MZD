# Canaux Slack MZD

> Source vérité pour les IDs de canaux Slack. Citer ce fichier dans les skills
> plutôt que d'hardcoder les IDs. Mettre à jour si un canal est renommé ou créé.

---

## Canaux de coordination (CA / équipe)

### #échanges-ca-équipe
- **ID** : `CJALG7LFM`
- **Type** : Privé (CA + équipe salariée)
- **Usage** : Échanges internes CA, décisions, alertes de coordination
- **Skills qui l'utilisent** : `brief-hebdo-actif`, `cloture-semaine`

### #info-generale
- **ID** : `C02085Z5CHL`
- **Type** : Public (tous les bénévoles)
- **Usage** : Annonces officielles, appels à bénévoles, nouveautés
- **Topic** : Infos générales pour les bénévoles : appels à BN, nouvelles consignes, nouveautés produits, projets, fiches lectures pour librairie, appel à don

---

## Canaux d'information

### #info-en-direct
- **ID** : `C5Q50K893`
- **Type** : Public
- **Usage** : Live chat pour les BN en boutique et au café

### #info-animation
- **ID** : `C01QP0KHLRK`
- **Type** : Public
- **Usage** : Organisation et suivi des ateliers, visites et balades urbaines

### #info-planning-boutique-café
- **ID** : `C075024JKQX`
- **Type** : Public
- **Usage** : Planning boutique et café

---

## Canaux pôles / groupes de travail

### #pôle-communauté
- **ID** : `C0APNRJDV9S`
- **Type** : Public
- **Usage** : Accueil et intégration des bénévoles, organisation des événements de convivialité (apéros, pots)
- **Skills qui l'utilisent** : `fiche-pole`

### #pôle-boutique
- **ID** : `C0APY566U4R`
- **Type** : Public

### #gt-boutique
- **ID** : `C01QJR5BMTR`
- **Type** : Public

### #gt-signa-boutique
- **ID** : `C01RBV2L21F`
- **Type** : Public

### #gt-informatique
- **ID** : `C04C6C7JJ5N`
- **Type** : Public
- **Usage** : Outils informatiques de la MZD

---

## Canaux projets

### #projet-mzd-vivante
- **ID** : `C08CLTC5GHH`
- **Type** : Public

### #offre-entreprise-mzd
- **ID** : `C0822LXBJQZ`
- **Type** : Public

### #cine-mzd
- **ID** : `C0AK2USESN9`
- **Type** : Public

---

## Canaux partage / communauté

### #partage-mzd-a-du-talent
- **ID** : `C021APZELLV`
- **Type** : Public
- **Topic** : Présentons-nous !

### #partage-photo
- **ID** : `C03LB5WKLH4`
- **Type** : Public
- **Usage** : Photos de la MZD, du lieu, d'événements

### #partage-suggestion
- **ID** : `CCH07RSM7`
- **Type** : Public
- **Usage** : Idées boutique / café / programmation / espace ressources

### #club-pilates
- **ID** : `C076SM0DV88`
- **Type** : Public
- **Usage** : Dates des cours de pilates à la MZD

---

## Usage dans les skills

Pour référencer un canal dans un SKILL.md :

```
Envoie le message sur #info-generale.
→ voir reference/slack-channels.md pour l'ID du canal.
```

Ne jamais hardcoder un ID directement dans un SKILL.md.
Si Claude a besoin d'un ID, il le trouve ici.
