---
name: tech-editorial-landing
description: Design system "Tech-Editorial" pour landing pages marketing orientées développeurs/ingénieurs. Inspiré de Composio.dev. Style sobre, premium, typographique. Fond crème, boutons carrés, dualité serif/monospace, scroll narratif cinématographique. Utiliser pour tout projet de landing page, site vitrine, ou page marketing technique.
license: Complete terms in LICENSE.txt
---

# SKILL: Tech-Editorial Landing Page Design System

> Style inspiré de Composio.dev, rationalisé pour la maintenabilité et l'implémentation.
> Cible : landing pages marketing pour produits techniques (dev tools, SaaS, APIs, frameworks).

---

## 1. IDENTITÉ VISUELLE

### Philosophie
**"Tech-Editorial"** : l'élégance typographique d'un magazine haut de gamme fusionnée avec l'esthétique austère des outils dev. La typographie est le principal outil de design. La couleur est narrative, pas décorative.

**Ton visuel** : sérieux, premium, minimaliste, technique.
**Référence mentale** : The New York Times × Linear × Stripe.
**Cible** : développeurs, ingénieurs, équipes techniques.

### Ce qui rend ce style immédiatement reconnaissable
1. Fond crème/sable — jamais blanc pur
2. Boutons rectangulaires stricts — `border-radius: 0px`
3. Titres serif + UI monospace — dualité sémantique forte
4. Changements de fond au scroll comme outil narratif
5. Espaces blancs intentionnellement généreux

---

## 2. COULEURS

### Palette simplifiée (3 tons de fond suffisent)

| Rôle | Valeur | Usage |
|------|--------|-------|
| Fond principal | `#F5F2EE` | Body, sections standard |
| Fond card / surface | `#F0EDE9` | Cards, inputs, bouton ghost |
| Fond sombre | `#080808` | Header, bouton primaire, sections dark |

> **Règle clé** : ne pas multiplier les variantes de crème. Ces 3 valeurs couvrent 95% des cas. Le fond n'est jamais `#ffffff`.

### Palette texte

| Rôle | Valeur | Usage |
|------|--------|-------|
| Texte principal | `#0A0A0A` | Titres, corps |
| Texte secondaire | `#707070` | Sous-titres, métadata, labels |
| Texte sur fond sombre | `#F0EDE9` | Sur sections noires |
| Séparateur | `rgba(0,0,0,0.08)` | Borders, dividers |

### Palette d'accents (usage ponctuel uniquement)

| Rôle | Valeur | Usage |
|------|--------|-------|
| Succès / positif | `#2DA000` | Chiffres "avec le produit", KPIs positifs |
| Erreur / négatif | `#E62C02` | États d'erreur, chiffres "sans le produit" |
| Accent bleu | `#5C80FF` | Liens, highlights code |

> **Règle** : les accents apparaissent uniquement pour un contraste narratif ponctuel. Pas de couleur d'accent permanente dans la nav ou les sections standard.

### Sections de fond (scroll narratif)

Les changements de fond sont des **marqueurs de progression narrative**, pas de la décoration :

```
1. Hero          → #F5F2EE (crème) + overlay radial sombre/coloré en arrière-plan
2. Social proof  → #F5F2EE, logos partenaires grisés
3. Problème      → transition crème → #080808 (noir) — effet cinématographique
4. Solution      → retour #F5F2EE ou fond coloré plein écran (image/gradient)
5. Use-cases     → #F5F2EE
6. Footer        → #F5F2EE
```

---

## 3. TYPOGRAPHIE

### Familles (Google Fonts uniquement)

