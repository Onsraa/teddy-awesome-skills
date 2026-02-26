---
name: mapf-fis-ui-en
description: Design system for MAPF-FIS (Multi-Agent Path Finding — Fault Injection Simulator). Use this when building any UI component, layout, or HTML/CSS interface for the MAPF-FIS project.
license: Complete terms in LICENSE.txt
---

# SKILL: MAPF-FIS UI Design System — "Scientific Instrument" Style

> Architecture target: Bevy WASM canvas (central 3D viewport) + peripheral HTML/CSS/JS via wasm-bindgen.

---

## 1. VISUAL IDENTITY

### Philosophy
**"Scientific Instrument"**: The aesthetic of high-precision measurement instruments. Sober, technical, confident. The Bevy 3D scene is the absolute center of the experience — the UI never competes with it, it serves it.

**Golden Rule**: If the UI draws more attention than the simulation, it has failed.

**Target Audience**: Researchers, engineers, developers.
**Visual Tone**: Precise, dense but breathable, premium but not marketing-oriented.
**References**: Linear × Three.js Editor × W&B dashboard.

### Page Layout Architecture
```
┌─────────────┬──────────────────────────────┬────────────┐
│  #panel-left│                              │#panel-right│
│  Pre-sim    │      #canvas-bevy            │  Real-time │
│  Parameters │      (Bevy WASM viewport)    │  Metrics   │
│  Config     │                              │  Agents    │
│  Scenario   │                              │  Stats     │
└─────────────┴──────────────────────────────┴────────────┘
│                   #toolbar-bottom                        │
│         Sim Controls · Timeline · Status                 │
└──────────────────────────────────────────────────────────┘
```

The Bevy canvas occupies **70-75%** of the width. The panels are discreet tools.

---

## 2. COLORS

### Fundamental Rule
The background is **never pure white**. It is always slightly tinted cream/sand. UI panels have a cream background. The Bevy viewport has its own dark background managed internally.

### Main Palette
| Role | CSS Value | Usage |
|------|-----------|-------|
| Global body background | `rgb(246, 244, 240)` | Panel backgrounds, entire page |
| Panel surface | `rgb(244, 241, 237)` | Sidebars, toolbar |
| Card surface | `rgb(247, 244, 240)` | Stat cards, sections |
| Input surface | `rgb(240, 237, 233)` | Inputs, sliders track |
| Dark section background | `rgb(8, 8, 8)` | Top header bar |
| Separators | `rgba(5, 5, 5, 0.08)` | Borders, dividers |

### Text Palette
| Role | CSS Value | Usage |
|------|-----------|-------|
| Main text | `rgb(5, 5, 5)` | Titles, key labels |
| Secondary text | `rgb(112, 112, 112)` | Descriptions, metadata |
| Muted text | `rgb(160, 160, 160)` | Placeholders, captions |
| Text on dark background| `rgb(244, 241, 237)` | Header bar |

### State Palette (Agents & Simulation)
| State | CSS Value | Usage |
|-------|-----------|-------|
| IDLE | `rgb(160, 160, 160)` | Waiting agent |
| MOVING | `rgb(45, 160, 0)` | Moving agent |
| DELAYED | `rgb(230, 140, 0)` | Delayed agent (fault propagation) |
| FAULT | `rgb(230, 44, 2)` | Agent failure |
| CRITICAL | `rgb(143, 58, 222)` | Critical agent (heatmap) |
| SUCCESS | `rgb(45, 160, 0)` | Simulation completed successfully |

> These state colors are the **only saturated colors** in the UI. They must pop immediately against the cream background.

---

## 3. TYPOGRAPHY

### Families
| Target Font | Free Alternative | Usage |
|---|---|---|
| **Flecha S Regular** | **Playfair Display** | Section titles, scenario names |
| **DM Mono** | **DM Mono** (Google Fonts ✓) | Buttons, UI labels, numerical values |
| **Inter Display** | **Inter** (Google Fonts ✓) | Body, descriptions, stats |

> **IMPORTANT**: Use `DM Mono` for **all numerical values** (timestamps, scores, counters) to reinforce the measurement instrument feel.

