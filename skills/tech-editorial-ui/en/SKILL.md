---
name: tech-editorial-landing-en
description: Design system "Tech-Editorial" for developer/engineer-focused marketing landing pages. Inspired by Composio.dev. Minimalist, premium, typographic style. Use for marketing pages.
license: Complete terms in LICENSE.txt
---

# SKILL: Tech-Editorial Landing Page Design System

> Target: Marketing landing pages for technical products (dev tools, SaaS, APIs, frameworks).

---

## 1. VISUAL IDENTITY

### Philosophy
**"Tech-Editorial"**: The typographic elegance of a high-end magazine fused with the austere aesthetic of dev tools. Typography is the main design tool. Color is narrative, not decorative.

**Visual Tone**: Serious, premium, minimalist, technical.
**Mental Reference**: The New York Times × Linear × Stripe.
**Target Audience**: Developers, engineers, technical teams.

### Signatures of the Style
1. Cream/sand background — never pure white.
2. Strict rectangular buttons — `border-radius: 0px`.
3. Serif titles + Monospace UI — strong semantic duality.
4. Background shifts at scroll as a narrative tool.
5. Intentionally generous white space.

---

## 2. COLORS

### Simplified Palette (3 background tones are enough)

| Role | Value | Usage |
|------|-------|-------|
| Main Background | `#F5F2EE` | Body, standard sections |
| Card / Surface | `#F0EDE9` | Cards, inputs, ghost buttons |
| Dark Background | `#080808` | Header, primary button, dark sections |

> **Key Rule**: Do not multiply cream variants. These 3 values cover 95% of usecases. Background is NEVER `#ffffff`.

### Text Palette

| Role | Value | Usage |
|------|-------|-------|
| Main Text | `#0A0A0A` | Titles, body |
| Secondary Text | `#707070` | Subtitles, metadata, labels |
| Text on Dark | `#F0EDE9` | On black sections |
| Separator | `rgba(0,0,0,0.08)` | Borders, dividers |

### Accent Palette (Punctual use only)

| Role | Value | Usage |
|------|-------|-------|
| Success / Positive | `#2DA000` | Numbers "with the product", positive KPIs |
| Error / Negative | `#E62C02` | Error states, numbers "without the product" |
| Blue Accent | `#5C80FF` | Links, code highlights |

> **Rule**: Accents appear ONLY for punctual narrative contrast. No permanent accent colors in nav or standard sections.

### Scroll Narrative Backgrounds

```
1. Hero          → #F5F2EE (cream) + dark/colored radial overlay in background
2. Social proof  → #F5F2EE, grayed partner logos
3. Problem       → transition cream → #080808 (black) — cinematic effect
4. Solution      → return to #F5F2EE or full screen colored background (image/gradient)
5. Use-cases     → #F5F2EE
6. Footer        → #F5F2EE
```

---

## 3. TYPOGRAPHY

### Families (Google Fonts Only)

- **Playfair Display**: H1, H2, narrative titles.
- **DM Mono**: Buttons, nav labels, UI values.
- **Inter**: Body, subtitles, descriptions.

### Foundational Typographic Rules

**1. Mix Roman/Italic in Titles**
The conceptual key word is always italicized, the rest is regular:
```html
<h1>Build agents that <em>actually work</em></h1>
<h2>Complexity <em>erased</em> in one call</h2>
```

**2. Negative letter-spacing on large titles**
Tightens letters for a premium effect. Always apply on H1/H2 (-1px to -1.5px).

**3. Monospace = Interface, Serif = Content**
This duality is the semantic signature. Never mix them.

**4. Body in light weight (300)**
Maintains an air of lightness. Never exceed 400 for body text.

---

## 4. LAYOUT & SPACING

### Section Vertical Spacing
- **Standard section**: `padding: 120px 0`
- **Hero section**: `padding: 160px 0`
- **Narrative transition section** (single centered sentence): `padding: 200px 0`

> The excessive whitespace is **intentional**. Sections with a single centered sentence and 200px padding are design elements in themselves — they create rhythm and breathability.

---

## 5. UI COMPONENTS

**Primary CTA Button**:
```css
.btn-primary {
  display: inline-block;
  background: var(--bg-dark);
  color: var(--text-on-dark);
  font-family: var(--font-mono);
  font-size: 15px;
  text-transform: uppercase;
  border-radius: 0; /* ABSOLUTE RULE */
  padding: 14px 32px;
  cursor: pointer;
}
```

**Cards**:
```css
.card {
  background: var(--bg-surface);
  border: 1px solid var(--border);
  border-radius: 12px; /* ONLY cards get a moderate radius */
  padding: 28px 32px;
}
```

**Comparative Statistic (Narrative KPI)**:
Avant/Après style (e.g., 36hrs vs 5 mins). Use `text-decoration: line-through` for the "before" state.

---

## 6. NARRATIVE SCROLL (Lightweight Implementation)

Use `IntersectionObserver` to trigger fade-ins `.reveal -> .visible` and background shifts `.dark-section`. No heavy scroll event listeners.

---

## 7. ABSOLUTE RULES

| ❌ FORBIDDEN | ✅ REQUIRED |
|---|---|
| `border-radius` on buttons/badges | Strict `border-radius: 0` |
| White background `#ffffff` | Cream background `#F5F2EE` |
| Arial/Roboto for titles | Playfair Display for titles |
| Permanent accent colors | Accents strictly for narrative KPIs |
| Heavy box shadow | `border: 1px solid rgba(0,0,0,0.08)` |
| Heavy body text weight (600+) | Weight 300-400 only |
| Multiply CSS hex colors | Use strictly the 3 background CSS variables |
