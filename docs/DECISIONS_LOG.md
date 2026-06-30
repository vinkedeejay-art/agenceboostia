# Decisions Log — AgenceBoostIA

> Toutes les décisions validées par Kevin, dans l'ordre chronologique.  
> Source unique de vérité pour les agents IA travaillant sur ce projet.  
> **Règle :** ne jamais prendre une décision qui contredit ce fichier sans validation explicite de Kevin.

---

## Décisions Site V2 — 30 juin 2026

| # | Décision | Contexte | Validé par |
|---|---|---|---|
| D-01 | **Vouvoiement partout** sur le site B2B | Le site mixait tutoiement (Pack Étincelle) et vouvoiement. Harmonisation en vouvoiement. Exception autorisée : Instagram et page Candidature (B2C). | Kevin · 30/06/2026 |
| D-02 | **Supprimer "98% satisfaction"** du tableau comparatif | Chiffre sans clients publics référencés. Suppression de la ligne entière plutôt que remplacement. | Kevin · 30/06/2026 |
| D-03 | **Ne pas créer de section Social Proof** pour l'instant | Pas de clients publics à afficher. À réactiver quand 5+ projets livrés documentés. | Kevin · 30/06/2026 |
| D-04 | **Hero H1 → "Transformez votre boutique Shopify avec l'intelligence artificielle"** | Ancrage sur l'ICP e-commerce Shopify, plus précis que "business" générique. | Kevin · 30/06/2026 |

---

## Décisions Produit & Positionnement — juin 2026

| # | Décision | Contexte | Validé par |
|---|---|---|---|
| D-05 | **ICP élargi : toutes niches Shopify françaises** (pas seulement mode) | Pivot 20/06/2026 — adressable x10. Ne plus utiliser "mode françaises" dans les scripts prospection. | Kevin · 20/06/2026 |
| D-06 | **Nom officiel : AgenceBoostIA** (jamais "BoostIA" seul) | "BoostIA" seul déjà utilisé par d'autres marques. | Kevin · juin 2026 |
| D-07 | **Séparation stricte B2B / B2C** | Formspree `xpwzgvbq` = B2B · Tally `KYOArK` = Candidature B2C. Ne jamais mélanger. | Kevin · 25/06/2026 |
| D-08 | **Candidature CV = branche B2C indépendante** à 69€ | Page `/agenceboostia-candidature` · onglet "Candidature CV" dans nav · Ne pas mélanger avec offres B2B | Kevin · 25/06/2026 |

---

## Décisions Design & Identité Visuelle

| # | Décision | Contexte | Validé par |
|---|---|---|---|
| D-09 | **Palette principale violet** : `#0A0A0F` / `#6C63FF` / `#8B85FF` / `#A78BFA` | Palette "Signal Lumière" — immuable sur le site et les livrables premium | Kevin · juin 2026 |
| D-10 | **Palette secondaire cyan** en rotation Instagram uniquement | `#00C8FF` en alternance — max 1 post cyan pour 2 posts violet. Jamais sur le site. | Kevin · 26/06/2026 |
| D-11 | **Logo officiel SVG** : sphère de nœuds interconnectés + barres croissantes + flèche montante, néon violet | Description complète dans `memory/logo-officiel.md`. Ne jamais remplacer par une version approximative. | Kevin · juin 2026 |
| D-12 | **WhatsApp button = couleur `var(--primary)`** (violet) | Pas vert — cohérence charte. | Kevin · juin 2026 |

---

## Décisions Infrastructure

| # | Décision | Contexte | Validé par |
|---|---|---|---|
| D-13 | **Command Center = projet Vercel séparé** d'agenceboostia.fr | URL : agenceboostia-command-center.vercel.app · Repo distinct | Kevin · juin 2026 |
| D-14 | **Roadmap Command Center V0.4 : ordre strict** V0.4.1 → V0.4.2 → V0.4.3 | Protection serveur AVANT clé API Claude. Non négociable. | Kevin · 26/06/2026 |
| D-15 | **Svelte Shape = labo interne BoostIA** (@svelte_shape / getsvelteshape.fr) | Ne jamais prospecter cette marque. Peut être utilisé comme référence projet avec accord. | Kevin · juin 2026 |

---

## Règles permanentes (non négociables sur tous les livrables)

- Ne jamais inventer chiffres, témoignages, résultats clients ou expériences
- Ne jamais remplacer le logo officiel par une version approximative
- Ne jamais mélanger B2B (Formspree) et Candidature B2C (Tally)
- Ne jamais modifier l'offre, le prix ou la promesse Candidature sans validation
- Ne pas déployer en production sans Preview Vercel validée
- Aucune action directe (email, DM, publication) sans signal écrit de Kevin ("VALIDÉ" ou "ENVOIE")

---

---

## Décisions Site V3 Premium — 30 juin 2026

| # | Décision | Contexte | Validé par |
|---|---|---|---|
| D-16 | **Refonte V3 Premium — dark abandonné** | Nouveau chantier. Palette dark (`#0A0A0F` / violet) remplacée par light premium. | Kevin · 30/06/2026 |
| D-17 | **V3 = light premium** : fond blanc/crème + accents | Direction visuelle. Palette complète à définir en Phase Cowork V3. | Kevin · 30/06/2026 |
| D-18 | **Contenu V2 conservé** : wording, structure, ordre des sections | V3 ne change que le visuel (CSS/design). Les textes et la logique de conversion V2 restent. | Kevin · 30/06/2026 |
| D-19 | **Périmètre V3 : à définir au fil des phases** | Commence par `index.html`, décision page par page ensuite. | Kevin · 30/06/2026 |

---

*Fichier maintenu par les agents Claude Code & Claude Cowork*  
*Dernière mise à jour : 30 juin 2026*