### Type Scale (Dashboard)
| Element | Font | Size | Weight | Notes |
|---------|------|------|--------|-------|
| Scenario Title | Playfair Display | 28px | 400 | Letter-spacing -0.5px |
| Panel Title | DM Mono | 11px | 500 | Uppercase, ls 0.8px |
| Metric Value | DM Mono | 32px | 400 | Real-time numbers |
| Metric Label | Inter | 12px | 400 | Muted, under the value |
| Body / Description | Inter | 14px | 300 | Line-height 1.6 |
| Button | DM Mono | 13px | 500 | Uppercase, ls 0.4px |
| State Badge | DM Mono | 11px | 500 | Uppercase |
| Input Label | Inter | 12px | 400 | Muted |

### Typographic Rules
1. **Panel titles are uppercase monospace** — clears semantic separation between "interface label" and "content".
2. **All numerical values are DM Mono**.
3. **Slightly negative letter-spacing** on serif titles (-0.5 to -1px).
4. **Positive letter-spacing** on all uppercase elements (+0.4 to +0.8px).

---

## 4. LAYOUT & SPACING

### Dimensions
- **Left Panel**: `280px` fixed
- **Right Panel**: `260px` fixed
- **Bottom Toolbar**: `56px` fixed
- **Header Bar**: `44px` fixed
- **Bevy Canvas**: Remainder (`calc(100vw - 540px)`)

### Internal Panel Spacing
- **Panel padding**: `16px`
- **Gap between sections**: `24px`
- **Gap between label and value**: `4px`
- **Card padding**: `12px 16px`
- **Button padding**: `8px 16px`

> Every pixel matters in a dashboard. Use functional spacing (16-24px), not marketing scale.

---

## 5. UI COMPONENTS (CSS Patterns)

### Buttons
**Primary Button**:
```css
.btn-primary {
  background: rgb(5, 5, 5);
  border: none;
  border-radius: 0px; /* STRICT SQUARE */
  color: rgb(244, 241, 237);
  font-family: "DM Mono", monospace;
  text-transform: uppercase;
  padding: 10px 20px;
  cursor: pointer;
}
```

**Secondary Button**:
```css
.btn-secondary {
  background: rgb(240, 237, 233);
  border: 1px solid rgba(5, 5, 5, 0.12);
  border-radius: 0px; /* STRICT SQUARE */
  color: rgb(5, 5, 5);
  font-family: "DM Mono", monospace;
  text-transform: uppercase;
  padding: 8px 16px;
  cursor: pointer;
}
```

---

## 6. BEVY ↔ HTML COMMUNICATION (wasm-bindgen)

### Pattern
Use `wasm-bindgen` to safely serialize data to JS via `serde_wasm_bindgen` or custom DOM events (`mapf-state-update`).
Expose tick rate, agents array with states, fault_count, etc.

---

## 7. CRITICAL RULES (NEVER VIOLATE)

1. **`border-radius: 0px`** on all buttons, inputs, badges, cards — absolute signature of the style.
2. **Never use pure white backgrounds** — always cream/sand (`rgb(246,244,240)`).
3. **All numerical values MUST be DM Mono**.
4. **UI Labels are always uppercase with positive letter-spacing**.
5. **Saturated colors are ONLY for agent states** to immediately catch the eye.
6. **No HTML overlays on the Bevy canvas** — panels are strictly lateral.
7. **No box-shadows** — subtle borders only.
8. **No unnecessary animations** — allow only state change transitions (color changes, opacity).

---

## 8. ANTI-PATTERNS (DO NOT DO THIS)

| ❌ DO NOT DO | ✅ DO INSTEAD |
|---|---|
| `border-radius: 8px` on buttons | Strict `border-radius: 0px` |
| White background `#ffffff` | Cream background `rgb(246,244,240)` |
| Heavy box-shadows | Borders `rgba(5,5,5,0.08)` |
| Accent colors everywhere | Colors ONLY on agent states |
| Inter font for numbers | DM Mono for ALL values |
| Glassmorphism / blur | Opaque, clean surfaces |
