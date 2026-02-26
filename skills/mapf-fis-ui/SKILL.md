---
name: mapf-fis-ui
description: Design system for MAPF-FIS (Multi-Agent Path Finding — Fault Injection Simulator). Use this when building any UI component, layout, or HTML/CSS interface for the MAPF-FIS project. Architecture cible — Bevy WASM canvas (viewport 3D central) + HTML/CSS/JS périphérique via wasm-bindgen. Style "Scientific Instrument" — sobre, technique, fonctionnel. Jamais de border-radius sur les boutons, jamais de fond blanc pur.
license: Complete terms in LICENSE.txt
---

# SKILL: MAPF-FIS UI Design System — "Scientific Instrument" Style

> Adapté du style Tech-Editorial de Composio, reconfiguré pour un dashboard de simulation scientifique 3D.
> Architecture cible : Bevy (canvas WASM central) + HTML/CSS/JS périphérique via wasm-bindgen.

---

## 1. IDENTITÉ VISUELLE

### Philosophie
**"Scientific Instrument"** : l'esthétique d'un instrument de mesure de haute précision. Sobre, technique, confiant. La scène 3D Bevy est le centre absolu de l'expérience — l'UI ne compete jamais avec elle, elle la sert.

**Règle d'or** : si l'UI attire l'œil plus que la simulation, elle a échoué.

**Cible** : chercheurs, ingénieurs, développeurs.
**Ton visuel** : précis, dense mais respirant, premium sans être marketing.
**Références** : Linear × Three.js Editor × W&B dashboard.

### Architecture de la page
```
┌─────────────┬──────────────────────────────┬────────────┐
│  #panel-left│                              │#panel-right│
│  Paramètres │      #canvas-bevy            │  Métriques │
│  pré-sim    │      (Bevy WASM viewport)    │  temps réel│
│  Config     │                              │  Agents    │
│  Scénario   │                              │  Stats     │
└─────────────┴──────────────────────────────┴────────────┘
│                   #toolbar-bottom                        │
│         Contrôles simulation · Timeline · Status        │
└──────────────────────────────────────────────────────────┘
```

La canvas Bevy occupe **70-75%** de la largeur. Les panneaux sont des outils discrets.

---

## 2. COULEURS

### Règle fondamentale
Le fond n'est **jamais blanc pur**. Il est toujours légèrement teinté crème/sable. Les panneaux UI sont sur fond crème. La viewport Bevy a son propre fond sombre géré en interne.

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

### Palette d'état (agents & simulation)
| État | Valeur | Usage |
|------|--------|-------|
| IDLE | `rgb(160, 160, 160)` | Agent en attente |
| MOVING | `rgb(45, 160, 0)` | Agent en déplacement |
| DELAYED | `rgb(230, 140, 0)` | Agent en retard (fault propagation) |
| FAULT | `rgb(230, 44, 2)` | Agent en panne |
| CRITICAL | `rgb(143, 58, 222)` | Agent critique (heatmap) |
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

> Pour MAPF-FIS : DM Mono est gratuit et disponible — l'utiliser pour **toutes les valeurs numériques** (timestamps, scores, compteurs) renforce l'aspect instrument de mesure.

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
- **Canvas Bevy** : tout le reste (`calc(100vw - 540px)`)

### Espacement interne des panneaux
- **Padding panel** : `16px`
- **Gap entre sections** : `24px`
- **Gap entre label et valeur** : `4px`
- **Padding card** : `12px 16px`
- **Padding bouton** : `8px 16px`

> Contraste avec Composio : espacement **fonctionnel** (16-24px) et non marketing (120-200px). Chaque pixel compte dans un dashboard.

---

## 5. COMPOSANTS UI

