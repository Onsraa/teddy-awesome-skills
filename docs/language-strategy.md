# Language Strategy: English vs. Localized Languages

When writing your own "Skills" (business instructions for AI agents like Claude, GPT-4, Cursor, etc.), the question of language frequently arises. Should they be written in your native language, or in English?

This repository offers a simple organizational method by providing **distinct folders** for English and other localized languages (e.g., French, Spanish, German).

## Why an EN (English) folder?

1. **The majority of LLMs' training data:** State-of-the-art models like GPT-4, Claude 3, or Gemini have been trained on predominantly English corpora (often over 80%). Their ability to understand nested rule lists, constraints, complex reasoning, and programming syntax is considerably superior in English.
2. **Fewer "hallucinations":** Forcing complex technical CSS/HTML syntax in localized languages (e.g., "Ne jamais mettre de rayon de bordure aux composants" instead of "Never use border-radius: 0") can generate approximations or logical leaps when the agent translates the concept back into code.
3. **Community and standards:** English is the universal standard for software development.

**Recommendation:** The `/en/SKILL.md` version is **always recommended for executing technical tasks and coding**.

## Why localized folders (e.g., FR, ES, DE)?

If your team is native to a specific country, it is more natural to interact, review guidelines, and read documentation in your native language. 

Localized prompts are highly recommended when:
- **Human Collaboration:** You need to share the design system or instructions with colleagues, designers, or marketing teams who prefer the local language.
- **Content Generation:** Your LLM is tasked with producing marketing copy, legal text, or user-facing content specifically for that region.

### Are there exceptions?

Yes. While English is fundamentally stronger for *coding logic*, localized languages become **mandatory** when dealing with specific cultural or legal constraints:
- **Legal/Compliance (e.g., French Law, German GDPR nuances):** The agent needs the specific local terminology (e.g., *Mentions Légales*, *Impressum*) to avoid generating generic, non-compliant translations.
- **Copywriting & Tone:** If you are generating a localized landing page, providing a Spanish skill (`/es/SKILL.md`) will yield much more natural, idiomatic Spanish marketing copy than asking the `en` skill to "translate to Spanish at the end".

## Structure of this repository

To maximize flexibility, every _Skill_ directory can offer multiple implementations:
- `/en/SKILL.md`: The design system 100% in English. Direct and incisive, designed for maximum LLM coding performance.
- `/fr/SKILL.md` (or `/es/`, `/de/`, etc.): The localized design system. Easy to read for your business teams, and perfect for generating native content.

When in doubt: **Use `/en/` for the brain (logic, code) and your local language for the voice (content, documentation).** If you use the `/en/` skill, you can always simply ask the AI in your prompt to "reply to me and add code comments in French/Spanish".
