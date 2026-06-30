# Audit technique — 2026-06-30

## État du projet

**Stack**
- HTML statique pur — aucun framework, aucun bundler, aucun build step
- CSS : styles `<style>` inline dans chaque fichier HTML, aucune feuille CSS externe partagée
- JS : scripts inline dans chaque fichier HTML, aucun fichier JS externe
- Hébergement : Vercel — `vercel.json` avec `cleanUrls: true` (URLs sans `.html`)
- Exception : `dashboard.html` charge React 18 + Babel Standalone depuis CDN unpkg — fichier hors scope du site public (outil interne non lié au reste)

**Conventions observées**
- Classes CSS minifiées avec noms courts (`.bp`, `.bs`, `.nc`, `.nl`, `.rv`, `.gr`, etc.) — pas de convention BEM ni utility-first
- Variables CSS `:root` dupliquées dans chaque fichier avec de légères variations (ex : `pack-croissance.html` ajoute `--gold`, `--gold2`, `--gold3`)
- Animations scroll-reveal via classe `.js-ready .rv` + JS inline
- Logo AgenceBoostIA : SVG inline dans le `<nav>` de chaque page B2B
- Pas de versioning d'assets, pas de cache-busting
- `sitemap.xml` incomplet — référence uniquement `/` (homepage), pas les pages packs ni audit-gratuit

---

## Architecture actuelle

```
agenceboostia/
├── index.html                      ← Homepage B2B (page principale)
├── audit-gratuit.html              ← Lead magnet — formulaire audit gratuit
├── pack-etincelle.html             ← Page offre Pack Étincelle 147€
├── pack-decollage.html             ← Page offre Pack Décollage 490€
├── pack-croissance.html            ← Page offre Pack Croissance 699€/mois
├── agenceboostia-candidature.html  ← B2C — produit CV/candidature (ZONE INTERDITE)
├── merci-candidature.html          ← B2C — confirmation post-soumission (ZONE INTERDITE)
├── dashboard.html                  ← Outil interne (React + Babel CDN, titre "SvelteShape")
├── mentions-legales.html           ← Mentions légales (noindex)
├── sitemap.xml                     ← Incomplet (homepage seulement)
├── robots.txt                      ← Standard (Allow: /)
├── og-image.jpg                    ← Image Open Graph partagée
├── vercel.json                     ← cleanUrls: true
└── docs/                           ← Créé lors de cet audit
    └── HANDOFF_CODE_TO_COWORK.md
```

**Sections de la homepage (`index.html`) dans l'ordre :**
1. Announcement bar (bannière gradient top, lien vers `/audit-gratuit`)
2. Nav fixe (logo SVG inline, liens ancres + `/agenceboostia-candidature` + CTA audit)
3. Menu mobile hamburger (`#mm`)
4. Hero (h1, badge, 2 CTAs, 3 cercles pulsants décoratifs)
5. Section banner audit gratuit (`div.agb`) — mise en avant Shopify
6. Toolbar outils IA (`div.tb`)
7. Section chiffres/icônes (`.ss`) — 4 stats emoji
8. Section services (`#sv`) — 6 cards + 1 card SEO/GEO pleine largeur
9. Section promo B2C AgenceBoostIA Candidature (inline, pas dans nav)
10. Tableau comparatif (`#cs`) — AgenceBoostIA vs agence classique
11. Processus (`#ps`) — 4 étapes numérotées
12. Section offres tunnel (`#pr`) — 3 packs en tunnel avec flèches
13. Section offre On-Demand (`.od`) — bloc optionnel sous les packs
14. FAQ accordéon (`#fq`) — 6 questions, Schema.org FAQPage
15. CTA final (`.ca` / `.cbox`)
16. Footer (logo, liens légaux)
17. Bouton WhatsApp flottant (`.wa-btn`, position fixed)

---

## Fichiers clés par zone

### Zone B2B — AgenceBoostIA (agence marketing)
| Fichier | Rôle | Priorité refonte |
|---|---|---|
| `index.html` | Homepage principale — entrée SEO et conversion | Haute |
| `audit-gratuit.html` | Lead magnet principal — formulaire de capture | Haute |
| `pack-etincelle.html` | Page de vente Pack 147€ (one-shot) | Haute |
| `pack-decollage.html` | Page de vente Pack 490€ (one-shot) | Haute |
| `pack-croissance.html` | Page de vente Pack 699€/mois (récurrent) | Haute |
| `mentions-legales.html` | Page légale (noindex) | Basse |
| `sitemap.xml` | À compléter après refonte | Haute |

### Zone B2C — AgenceBoostIA Candidature (ZONE INTERDITE)
| Fichier | Rôle |
|---|---|
| `agenceboostia-candidature.html` | Page produit CV optimisé — 69€ |
| `merci-candidature.html` | Page confirmation post-achat |

### Hors scope
| Fichier | Rôle |
|---|---|
| `dashboard.html` | Outil interne (React, titre "SvelteShape") — non indexé, non lié |

---

## Pages : état actuel

