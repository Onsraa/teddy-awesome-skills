---
name: scientific-instrument-ui
description: Design system pour les dashboards de simulation 3D/WebGL. Utilisez ceci lors de la création de tout composant d'interface utilisateur, layout, ou interface HTML/CSS qui entoure un espace de rendu 3D central ou de la data visualisation.
license: Complete terms in LICENSE.txt
---

# SKILL: Scientific Instrument UI Design System

> Architecture cible : Canvas WebGL (viewport 3D central) + HTML/CSS/JS périphérique.

---

## 1. IDENTITÉ VISUELLE

### Philosophie
**"Scientific Instrument"** : l'esthétique d'un instrument de mesure de haute précision. Sobre, technique, confiant. La scène 3D est le centre absolu de l'expérience — l'UI ne compete jamais avec elle, elle la sert.

**Règle d'or** : si l'UI attire l'œil plus que la simulation, elle a échoué.

**Cible** : chercheurs, ingénieurs, développeurs.
**Ton visuel** : précis, dense mais respirant, premium sans être marketing.
**Références** : Linear × Three.js Editor × W&B dashboard.

### Architecture de la page
```
┌─────────────┬──────────────────────────────┬────────────┐
│  #panel-left│                              │#panel-right│
│  Paramètres │      #canvas-webgl           │  Métriques │
│  pré-sim    │      (Viewport 3D)           │  temps réel│
│  Config     │                              │  Entités   │
│  Scénario   │                              │  Stats     │
└─────────────┴──────────────────────────────┴────────────┘
│                   #toolbar-bottom                        │
│         Contrôles simulation · Timeline · Status         │
└──────────────────────────────────────────────────────────┘
```

Le canvas WebGL occupe **70-75%** de la largeur. Les panneaux sont des outils discrets.

---

## 2. COULEURS

### Règle fondamentale
Le fond n'est **jamais blanc pur**. Il est toujours légèrement teinté crème/sable. Les panneaux UI sont sur fond crème. La viewport 3D a son propre fond sombre géré en interne.

### Palette principale
| Rôle | Valeur CSS | Usage |
|------|-----------|-------|
| Fond global (body) | `rgb(246, 244, 240)` | Background panneaux, page entière |
| Surface panel | `rgb(244, 241, 237)` | Sidebars, toolbar |
| Surface card | `rgb(247, 244, 240)` | Cards de stats, sections |
| Surface input | `rgb(240, 237, 233)` | Inputs, sliders track |
| Fond section sombre | `rgb(8, 8, 8)` | Header barre supérieure |
| Séparateur | `rgba(5, 5, 5, 0.08)` | Borders, dividers |

### Palette texte
| Rôle | Valeur CSS | Usage |
|------|-----------|-------|
| Texte principal | `rgb(5, 5, 5)` | Titres, labels clés |
| Texte secondaire | `rgb(112, 112, 112)` | Descriptions, métadonnées |
| Texte muted | `rgb(160, 160, 160)` | Placeholders, captions |
| Texte sur fond sombre | `rgb(244, 241, 237)` | Header bar |

### Palette d'état (Entités & simulation)
| État | Valeur | Usage |
|------|--------|-------|
| IDLE | `rgb(160, 160, 160)` | Entité en attente |
| ACTIVE | `rgb(45, 160, 0)` | Entité en déplacement/active |
| WARNING | `rgb(230, 140, 0)` | Entité en alerte |
| ERROR | `rgb(230, 44, 2)` | Erreur d'entité |
| CRITICAL | `rgb(143, 58, 222)` | État critique |
| SUCCESS | `rgb(45, 160, 0)` | Simulation terminée OK |

> Ces couleurs d'état sont la **seule couleur saturée** dans l'UI. Elles doivent ressortir immédiatement sur le fond crème.

---

## 3. TYPOGRAPHIE

