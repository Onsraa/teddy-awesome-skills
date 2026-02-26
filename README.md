# Teddy Awesome Skills 🚀

Bienvenue sur le dépôt **Teddy Awesome Skills** !

Ce repository professionnel regroupe une collection de compétences (Skills) avancées pour vos agents IA (Claude, GPT-4, Cursor, etc.). Ces skills incarnent des systèmes de design précis et ré-exploitables pour vos projets de développement Frontend et interfaces Web.

## 📦 Les Skills disponibles

1. **[MAPF-FIS UI Design System](./skills/mapf-fis-ui/)**
   - Un style austère, sobre et confiant type "Instrument Scientifique".
   - Idéal pour les tableaux de bord techniques de simulation, les interfaces 3D WebGL (Bevy, Three.js) ou la dataviz.
   
2. **[Tech-Editorial Landing Page Design System](./skills/tech-editorial-ui/)**
   - Une esthétique "Magazine haut de gamme" mariée au minimalisme technique.
   - Idéal pour les landing pages de Dev Tools, startups tech, APIs et solutions SaaS.

## 🏗️ Architecture du projet

Afin de pouvoir s'adapter aussi bien au développeur (lisibilité) qu'aux l'intelligences artificielles (performance d'exécution), chaque skill est décliné en deux versions :

```bash
skills/
└── mon-skill-nom/
    ├── fr/         # 🇫🇷 Version 100% en français (idéale pour la documentation humaine)
    │   └── SKILL.md
    └── en/         # 🇬🇧 Version 100% en anglais (optimisée pour la génération IA)
        └── SKILL.md
```

**Pourquoi deux versions ?**
Les modèles de langages sont naturellement plus performants (raisonnement et programmation) lorsqu'on leur donne des consignes dans leur langue maternelle d'entraînement : l'Anglais. La version _Anglaise_ est donc idéale pour paramétrer le comportement profond de l'agent.

👉 [Lisez notre documentation sur l'approche Française vs Anglaise](./docs/fr-vs-en.md)

## 🛠️ Comment utiliser un Skill ?

- Copiez le contenu du fichier `SKILL.md` de la langue de votre choix dans vos propres "Custom Instructions" / "System Prompt" sur Claude, ChatGPT, Cursor, GitHub Copilot.
- Ou si vous utilisez un agent avec un contexte persistant local (comme *Claude Code*), pointez-le simplement vers le chemin du fichier concerné (ex: `Utilise le skill stocké dans skills/tech-editorial-ui/en/SKILL.md pour redessiner ma page index.html`).

---
_Créé pour standardiser, accélérer et sublimer le développement Frontend assisté par IA._
