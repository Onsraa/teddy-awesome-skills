# Teddy Awesome Skills 🚀

Welcome to the **Teddy Awesome Skills** repository!

This professional repository contains a collection of advanced Skills (prompts and instructions) for your AI agents (Claude, GPT-4, Cursor, etc.). These skills provide precise, reusable design systems and logic for your Frontend development and web interface projects.

## 📦 Available Skills

1. **[Scientific Instrument UI Design System](./skills/scientific-instrument-ui/)**
   - An austere, sober, and confident "Scientific Instrument" style.
   - Ideal for technical simulation dashboards, 3D WebGL interfaces (Three.js), or data visualization.
   
2. **[Tech-Editorial Landing Page Design System](./skills/tech-editorial-ui/)**
   - A "High-end Magazine" aesthetic combined with technical minimalism.
   - Ideal for Dev Tools landing pages, tech startups, APIs, and SaaS solutions.

## 🏗️ Project Architecture

To accommodate both developers (readability) and artificial intelligence (execution performance), each skill is available in two versions:

```bash
skills/
└── my-skill-name/
    ├── en/         # �� 100% English version (optimized for AI generation)
    │   └── SKILL.md
    └── fr/         # �� 100% French version (ideal for human documentation)
        └── SKILL.md
```

**Why two versions?**
Large Language Models naturally perform better (both in reasoning and coding) when given instructions in their native training language: English. The _English_ version is therefore ideal for setting up the core behavior of your agent. 

👉 [Read our documentation on the English vs French approach](./docs/en-vs-fr.md)

## 🛠️ How to use a Skill?

- Copy the content of the `SKILL.md` file from your preferred language folder into your "Custom Instructions" / "System Prompt" on Claude, ChatGPT, Cursor, or GitHub Copilot.
- Or, if you use an agent with persistent local context (like *Claude Code*), simply point it to the relevant file path (e.g., `Use the skill from skills/tech-editorial-ui/en/SKILL.md to redesign my index.html page`).

---
_Created to standardize, accelerate, and elevate AI-assisted Frontend development._