### Familles (avec alternatives Google Fonts)
| Police cible | Alternative libre | Usage |
|---|---|---|
| **Flecha S Regular** | **Playfair Display** | Titres de section, noms de scénarios |
| **DM Mono** | **DM Mono** (Google Fonts ✓) | Boutons, labels UI, valeurs numériques |
| **Inter Display** | **Inter** (Google Fonts ✓) | Corps, descriptions, stats |

> L'utilisation de DM Mono pour **toutes les valeurs numériques** (timestamps, scores, compteurs) renforce l'aspect instrument de mesure.

### Type Scale (dashboard)
| Élément | Police | Taille | Weight | Notes |
|---------|--------|--------|--------|-------|
| Titre scénario | Playfair Display | 28px | 400 | Letter-spacing -0.5px |
| Titre panel | DM Mono | 11px | 500 | Uppercase, ls 0.8px |
| Valeur métrique | DM Mono | 32px | 400 | Chiffres temps réel |
| Label métrique | Inter | 12px | 400 | Muted, sous la valeur |
| Corps / description | Inter | 14px | 300 | Line-height 1.6 |
| Bouton | DM Mono | 13px | 500 | Uppercase, ls 0.4px |
| Badge état | DM Mono | 11px | 500 | Uppercase |
| Input label | Inter | 12px | 400 | Muted |

### Règles typographiques
1. **Titres de panel en monospace uppercase** — séparation sémantique claire entre "label d'interface" et "contenu"
2. **Toutes les valeurs numériques en DM Mono** — cohérence instrument de mesure
3. **Letter-spacing légèrement négatif** sur les titres serif (-0.5 à -1px)
4. **Letter-spacing positif** sur tous les éléments uppercase (+0.4 à +0.8px)

---

## 4. LAYOUT & ESPACEMENT

### Dimensions
- **Panel gauche** : `280px` fixe
- **Panel droit** : `260px` fixe
- **Toolbar bas** : `56px` fixe
- **Header bar** : `44px` fixe
- **Canvas WebGL** : tout le reste (`calc(100vw - 540px)`)

### Espacement interne des panneaux
- **Padding panel** : `16px`
- **Gap entre sections** : `24px`
- **Gap entre label et valeur** : `4px`
- **Padding card** : `12px 16px`
- **Padding bouton** : `8px 16px`

> Chaque pixel compte dans un dashboard. Utilisez l'espacement **fonctionnel** (16-24px).

---

## 5. COMPOSANTS UI

Exemples CSS de la signature :
```css
.btn-primary {
  background: rgb(5, 5, 5);
  border: none;
  border-radius: 0px; /* Carré strict — signature du style */
  color: rgb(244, 241, 237);
  font-family: "DM Mono", monospace;
  text-transform: uppercase;
}
```

---

## 6. COMMUNICATION SIMULATION ↔ HTML

### Pattern recommandé
Utiliser des WebSockets ou un pont Events (WASM, ThreeJs renderer loop) pour déclencher l'événement dans le DOM (ex: `simulation-state-update`).

---

## 7. RÈGLES CRITIQUES (à ne jamais violer)

1. **`border-radius: 0px`** sur tous les boutons, inputs, badges, cards — signature absolue du style
2. **Fond jamais blanc pur** — toujours crème/sable (`rgb(246,244,240)` ou proche)
3. **Toutes les valeurs numériques en DM Mono** — cohérence instrument
4. **Labels UI toujours uppercase + letter-spacing positif** — séparation sémantique
5. **Couleurs saturées uniquement pour les états des entités** — elles doivent attirer l'œil immédiatement
6. **La canvas de rendu 3D ne reçoit jamais d'overlay HTML** — les panneaux sont latéraux, jamais par-dessus
7. **Pas de box-shadow** — les bordures subtiles suffisent
8. **Pas d'animations superflues** — les seules transitions autorisées sont les changements d'état (couleur badge, valeur métrique)
