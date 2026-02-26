# English vs French: The Guide

When writing your own "Skills" (business instructions for AI agents like Claude, GPT-4, Cursor, etc.), the question of language frequently arises. Should they be written in our native language, or in English?

This repository offers a simple organizational method by providing **two distinct folders** for each design system.

## Why an EN (English) folder?

1. **The majority of LLMs' training data:** State-of-the-art models like GPT-4, Claude 3, or Gemini have been trained on over 80% English corpora. Their ability to understand nested rule lists, constraints, or programming syntax is considerably superior in this language.
2. **Fewer "hallucinations":** Forcing complex technical syntax in French ("Ne jamais mettre de rayon de bordure aux composants" instead of "Never use border-radius: 0") can generate approximations when the agent literally transposes the concept into HTML/CSS code.
3. **Community and standards:** English is the universal standard for software development.

## Why an FR (French) folder?

If you are a French developer, it is more natural to interact, have code reviewed, and read reports in French. Original prompts are often conceived in French so they can be:
- More inclusive for your colleagues or team (for reviewing guidelines).
- Easily understood when your LLM needs to produce French marketing content specifically.

## Structure of this repository

To maxmize flexibility, every _Skill_ directory offers two implementations:
- `/en/SKILL.md`: The design system 100% in English. Direct and incisive, designed for LLMs.
- `/fr/SKILL.md`: The design system 100% in French. Easy to read for business, marketing, and the developers managing its maintenance.

We recommend prioritizing the **`/en/SKILL.md`** version inside your LLM prompt when asking it to generate flawless complex code. Of course, you are free to give an *explicit* supplementary instruction asking it to reply to you in French naturally!