| Police | Usage | Import |
|--------|-------|--------|
| **Playfair Display** | H1, H2, titres narratifs (remplace Flecha S) | Google Fonts |
| **DM Mono** | Boutons, labels nav, valeurs UI | Google Fonts |
| **Inter** | Corps, sous-titres, descriptions | Google Fonts |

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;1,400;1,500&family=DM+Mono:wght@300;400;500&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
```

> **Note** : Playfair Display est légèrement plus expressif que Flecha S. Compenser avec un `letter-spacing` légèrement plus négatif et un `line-height` plus serré pour un rendu proche.

### Type Scale

| Élément | Police | Taille | Weight | Letter-spacing | Transform |
|---------|--------|--------|--------|----------------|-----------|
| H1 | Playfair Display | 64px | 400 | -1.5px | none |
| H1 italic accent | Playfair Display Italic | 64px | 400 | -1.5px | none |
| H2 section | Playfair Display | 52px | 500 | -1px | none |
| H3 | Playfair Display | 40px | 400 | -0.8px | none |
| Sous-titre | Inter | 20px | 300 | 0 | none |
| Corps | Inter | 16px | 300 | 0 | none |
| **Bouton CTA** | **DM Mono** | **15px** | **500** | **0.3px** | **uppercase** |
| Label nav | DM Mono | 13px | 300 | 0.3px | uppercase |
| Caption / metadata | Inter | 14px | 300 | 0 | none |

### Règles typographiques fondamentales

**1. Mélange roman/italique dans les titres**
Le mot clé conceptuel est toujours en italique, le reste en regular :
```html
<h1>Build agents that <em>actually work</em></h1>
<h2>Complexity <em>erased</em> in one call</h2>
```

**2. Letter-spacing négatif sur les grands titres**
Resserre les lettres pour l'effet premium. Toujours appliquer sur H1/H2.

**3. Monospace = interface, Serif = contenu**
Cette dualité est la signature sémantique du style. Ne jamais mélanger.

**4. Corps en weight léger (300)**
Maintient l'air de légèreté. Ne jamais dépasser 400 pour le corps.

---

## 4. LAYOUT & ESPACEMENT

### Container
```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 48px;
}
```

### Espacement vertical des sections
- **Section standard** : `padding: 120px 0`
- **Section hero** : `padding: 160px 0`
- **Section de transition narrative** (phrase seule, centrée) : `padding: 200px 0`

> L'espace blanc excessif est **intentionnel**. Les sections avec une seule phrase centrée et 200px de padding sont un élément de design à part entière — elles créent du rythme et de la respiration.

### CSS Variables (base du système)
```css
:root {
  /* Couleurs */
  --bg: #F5F2EE;
  --bg-surface: #F0EDE9;
  --bg-dark: #080808;
  --text: #0A0A0A;
  --text-muted: #707070;
  --text-on-dark: #F0EDE9;
  --border: rgba(0, 0, 0, 0.08);
  --accent-positive: #2DA000;
  --accent-negative: #E62C02;

  /* Typography */
  --font-serif: 'Playfair Display', Georgia, serif;
  --font-mono: 'DM Mono', 'Courier New', monospace;
  --font-sans: 'Inter', system-ui, sans-serif;

  /* Spacing */
  --section-padding: 120px;
  --container-padding: 48px;
}
```

---

## 5. COMPOSANTS UI

### Navigation
```css
nav {
  position: fixed;
  top: 0;
  width: 100%;
  height: 64px;
  background: transparent;
  z-index: 100;
  padding: 0 var(--container-padding);
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.nav-link {
  font-family: var(--font-mono);
  font-size: 13px;
  font-weight: 300;
  letter-spacing: 0.3px;
  text-transform: uppercase;
  color: var(--text);
  text-decoration: none;
  padding: 10px 16px;
}
/* Bouton CTA nav (le seul élément avec fond) */
.nav-cta {
  background: var(--bg-dark);
  color: var(--text-on-dark);
  font-family: var(--font-mono);
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.3px;
  text-transform: uppercase;
  padding: 6px 14px;
  border-radius: 0;        /* Carré strict */
  border: none;
  cursor: pointer;
}
```

### Bouton CTA Primaire
```css
.btn-primary {
  display: inline-block;
  background: var(--bg-dark);
  color: var(--text-on-dark);
  font-family: var(--font-mono);
  font-size: 15px;
  font-weight: 500;
  letter-spacing: 0.3px;
  text-transform: uppercase;
  padding: 14px 32px;
  border-radius: 0;        /* Carré strict — règle absolue */
  border: none;
  cursor: pointer;
  min-width: 240px;
  text-align: center;
  text-decoration: none;
  transition: opacity 150ms ease;
}
.btn-primary:hover { opacity: 0.85; }
```

### Bouton CTA Secondaire (ghost)
```css
.btn-secondary {
  display: inline-block;
  background: var(--bg-surface);
  color: var(--text);
  font-family: var(--font-mono);
  font-size: 15px;
  font-weight: 500;
  letter-spacing: 0.3px;
  text-transform: uppercase;
  padding: 14px 32px;
  border-radius: 0;
  border: 1px solid var(--border);
  cursor: pointer;
  min-width: 240px;
  text-align: center;
}
```

### Card
```css
.card {
  background: var(--bg-surface);
  border: 1px solid var(--border);
  border-radius: 12px;     /* Seuls les cards ont un arrondi modéré */
  padding: 28px 32px;
}
.card-title {
  font-family: var(--font-serif);
  font-size: 32px;
  font-weight: 400;
  letter-spacing: -0.6px;
  color: var(--text);
  margin-bottom: 12px;
}
.card-body {
  font-family: var(--font-sans);
  font-size: 16px;
  font-weight: 300;
  color: var(--text-muted);
  line-height: 1.6;
}
```

### Badge / Pill
```css
/* Pill arrondie — pour tags, labels flottants */
.pill {
  display: inline-block;
  background: var(--bg-surface);
  border-radius: 999px;
  padding: 8px 20px;
  font-family: var(--font-sans);
  font-size: 14px;
  font-weight: 400;
  color: var(--text);
}
/* Badge carré — pour statuts, catégories */
.badge {
  display: inline-block;
  background: var(--bg-surface);
  border-radius: 0;
  padding: 4px 10px;
  font-family: var(--font-mono);
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 0.3px;
  text-transform: uppercase;
  color: var(--text-muted);
}
```

### Statistique comparative (KPI narratif)
```css
/* Pattern "avant/après" — 36hrs vs 5 mins */
.stat-group {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.stat-before {
  font-family: var(--font-sans);
  font-size: 40px;
  font-weight: 300;
  color: var(--text-muted);
  text-decoration: line-through;
}
.stat-after {
  font-family: var(--font-sans);
  font-size: 40px;
  font-weight: 500;
  color: var(--accent-positive);
}
.stat-label {
  font-family: var(--font-sans);
  font-size: 14px;
  font-weight: 300;
  color: var(--text-muted);
}
```

---

## 6. SCROLL NARRATIF (implémentation simplifiée)

Le scroll narratif est la feature la plus distinctive du style, mais aussi la plus coûteuse. Voici une implémentation légère avec **IntersectionObserver** uniquement — pas de scroll listeners lourds.

### Fade-in au scroll (base)
```css
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 600ms ease, transform 600ms ease;
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
```
```javascript
const observer = new IntersectionObserver(
  (entries) => entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('visible');
  }),
  { threshold: 0.15 }
);
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
```

### Changement de fond de section
```css
body { background: var(--bg); transition: background 600ms ease; }
/* Sections sombres — le JS toggle une classe sur body */
.dark-section {
  background: var(--bg-dark);
  color: var(--text-on-dark);
}
```
```javascript
const darkSections = document.querySelectorAll('.dark-section');
const bodyObserver = new IntersectionObserver(
  (entries) => entries.forEach(e => {
    document.body.classList.toggle('is-dark', e.isIntersecting);
  }),
  { threshold: 0.5 }
);
darkSections.forEach(s => bodyObserver.observe(s));
```

### Texte défilant en parallax (optionnel, léger)
```css
.scrolling-text {
  font-family: var(--font-mono);
  font-size: 20px;
  color: rgba(112, 112, 112, 0.4);
  white-space: nowrap;
  overflow: hidden;
}
/* Animer via CSS uniquement */
@keyframes marquee {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}
.scrolling-text-inner {
  display: inline-block;
  animation: marquee 20s linear infinite;
}
```

---

## 7. STRUCTURE HTML TYPE (landing page)

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;1,400&family=DM+Mono:wght@300;500&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
</head>
<body>

  <!-- Navigation fixe -->
  <nav>...</nav>

  <!-- Section Hero -->
  <section class="section-hero reveal">
    <div class="container">
      <h1>Titre avec mot <em>clé</em> en italique</h1>
      <p class="subtitle">Sous-titre en Inter 300, 20px</p>
      <div class="cta-group">
        <a href="#" class="btn-primary">Get Started</a>
        <a href="#" class="btn-secondary">Documentation</a>
      </div>
    </div>
  </section>

  <!-- Section texte narratif seul (respiration) -->
  <section class="section-statement reveal">
    <div class="container">
      <h2>Une phrase forte et centrée.</h2>
    </div>
  </section>

  <!-- Section sombre (transition cinématographique) -->
  <section class="dark-section reveal">
    <div class="container">
      <h2>Ce qui rend le problème <em>visible</em></h2>
    </div>
  </section>

  <!-- Section use-cases (cards) -->
  <section class="section-usecases reveal">
    <div class="container">
      <div class="cards-grid">
        <div class="card">...</div>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>...</footer>

</body>
</html>
```

---

## 8. RÈGLES ABSOLUES

| ❌ Interdit | ✅ Requis |
|---|---|
| `border-radius` sur boutons/badges | `border-radius: 0` strict |
| Fond blanc `#ffffff` | Fond crème `#F5F2EE` |
| Police Arial, Roboto, system-ui pour titres | Playfair Display pour titres |
| Couleurs d'accent permanentes | Accents uniquement pour KPIs narratifs |
| Box-shadow prononcée | `border: 1px solid rgba(0,0,0,0.08)` |
| Body text en weight 600+ | Weight 300-400 uniquement |
| Scroll listeners lourds | IntersectionObserver uniquement |
| Valeurs CSS quasi-identiques multipliées | 3 tons de fond maximum via CSS variables |