### Header Bar (fond sombre)
```css
#header {
  background: rgb(8, 8, 8);
  height: 44px;
  padding: 0 16px;
  display: flex;
  align-items: center;
  gap: 24px;
}
/* Logo / nom projet */
.header-title {
  font-family: "DM Mono", monospace;
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.6px;
  text-transform: uppercase;
  color: rgb(244, 241, 237);
}
/* Status global simulation */
.header-status {
  font-family: "DM Mono", monospace;
  font-size: 11px;
  font-weight: 400;
  letter-spacing: 0.4px;
  text-transform: uppercase;
  color: rgb(112, 112, 112);
}
```

### Panel (sidebar générique)
```css
.panel {
  background: rgb(244, 241, 237);
  border-right: 1px solid rgba(5, 5, 5, 0.08);
  overflow-y: auto;
  padding: 16px;
}
.panel-section-title {
  font-family: "DM Mono", monospace;
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.8px;
  text-transform: uppercase;
  color: rgb(112, 112, 112);
  margin-bottom: 12px;
}
```

### Carte de métrique
```css
.metric-card {
  background: rgb(247, 244, 240);
  border: 1px solid rgba(5, 5, 5, 0.06);
  border-radius: 0px;          /* Carré strict */
  padding: 12px 16px;
  margin-bottom: 8px;
}
.metric-value {
  font-family: "DM Mono", monospace;
  font-size: 28px;
  font-weight: 400;
  color: rgb(5, 5, 5);
  line-height: 1;
}
.metric-label {
  font-family: "Inter", sans-serif;
  font-size: 11px;
  font-weight: 400;
  color: rgb(112, 112, 112);
  letter-spacing: 0.2px;
  margin-top: 4px;
}
```

### Badge d'état agent
```css
.agent-badge {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 4px 10px;
  border-radius: 0px;          /* Carré strict */
  font-family: "DM Mono", monospace;
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.4px;
  text-transform: uppercase;
}
/* Dot coloré selon l'état */
.agent-badge::before {
  content: '';
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: currentColor;
}
/* Variantes d'état */
.badge-idle     { color: rgb(160,160,160); background: rgba(160,160,160,0.1); }
.badge-moving   { color: rgb(45,160,0);   background: rgba(45,160,0,0.1);   }
.badge-delayed  { color: rgb(230,140,0);  background: rgba(230,140,0,0.1);  }
.badge-fault    { color: rgb(230,44,2);   background: rgba(230,44,2,0.1);   }
.badge-critical { color: rgb(143,58,222); background: rgba(143,58,222,0.1); }
```

### Bouton Primaire (lancer simulation)
```css
.btn-primary {
  background: rgb(5, 5, 5);
  border: none;
  border-radius: 0px;          /* Carré strict — signature du style */
  padding: 10px 20px;
  width: 100%;
  font-family: "DM Mono", monospace;
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.4px;
  text-transform: uppercase;
  color: rgb(244, 241, 237);
  cursor: pointer;
  transition: opacity 150ms ease;
}
.btn-primary:hover { opacity: 0.85; }
.btn-primary:disabled { opacity: 0.35; cursor: not-allowed; }
```

### Bouton Secondaire
```css
.btn-secondary {
  background: rgb(240, 237, 233);
  border: 1px solid rgba(5, 5, 5, 0.12);
  border-radius: 0px;
  padding: 8px 16px;
  font-family: "DM Mono", monospace;
  font-size: 12px;
  font-weight: 500;
  letter-spacing: 0.4px;
  text-transform: uppercase;
  color: rgb(5, 5, 5);
  cursor: pointer;
}
```

### Input / Slider
```css
.input-group {
  margin-bottom: 16px;
}
.input-label {
  font-family: "Inter", sans-serif;
  font-size: 12px;
  font-weight: 400;
  color: rgb(112, 112, 112);
  margin-bottom: 6px;
  display: block;
}
.input-field {
  width: 100%;
  background: rgb(240, 237, 233);
  border: 1px solid rgba(5, 5, 5, 0.1);
  border-radius: 0px;
  padding: 7px 10px;
  font-family: "DM Mono", monospace;
  font-size: 13px;
  color: rgb(5, 5, 5);
  outline: none;
}
.input-field:focus {
  border-color: rgba(5, 5, 5, 0.4);
}
/* Slider */
input[type="range"] {
  -webkit-appearance: none;
  width: 100%;
  height: 2px;
  background: rgba(5, 5, 5, 0.15);
  outline: none;
}
input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 12px;
  height: 12px;
  background: rgb(5, 5, 5);
  border-radius: 0px;          /* Carré */
  cursor: pointer;
}
```

