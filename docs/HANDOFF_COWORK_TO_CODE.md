# Recommandations stratégiques — 30 juin 2026

> **Auteur :** Claude Cowork — Phase 2 Stratégie & Recommandations  
> **Base de travail :** `index.html` (lu en intégralité) · `AUDIT-SITE-AGENCEBOOSTIA.md` · `candidature-brief.md` · mémoires projet  
> **⚠️ Note :** Les fichiers `docs/` (SOURCE_OF_TRUTH, SITE_V2_BRIEF, etc.) n'existent pas encore. Ce handoff est construit depuis les sources primaires. Si Claude Code produit HANDOFF_CODE_TO_COWORK.md en amont d'une prochaine session, ce document sera à mettre à jour.

---

## Synthèse — 3 points clés

**1. L'architecture de conversion est inversée.**  
Le hero pousse vers l'audit gratuit → puis immédiatement une deuxième grande section "Audit Banner" enfonce le même CTA. Résultat : le visiteur voit deux fois le même message avant d'avoir vu les services. La Comparison (qui est l'un des assets les plus convaincants du site) est enterrée au milieu — après la Candidature qui brise le flow B2B.

**2. La preuve sociale est absente — c'est le talon d'Achille critique.**  
"98% satisfaction" dans le tableau comparatif et "Satisfaction garantie" dans le CTA final sans aucun client visible = risque de crédibilité. Le site doit soit reformuler ces éléments, soit les appuyer avec un premier cas réel (Svelte Shape en tant que labo interne est légitime et disponible).

**3. Le wording manque de spécificité sur l'ICP.**  
Le site vise les "boutiques Shopify françaises" (décision validée 20/06/2026) mais le hero dit "propulsez votre business" — trop générique. Les services, le tunnel d'offres et le CTA peuvent tous être rendus plus pointus sur la cible e-commerce sans sacrifier la lisibilité.

---

## Architecture proposée

### Structure actuelle (à corriger)
```
Top Banner → Nav → Hero → Audit Banner → Tools Ticker → Garanties (4 cartes emoji)
→ Services (6+1) → Candidature "Nouveau" → Comparison → Process → Pricing Tunnel
→ FAQ → Bottom CTA → Footer
```

### Structure V2 recommandée
```
Top Banner → Nav → Hero → Tools Ticker → Proof Points (4 cartes reformulées)
→ Services (6+1, restructurés) → Process (4 étapes) → Comparison
→ Pricing Tunnel → Social Proof Placeholder → FAQ → Audit Banner → Bottom CTA
→ Footer
```

**Justification des déplacements :**

| Section | Mouvement | Raison |
|---|---|---|
| Audit Banner | Après FAQ, avant CTA final | Redondance avec hero — mieux comme "dernier filet" de conversion |
| Tools Ticker | Immédiatement après hero | Renforcer la crédibilité technique juste après la promesse |
| Comparison | Avant Pricing Tunnel | La logique de conversion : comprendre la différence → voir les offres |
| Candidature "Nouveau" | Supprimer de la section mid-page | Rompt le flow B2B — conserver dans nav + footer uniquement |
| Process | Avant Comparison | Rassurer sur "comment ça marche" avant de comparer puis acheter |
| Social Proof Placeholder | Après Pricing | Renforcer après l'exposition aux prix |

---

## Wording par section

### Top Banner (announcement bar)
**Actuel :** `🎯 Nouveau : obtenez votre audit marketing gratuit — rapport personnalisé en 24h →`  
**V2 :** `⚡ Audit flash offert — on analyse votre boutique Shopify et on vous livre 3 actions concrètes en 24h →`  
*Raison : "boutique Shopify" ancre l'ICP dès la première ligne.*

---

### Hero

**Badge :**  
Actuel : `✦ Agence IA nouvelle génération`  
V2 : `✦ Agence marketing IA · Shopify & Web`  
*Raison : positionne sur l'ICP sans perdre la dimension premium.*

**H1 :**  
Actuel : `Propulsez votre business avec l'intelligence artificielle`  
V2 (option A) : `Transformez votre boutique Shopify avec l'intelligence artificielle`  
V2 (option B) : `Propulsez votre boutique avec l'intelligence artificielle` *(si Kevin veut garder "business" pour élargir)*  
*Note : un `<br>` est présent dans le code entre "business" et "avec" — gérer uniquement en CSS pour ne pas créer de bug de concaténation côté crawlers.*

**Sous-titre (p principal) :**  
Actuel : `Marketing digital, création web et automatisation IA. Des résultats mesurables, livrés en 7 jours.`  
V2 : `Marketing IA, création web et automatisation pour e-commerçants. Résultats mesurables, livrés en 7 jours.`

**Sous-titre secondaire (petite ligne GEO) :**  
Actuel : `SEO + visibilité IA — optimisez votre présence sur Google, ChatGPT, Gemini et Perplexity.`  
**SUPPRIMER** de la hero section — trop technique pour l'accroche principale. À intégrer dans la carte service SEO/GEO.

**CTA pair :**  
- Primaire : `Audit gratuit →` ✅ Conserver  
- Secondaire : `Découvrir les services` ✅ Conserver

---

### Proof Points (anciennement "Garanties 4 cartes emoji")

Les cartes actuelles sont correctes mais le wording peut être renforcé :

| Actuel | V2 |
|---|---|
| 🎯 **Audit offert** · Diagnostic clair avant engagement | 🎯 **Audit flash offert** · 3 failles identifiées, rapport en 24h |
| ⚡ **Réponse rapide** · Premier retour selon disponibilité | ⚡ **Livraison en 7 jours** · Engagement contractuel sur chaque projet |
| 📦 **Livrables inclus** · Site, textes et recommandations | 📦 **Vous restez propriétaire** · Tous les accès transférés à la livraison |
| 🔐 **Propriété client** · Vos livrables vous appartiennent | 🤖 **100% IA-natif** · Outils IA intégrés dans chaque prestation |

*Raison : supprimer le doublon Livrables/Propriété, ajouter le différenciateur IA.*

---

### Services (section `#sv`)

**Titre section :**  
Actuel : `Tout ce dont vous avez besoin`  
V2 : `Des prestations IA conçues pour les e-commerçants`

**Sous-titre :**  
Actuel : `Des solutions IA complètes pour accélérer votre croissance.`  
V2 : `Marketing, création web, automatisation et SEO — chaque prestation intègre les meilleurs outils IA du marché.`

**Cartes individuelles — ajustements wording :**

- **Marketing IA** → conserver tel quel, bien ciblé  
- **Création Web** → ajouter mention "Shopify ou site sur-mesure" dans la description  
- **Automatisation IA** → bien, conserver  
- **Growth et SEO** → renommer en `SEO & Croissance` pour la lisibilité  
- **Contenu et Branding** → conserver  
- **Consulting IA** → conserver  
- **Carte full-width SEO/GEO** → enrichir avec la ligne GEO supprimée du hero : `"Votre site optimisé pour Google, ChatGPT, Gemini et Perplexity — la nouvelle frontière du référencement."`

---

### Process (section `#ps`)

**Titre :**  
Actuel : `De l'idée au résultat en 4 étapes`  
V2 : `Votre projet en 4 étapes claires`

**Sous-titre :**  
Actuel : `Un processus clair et éprouvé pour transformer votre vision en résultats mesurables.`  
V2 : `Audit → Stratégie → Livraison → Optimisation. Sans jargon, sans surprise.`

---

### Comparison (section `#cs`)

**Problème critique — "98% satisfaction" :**  
Ce chiffre apparaît dans le tableau comparatif colonne AgenceBoostIA. Sans clients référencés publiquement, ce chiffre est un risque de crédibilité.

**Options (Kevin doit choisir) :**
- **Option A (recommandée)** : Remplacer par `100% satisfaction` — plus crédible pour une agence naissante (0 client insatisfait sur les projets livrés)
- **Option B** : Supprimer cette ligne du tableau et la remplacer par `Satisfaction mesurée · À chaque livraison`
- **Option C** : Conserver 98% mais ajouter une note `(sur les projets livrés en 2026)` — honnête mais fragile

**Titre section :**  
Actuel : `AgenceBoostIA vs Agence classique`  
V2 : `Pourquoi choisir AgenceBoostIA ?` + sous-titre `Comparez les différences concrètes.`  
*Raison : le titre actuel est bon mais la V2 est plus orientée bénéfice visiteur.*

---

### Pricing Tunnel (section `#pr`)

**Titre section :**  
Actuel : `Votre parcours, étape par étape`  
V2 : `Choisissez votre point d'entrée`

**Sous-titre :**  
Actuel : `Commencez gratuitement. Progressez selon votre budget. Chaque offre est une victoire mesurable.`  
V2 : `Audit gratuit, correction rapide ou refonte complète — chaque étape est indépendante. Aucun engagement obligatoire.`

**Wording des step-wd (sous-labels italiques) :**

| Actuel | V2 |
|---|---|
| « Je découvre » | ✅ Conserver |
| « Je corrige » | ✅ Conserver |
| « Je décolle » | ✅ Conserver |
| « Je domine » | V2 : `« Je délègue »` *(plus précis pour un pack mensuel géré)* |

**Pack Étincelle — description :**  
Actuel : `Tes 3 premières victoires concrètes corrigées sur ton site. En 48h. Sans engagement.`  
V2 : `Vos 3 corrections prioritaires implémentées sur votre site. 48h. Résultats visibles immédiatement.`  
*Raison : tutoiement vs vouvoiement à harmoniser — le site principal tutoie et vouvoie en alternance. Kevin doit décider d'une règle.*

**⚠️ Point de décision Kevin — tutoiement ou vouvoiement ?**  
Le tunnel actuel mixe les deux (Pack Étincelle tutoie, le reste vouvoie). Ce choix doit être arrêté et appliqué uniformément.

---

### Social Proof Placeholder (section à CRÉER)

**Position :** Entre Pricing Tunnel et FAQ.

**Contenu minimal recommandé (sans inventer de résultats) :**

```
[TAG] Premiers résultats

"Notre premier projet : Svelte Shape — site web livré, SEO optimisé, 
performance Lighthouse 90+. En cours d'indexation Google."

[Capture screenshot Svelte Shape — optionnel si disponible]

+ CTA : Demandez le même traitement pour votre boutique →
```

*Alternative si Kevin ne veut pas exposer Svelte Shape publiquement :*  
Créer un encart neutre : `"Premiers livrables disponibles — demandez à voir notre travail en audit gratuit."` avec CTA vers /audit-gratuit.

*⚠️ Règle absolue : ne jamais inventer de témoignage, résultat chiffré, ou client fictif.*

---

### Audit Gratuit Banner (section déplacée)

**Nouvelle position :** Juste avant le Bottom CTA (après FAQ).  
**Wording actuel :** Correct, conserver tel quel.

---

### FAQ

**Ajouter 2 questions supplémentaires :**

Q7 (déjà là) : "C'est quoi le GEO IA ?" ✅  
**À ajouter :**

Q8 : `"Vous travaillez avec des boutiques Shopify uniquement ?"`  
Réponse : `"Notre cœur de métier est le e-commerce, principalement les boutiques Shopify françaises. On travaille aussi avec des WordPress, des indépendants et des PME sur devis. L'audit gratuit permet de voir si votre situation correspond à notre méthode."`

Q9 : `"Combien ça coûte réellement, tout compris ?"`  
Réponse : `"Vous voyez les vrais tarifs sur cette page : audit flash offert, Pack Étincelle à 147€, Pack Décollage à 490€, Pack Croissance à 699€/mois. Pas de frais cachés, pas de dépassement sans validation."`

---

### Bottom CTA

**Titre :**  
Actuel : `Prêt à multiplier votre croissance par 3 ?`  
**Conserver** — accrocheur, non vérifiable comme un engagement contractuel.

**Sous-titre :**  
Actuel : `Rejoignez les entrepreneurs qui ont déjà adopté l'IA pour dépasser leurs concurrents. Audit gratuit, sans engagement.`  
V2 : `Audit flash offert. On analyse votre boutique et on vous livre un plan d'action concret en 24h. Sans engagement.`  
*Raison : "Rejoignez les entrepreneurs qui ont DÉJÀ adopté" — présuppose une base clients large, risqué au démarrage.*

**Badges de réassurance :**  
Actuel : `Réponse en 24h · Sans engagement · 100% sur-mesure · Satisfaction garantie`  
V2 : `Réponse en 24h · Sans engagement · 100% sur-mesure · Propriété complète des livrables`  
*Raison : "Satisfaction garantie" sans clients publics = promesse creuse. Remplacer par une garantie concrète.*

---

## Direction visuelle

### Palette — status V2
La palette actuelle (`--bg: #0A0A0F`, `--primary: #6C63FF`, `--a2: #A78BFA`) est **validée et à conserver**. Aucun changement de palette pour V2.

**Ce qui change concrètement :**

1. **Gradient hero** : Le `radial-gradient` existant (violet 15% opacity) peut monter à 18-20% pour plus d'impact visuel — actuellement très discret sur les écrans lumineux.

2. **Section alternance bg** : L'alternance `--bg` / `--bg2` (#0A0A0F / #111118) est bien. S'assurer que la nouvelle section "Social Proof" utilise `--bg3` (#16161F) pour la distinguer visuellement.

3. **Candidature section** : La couleur d'accent `#A78BFA` (lavande) pour la section Candidature est correcte et bien différenciée du violet principal. Conserver si la section reste visible quelque part.

4. **Pricing Tunnel — Pack Croissance** : Le thème gold (`rgba(201,168,76,0.35)`) est une bonne différentiation. Conserver. S'assurer que le bouton `.bfg` est accessible en contraste.

5. **WhatsApp button** : Actuellement `var(--primary)` (violet) — bien, conforme à la charte. ✅ Déjà corrigé depuis l'audit.

6. **La section "Audit Banner"** (fond `--bg2` avec gradient violet) : fonctionne bien mais sa nouvelle position (avant Bottom CTA) devra avoir un separator visuel clair (border-top full-width violet comme sur `.tb`).

### Hiérarchie typographique — ce qui manque
- Les `<h2>` de section ont tous la même taille et la même graisse → sur une page aussi longue, ça crée de la fatigue visuelle. Recommandation : ajouter une classe `.section-tag` plus marquée (actuelle = `.tag` en violet très discret) pour aider l'œil à se repérer.
- Le `.tag` label au-dessus des H2 est correct mais trop petit sur mobile (`.78rem`). Passer à `.82rem` minimum.

---

## Réponses aux questions ouvertes

> *Note : le fichier HANDOFF_CODE_TO_COWORK.md n'a pas encore été produit par Claude Code. Les questions ci-dessous sont dérivées de l'analyse du code actuel et de l'audit AUDIT-SITE-AGENCEBOOSTIA.md.*

**Q1 — Tutoiement vs vouvoiement ?**  
→ **Décision Kevin requise.** Le site mixe les deux. Le Pack Étincelle tutoie ("Tes 3 premières victoires"). Le reste vouvoie. Recommandation : vouvoiement sur tout le site B2B (plus crédible pour une agence premium). Le tutoiement est acceptable sur Instagram et la section Candidature uniquement.

**Q2 — Les CTAs tarifs pointent vers les pages pack ou vers mailto ?**  
→ À vérifier. L'audit de juin signalait des `mailto:` sur les CTAs tarifs. Le code actuel du tunnel pointe vers `/pack-etincelle`, `/pack-decollage`, `/pack-croissance` — à confirmer que ces pages sont bien live (vérification Vercel).

**Q3 — La section stats (50+ clients, 98% satisfaction) doit-elle revenir ?**  
→ Non. La version actuelle avec 4 cartes emoji est mieux pour l'honnêteté au stade actuel. À réactiver avec de vrais chiffres dès que 5+ clients sont livrés.

**Q4 — La Candidature doit-elle rester sur l'accueil ?**  
→ Non au milieu du flow B2B. Conserver dans la nav + footer. Éventuellement ajouter une petite mention dans le footer sous les services.

**Q5 — Faut-il ajouter Svelte Shape comme référence ?**  
→ C'est la décision de Kevin. C'est légitime (vrai projet livré). Si oui, prévoir une section minimale avec screenshot + lien vers getsvelteshape.fr. Si non, la section Social Proof sera neutre ("demandez à voir notre travail").

**Q6 — Le compteur animé doit-il revenir ?**  
→ Pas avant d'avoir de vrais chiffres. Si Kevin veut des stats, utiliser des stats process (ex : "7 jours de délai · 48h de réponse · 100% propriété client") plutôt que des stats d'agence fictives.

---

## Consignes d'intégration pour Claude Code

> Ces consignes sont prêtes à exécuter. Ne pas démarrer avant la validation de Kevin.

### Priorité 1 — Architecture (ordre des sections)
**Réorganiser `index.html` pour obtenir cet ordre :**
1. Top banner (inchangé)
2. Nav (inchangée)
3. Hero (wording modifié — voir section Wording)
4. Tools Ticker (déplacer juste après hero — actuellement après l'Audit Banner)
5. Proof Points / Garanties (4 cartes — wording modifié)
6. Services `#sv` (wording titre + Création Web + carte SEO/GEO modifiés)
7. Process `#ps` (wording titre + sous-titre modifiés)
8. Comparison `#cs` (wording + décision "98% satisfaction" — attendre validation Kevin)
9. Pricing Tunnel `#pr` (wording titre + sous-titre + Pack Croissance step-wd modifiés)
10. Social Proof Placeholder (nouvelle section à créer — voir spec ci-dessus)
11. FAQ `#fq` (ajouter Q8 et Q9)
12. Audit Banner (déplacer ici, retirer de sa position actuelle après hero)
13. Bottom CTA `.ca` (wording modifié)
14. Footer (inchangé sauf si Kevin veut ajouter lien Candidature)

### Priorité 2 — Wording (après validation architecture)
Appliquer tous les changements de texte détaillés dans la section "Wording par section" ci-dessus. **Ne pas modifier les couleurs CSS, les classes, ni le logo SVG** — uniquement les contenus textuels.

### Priorité 3 — Section Social Proof (après validation Kevin)
Créer une section entre `#pr` et `#fq` avec :
- Classe CSS : `.sp` (social proof)
- Style : fond `--bg3`, border-top/bottom `--border`
- Contenu : selon décision Kevin (Svelte Shape visible ou encart neutre)
- CTA : lien vers `/audit-gratuit`

### Contraintes techniques à respecter
- **Ne pas modifier** : logo SVG, palette CSS (`--bg`, `--primary`, etc.), animations `.rv`, script IntersectionObserver, WhatsApp button
- **Ne pas toucher** : `/audit-gratuit`, `/agenceboostia-candidature`, `/pack-etincelle`, `/pack-decollage`, `/pack-croissance`, `vercel.json`
- **Tester après chaque modification** : smooth scroll des ancres nav, responsive mobile 375px, FAQ accordion
- **Vérifier** : que les CTAs du Pricing Tunnel pointent vers les bonnes URLs (pas de `mailto:`)
- **H1** : le `<br>` dans le H1 est acceptable visuellement — gérer le retour ligne uniquement en CSS, ne pas supprimer le `<br>` si cela casse l'affichage

### Décisions validées par Kevin — 30 juin 2026 ✅
- [x] **Vouvoiement partout** sur le site B2B (y compris Pack Étincelle)
- [x] **"98% satisfaction"** → Option B : supprimer cette ligne du tableau comparatif
- [x] **Section Social Proof** → ne pas créer pour l'instant
- [x] **Hero H1** → Option A : `"Transformez votre boutique Shopify avec l'intelligence artificielle"`

---

*Handoff rédigé par Claude Cowork · 30 juin 2026*  
*Prochaine étape : validation Kevin → Claude Code exécute en ordre strict Priorité 1 → 2 → 3*

---

## Plan d'intégration — Claude Code

> **Auteur :** Claude Code — Phase 3 Plan  
> **Date :** 30 juin 2026  
> **Périmètre :** `index.html` uniquement + `sitemap.xml`  
> **Fichiers intouchables :** `agenceboostia-candidature.html`, `merci-candidature.html`, `pack-etincelle.html`, `pack-decollage.html`, `pack-croissance.html`, `audit-gratuit.html`, `vercel.json`, `dashboard.html`

### Cartographie des blocs index.html (lignes actuelles)

| Bloc | Lignes | Note |
|---|---|---|
| `<head>` + CSS + Schema.org | 1–239 | |
| Announcement bar | 242–243 | 1 div, 1 ligne |
| Nav + mobile menu | 245–281 | 2 éléments liés |
| Hero | 282–294 | `<section class="hero">` |
| **Audit Banner** | 295–313 | `<section>` standalone — À DÉPLACER |
| **Tools Ticker** | 314–321 | `<div class="tb">` — À DÉPLACER |
| Proof Points (4 cartes) | 322–329 | `<section class="ss">` |
| Services `#sv` | 330–341 | `<section class="sv" id="sv">` |
| **Candidature section** | 343–359 | commentaire HTML + `<section>` — À SUPPRIMER |
| Comparison `#cs` | 361–373 | `<section class="cs" id="cs">` |
| Process `#ps` | 374–382 | `<section class="ps" id="ps">` |
| Pricing Tunnel `#pr` | 383–431 | `<section class="pr" id="pr">` |
| FAQ `#fq` | 432–443 | `<section class="fq" id="fq">` |
| Bottom CTA `.ca` | 444–456 | `<section class="ca">` |
| Footer | 457–487 | |
| JS inline | 488–fin | Menu hamburger + scroll-reveal |

---

### Plan d'intégration — table complète

| Étape | Fichiers concernés | Action | Risque | Test / validation |
|---|---|---|---|---|
| **0** | `sitemap.xml` | Ajouter 4 URLs manquantes : `/audit-gratuit`, `/pack-etincelle`, `/pack-decollage`, `/pack-croissance` avec `lastmod` et `priority` | Nul — fichier XML indépendant | Valider syntaxe XML + soumettre Google Search Console |
| **1A** | `index.html` l.242–243 | Wording announcement bar : `"🎯 Nouveau : obtenez..."` → `"⚡ Audit flash offert — on analyse votre boutique Shopify et on vous livre 3 actions concrètes en 24h →"` | Bas — 1 ligne de texte | Visuel navigateur, mobile 375px |
| **1B** | `index.html` l.285–293 | Hero : badge, H1, p principal, suppression p GEO secondaire — 4 changements texte | Bas — texte pur. **Garder le `<br>` dans H1** (SEO crawl + rendu mobile) | Vérifier H1 affiché, pas de saut de ligne parasite, lien CTA intact |
| **2** | `index.html` l.314–321 | **DÉPLACER** bloc Tools Ticker (`.tb`) : couper lignes 314–321, coller immédiatement après `</section>` hero (après l.294) | Moyen — déplacement de bloc HTML. Risque : oublier la ligne vide ou couper un `</div>` adjacent | Smooth scroll nav OK, audit banner toujours présent à sa nouvelle position |
| **3** | `index.html` l.295–313 | **DÉPLACER** Audit Banner (`<section>` div.agb) : couper lignes 295–313, coller entre `</section>` FAQ (l.443) et `<section class="ca">` (l.444) | Moyen — bloc de 19 lignes avec styles inline. Après déplacement, ajouter `border-top:1px solid var(--border)` à l'attribut style de la section | Preview Vercel obligatoire — vérifier ordre visuel complet, scroll nav ancres |
| **4** | `index.html` l.343–359 | **SUPPRIMER** section Candidature mid-page (commentaire HTML + `<section>`, lignes 343–359) | Moyen — suppression irréversible sans git. **Lien `/agenceboostia-candidature` reste dans nav et reste intact.** Git commit avant cette étape | Vérifier nav candidature OK, page `/agenceboostia-candidature` toujours accessible, aucun broken link |
| **5** | `index.html` l.361–382 | **INVERSER** Comparison et Process : déplacer bloc Process (374–382) avant bloc Comparison (361–373) | Moyen — permutation de 2 blocs. IDs `#cs` et `#ps` restent sur leurs sections — nav ancres correctes après permutation | Smooth scroll `#ps` et `#cs` depuis nav, ordre visuel correct |
| **6A** | `index.html` l.322–329 | Wording Proof Points : 4 cartes — remplacer textes selon tableau Cowork (4 labels + 4 sous-textes) | Bas — texte pur | Affichage mobile 375px, icônes emoji inchangées |
| **6B** | `index.html` l.330–341 | Wording Services : titre section, sous-titre, desc "Création Web" (+Shopify), renommer "Growth et SEO" → "SEO & Croissance", carte SEO/GEO full-width enrichir description | Bas — texte pur | Grille responsive OK, classe `.svgrid` inchangée |
| **6C** | `index.html` l.374–382 | Wording Process : titre `"De l'idée au résultat en 4 étapes"` → `"Votre projet en 4 étapes claires"`, sous-titre modifié | Bas — texte pur | — |
| **6D** | `index.html` l.361–373 | Wording Comparison : titre → `"Pourquoi choisir AgenceBoostIA ?"` + sous-titre. **Supprimer ligne "Satisfaction client / 98% / ~70%"** (1 div `.cr` à supprimer — D-02) | Bas — texte + suppression d'1 div | Vérifier tableau s'affiche proprement sans la ligne, 6 lignes restantes au lieu de 7 |
| **6E** | `index.html` l.383–431 | Wording Pricing Tunnel : titre, sous-titre, `step-wd` Pack Croissance `"Je domine"` → `"Je délègue"`, description Pack Étincelle vouvoiement (D-01) | Bas — texte pur | Liens vers `/pack-etincelle`, `/pack-decollage`, `/pack-croissance`, `/audit-gratuit` vérifiés inchangés |
| **7** | `index.html` l.432–443 + l.24–74 | FAQ : ajouter Q8 et Q9 en HTML (2 nouveaux `.fi` blocs). **Aussi** : mettre à jour `<script type="application/ld+json">` FAQPage en haut de `<head>` (lignes 38–74) pour ajouter les 2 mêmes Q/R | Bas-moyen — double modification (HTML + JSON-LD). Risque : JSON-LD invalide si virgule manquante | Valider JSON-LD via Google Rich Results Test, accordion FAQ fonctionnel |
| **8** | `index.html` l.444–455 | Wording Bottom CTA : sous-titre + badge `"Satisfaction garantie"` → `"Propriété complète des livrables"` (D-02 logique) | Bas — texte pur | — |
| **9** | `index.html` CSS `<style>` | CSS mineur : hero `radial-gradient` opacity 0.15 → 0.18. `.tag` font-size `.78rem` → `.82rem` | Bas — 2 valeurs CSS | Visuel hero sur écran lumineux, `.tag` mobile lisible |

---

### Points de vigilance

**PV-1 — Pack Étincelle page dédiée non touchée mais tutoie encore**  
D-01 (vouvoiement partout B2B) s'applique à `index.html` mais `pack-etincelle.html` contient encore les textes en tutoiement d'origine ("Tes 3 premières victoires…"). Cowork dit de ne pas toucher les pages packs dans cette phase. **Décision requise Kevin** : étape 6E met le tunnel en vouvoiement dans index.html, mais la page dédiée reste incohérente. À traiter dans une Phase 4 dédiée aux pages packs ou corriger maintenant ?

**PV-2 — CTAs Pricing Tunnel : liens confirmés mais non audités en profondeur**  
Les CTAs du tunnel dans `index.html` pointent bien vers `/pack-etincelle`, `/pack-decollage`, `/pack-croissance`, `/audit-gratuit` (pas de `mailto:`). Mais les **pages de destination** n'ont pas été auditées au-delà des 50 premières lignes. Vérifier avant exécution que leurs propres CTAs ne font pas de `mailto:` bloquant la conversion.

**PV-3 — Announce bar : wording change mais hauteur non testée**  
La contrainte technique identifiée : `pack-croissance.html` a `nav top:38px` supposant une announce bar de 38px. Le nouveau wording est plus long. Si la hauteur de la bar change (wrap sur mobile), la nav de `pack-croissance.html` se décalera. Portée limitée à `pack-croissance.html` qui est hors scope ici — **signaler à Kevin** pour correction ultérieure.

**PV-4 — Suppression section Candidature index.html vs "zones interdites"**  
L'audit Phase 1 notait "ne pas supprimer sans arbitrage". L'arbitrage est maintenant acté dans HANDOFF_COWORK_TO_CODE.md (Q4 : "Non au milieu du flow B2B") et confirmé par les décisions Kevin. La suppression est autorisée. Le lien dans la **nav** vers `/agenceboostia-candidature` doit rester intact — ne pas le toucher.

**PV-5 — Double mise à jour FAQ : HTML + JSON-LD**  
Q8 et Q9 doivent être ajoutées dans deux endroits simultanément : le HTML de la section FAQ et le `<script type="application/ld+json">` FAQPage dans le `<head>`. Oublier l'un des deux crée une incohérence Schema.org. Valider via Google Rich Results Test après exécution.

**PV-6 — `sitemap.xml` : pages packs absentes mais pages packs hors scope refonte**  
Les 4 pages `/audit-gratuit`, `/pack-etincelle`, `/pack-decollage`, `/pack-croissance` sont indexables mais absentes du sitemap. Leur ajout est SEO-prioritaire et non-destructif. Peut être exécuté indépendamment, avant toute modification de `index.html`.

---

### Ordre d'exécution recommandé

```
0.  sitemap.xml — ajout 4 URLs (non-destructif, indépendant, faire en premier)
    → commit : "seo: compléter sitemap.xml avec pages packs et audit"

1.  Wording textes index.html (étapes 1A, 1B, 6A→6E, 8) — tous textes purs, aucune structure
    → commit : "content: wording V2 homepage — hero, services, process, comparison, pricing, cta"

2.  Suppression section Candidature mid-page (étape 4) — irréversible, faire après commit wording
    → commit : "refactor: retirer section candidature du flow B2B index.html"

3.  Déplacer Tools Ticker après Hero (étape 2)
    → commit : "layout: tools ticker déplacé après hero"

4.  Inverser Process / Comparison (étape 5)
    → commit : "layout: process avant comparison"

5.  Déplacer Audit Banner avant Bottom CTA (étape 3)
    → commit : "layout: audit banner déplacé avant CTA final"
    → ⚠️ Preview Vercel obligatoire ici — valider ordre visuel complet avant de continuer

6.  FAQ Q8 + Q9 HTML + JSON-LD (étape 7)
    → commit : "content: FAQ Q8 Q9 + schema.org FAQPage"
    → valider Rich Results Test

7.  CSS mineur (étape 9)
    → commit : "style: hero gradient + tag font-size mobile"
```

> **Règle de sécurité :** chaque commit est un point de rollback. En cas de régression visuelle sur Preview Vercel, `git revert` sur le commit fautif sans toucher aux autres. Ne jamais grouper étapes structurelles (déplacements) et wording dans le même commit.

> **Ne pas déployer en production** avant validation Kevin sur Preview Vercel — règle permanente D-15 / DECISIONS_LOG.

---

*Plan rédigé par Claude Code · 30 juin 2026*  
*En attente de validation explicite Kevin avant toute exécution.*