| Page | URL | État | Observations |
|---|---|---|---|
| Homepage | `/` | Fonctionnelle | Dense, CSS ~240 lignes, JS inline, scroll-reveal actif |
| Audit gratuit | `/audit-gratuit` | Fonctionnelle | Design cohérent avec index, nav légèrement différente (sans burger complet) |
| Pack Étincelle | `/pack-etincelle` | Fonctionnelle | Page de vente dédiée, même design system |
| Pack Décollage | `/pack-decollage` | Fonctionnelle | Page de vente dédiée |
| Pack Croissance | `/pack-croissance` | Fonctionnelle | Variables CSS supplémentaires `--gold` pour accent doré, nav avec `top:38px` (announce bar) |
| Candidature | `/agenceboostia-candidature` | Fonctionnelle — NE PAS TOUCHER | Produit B2C séparé |
| Merci candidature | `/merci-candidature` | Fonctionnelle — NE PAS TOUCHER | noindex, page confirmation B2C |
| Dashboard | `/dashboard` | Hors scope — NE PAS TOUCHER | Outil interne React, pas de SEO |
| Mentions légales | `/mentions-legales` | Fonctionnelle | noindex, minimaliste |
| Sitemap | `/sitemap.xml` | Incomplet | Ne liste que la homepage — les pages packs et audit-gratuit manquent |

---

## Contraintes techniques identifiées

1. **Pas de système de templates** — nav, footer, et announcement bar sont copiés-collés dans chaque fichier. Toute modification doit être répercutée manuellement sur 5+ fichiers B2B. Risque élevé de divergence lors de la refonte.

2. **CSS non mutualisé** — chaque page embarque son propre `<style>`. Les variables `:root` sont dupliquées avec de légères variations selon les pages. Une refonte du design system nécessite de modifier chaque fichier indépendamment, à moins d'introduire un fichier CSS partagé.

3. **JS inline** — les animations, le menu mobile et les scripts sont inline dans chaque fichier. Pas de fichier JS externe. Maintenance fragile.

4. **Noms de classes opaques** — les classes courtes (`.bp`, `.bs`, `.rv`, `.gr`, etc.) ne sont pas auto-documentées. Sans source of truth, une refonte par remplacement de classes est risquée.

5. **`sitemap.xml` incomplet** — seule `/` est référencée. Les pages `/audit-gratuit`, `/pack-etincelle`, `/pack-decollage`, `/pack-croissance` sont absentes. Impact SEO réel.

6. **`pack-croissance.html` : nav avec `top:38px`** — différence avec les autres pages qui ont `top:0`. Cela suppose la présence d'une announce bar de 38px de hauteur fixe. Si l'announce bar est retirée ou repositionnée, la nav se retrouve décalée.

7. **Pas de favicon explicite** — aucun `<link rel="icon">` dans les pages (à vérifier côté Vercel ou domaine).

8. **Dépendances externes** — `dashboard.html` charge depuis CDN unpkg (React 18, ReactDOM, Babel). Ce fichier est hors scope de la refonte mais représente un risque si unpkg tombe.

9. **`og-image.jpg` unique** — toutes les pages partagent la même image OG. Pas d'image OG spécifique par offre.

10. **Schema.org partiel** — `index.html` a `ProfessionalService` + `FAQPage`. `agenceboostia-candidature.html` a `Service` + `FAQPage`. Les pages packs ont `Offer` uniquement. Pas de `BreadcrumbList` ni `WebPage`.

---

## Zones interdites (ne pas toucher)

1. **`agenceboostia-candidature.html`** — produit B2C indépendant, logique métier et tarif propres (69€), ne pas modifier
2. **`merci-candidature.html`** — page de confirmation liée au flux B2C candidature, ne pas modifier
3. **`dashboard.html`** — outil interne non documenté, ne pas modifier
4. **La section promo "AgenceBoostIA Candidature" dans `index.html`** (lignes ~343–359) — cross-sell B2C validé, ne pas supprimer ni modifier sans arbitrage stratégique
5. **Logo SVG inline** dans la nav — identité visuelle établie, ne pas modifier la forme ni les proportions
6. **Tarifs affichés** (147€, 490€, 699€/mois, 69€) — ne pas modifier sans validation côté stratégie
7. **Liens vers formulaires ou intégrations de paiement** si présents dans les pages offre — à vérifier avant refonte (non visibles dans les 50 premières lignes, à auditer si Cowork les touche)

---

## Questions ouvertes pour Cowork

1. **Architecture CSS** : introduire un fichier `style.css` partagé entre toutes les pages B2B, ou garder le CSS inline par page ? Un fichier partagé simplifie la maintenance mais change le modèle de déploiement.

2. **Système de templates** : la refonte V2 doit-elle rester en HTML statique pur, ou passer à un générateur de sites statiques (ex: Eleventy, Astro) pour partager nav/footer sans duplication ? Impacte le workflow de déploiement Vercel.

3. **`sitemap.xml`** : qui est responsable de le maintenir à jour ? Il manque actuellement 4 URLs indexables.

4. **Announce bar** : elle est différente entre pages (height 38px sur pack-croissance, absente ou différente sur audit-gratuit). Faut-il l'uniformiser ? Quel message par défaut ?

5. **Page `dashboard.html`** : ce fichier est accessible publiquement sur le domaine (`/dashboard`). Est-ce intentionnel ? Si non, il faudrait soit le protéger (auth) soit le retirer.

6. **Favicon** : aucun favicon détecté dans le code. Est-il servi au niveau Vercel ou DNS ? À vérifier et documenter.

7. **Formulaires de contact / paiement** : les pages packs ont-elles des intégrations actives (Stripe, Typeform, Tally, autre) ? Non visible dans les headers — à auditer sur les 200+ lignes restantes avant toute modification de CTA.

8. **Scope de la refonte V2** : est-ce un reskin visuel (CSS/couleurs/typo) ou une refonte de structure (nouvelles sections, ordre modifié, nouveaux flux) ? La réponse détermine si la refonte peut se faire fichier par fichier ou nécessite une réécriture complète.