### Toolbar Bas (contrôles simulation)
```css
#toolbar {
  background: rgb(244, 241, 237);
  border-top: 1px solid rgba(5, 5, 5, 0.08);
  height: 56px;
  padding: 0 16px;
  display: flex;
  align-items: center;
  gap: 16px;
}
/* Indicateur de step/tick */
.sim-tick {
  font-family: "DM Mono", monospace;
  font-size: 13px;
  font-weight: 400;
  color: rgb(112, 112, 112);
  letter-spacing: 0.2px;
}
.sim-tick span {
  color: rgb(5, 5, 5);
  font-weight: 500;
}
```

### Divider de section
```css
.panel-divider {
  height: 1px;
  background: rgba(5, 5, 5, 0.08);
  margin: 16px 0;
}
```

---

## 6. COMMUNICATION BEVY ↔ HTML (wasm-bindgen)

### Pattern recommandé
```rust
// Côté Rust/Bevy — exposer les données de simulation
#[wasm_bindgen]
pub fn get_simulation_state() -> JsValue {
    // Sérialiser l'état en JSON via serde
    serde_wasm_bindgen::to_value(&state).unwrap()
}

// Ou via events JS custom
web_sys::window()
    .unwrap()
    .dispatch_event(&CustomEvent::new("mapf-state-update").unwrap())
    .unwrap();
```

```javascript
// Côté JS — écouter les updates Bevy
window.addEventListener('mapf-state-update', (e) => {
  updateMetricCards(e.detail);
  updateAgentBadges(e.detail.agents);
});
```

### Données typiques à exposer
- `tick: u32` — step actuel de simulation
- `agents: Vec<AgentState>` — état de chaque agent (position, statut, retard)
- `fault_count: u32` — nombre de fautes actives
- `cascade_depth: u32` — profondeur de cascade actuelle
- `metrics: SimMetrics` — statistiques agrégées

---

## 7. RÈGLES CRITIQUES (à ne jamais violer)

1. **`border-radius: 0px`** sur tous les boutons, inputs, badges, cards — signature absolue du style
2. **Fond jamais blanc pur** — toujours crème/sable (`rgb(246,244,240)` ou proche)
3. **Toutes les valeurs numériques en DM Mono** — cohérence instrument
4. **Labels UI toujours uppercase + letter-spacing positif** — séparation sémantique
5. **Couleurs saturées uniquement pour les états agents** — elles doivent attirer l'œil immédiatement
6. **La canvas Bevy ne reçoit jamais d'overlay HTML** — les panneaux sont latéraux, jamais par-dessus
7. **Pas de box-shadow** — les bordures subtiles suffisent
8. **Pas d'animations superflues** — les seules transitions autorisées sont les changements d'état (couleur badge, valeur métrique)

---

## 8. ANTI-PATTERNS À ÉVITER

| ❌ À éviter | ✅ À faire |
|---|---|
| `border-radius: 8px` sur les boutons | `border-radius: 0px` strict |
| Fond blanc `#ffffff` | Fond crème `rgb(246,244,240)` |
| Box-shadows prononcées | Bordures `rgba(5,5,5,0.08)` |
| Couleurs d'accent partout | Couleurs uniquement sur états agents |
| Police Inter pour les chiffres | DM Mono pour toutes les valeurs |
| Overlays HTML sur la canvas | Panneaux latéraux uniquement |
| Espacement marketing (100px+) | Espacement fonctionnel (16-24px) |
| Glassmorphisme / blur | Surfaces opaques, nettes |
