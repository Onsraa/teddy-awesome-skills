# Français vs Anglais : Le Guide

Lors de la rédaction de vos propres "Skills" (instructions métiers pour agents d'IA, comme Claude, GPT-4, etc.), la question de la langue se pose fréquemment. Doit-on les rédiger dans notre langue maternelle, ou en anglais ?

Ce dépôt offre une méthode simple en proposant **deux dossiers disctincts** pour chaque design system.

## Pourquoi un dossier EN (Anglais) ?

1. **La majorité des données des LLMs :** Les modèles de pointe comme GPT-4, Claude 3 ou Gemini ont été entraînés à plus de 80% sur des corpus anglophones. Leur capacité à comprendre des listes de règles imbriquées, des contraintes (constraints) ou de la syntaxe de programmation est considérablement supérieure dans cette langue.
2. **Moins de "hallucinations"** : Forcer une syntaxe technique complexe en français ("Ne jamais mettre de rayon de bordure aux composants" plutôt que "Never use border-radius") peut générer des approximations si l'agent transpose littéralement le concept au moment de générer du code (HTML, CSS).
3. **Communauté et standards :** L'anglais est le standard universel du développement logiciel.

## Pourquoi un dossier FR (Français) ?

Si vous êtes développeur français, il est plus naturel d'interagir, de faire revoir son code et de lire des rapports en français. Les prompts originaux ont souvent été pensés en français pour qu'ils soient :
- Plus inclusifs pour vos collègues ou votre équipe (pour la relecture de guidelines).
- Plus facilement clairs lorsque votre LLM doit produire du contenu marketing francophone.

## Structure de ce dépôt

Afin d'offrir une flexibilité maximale, chaque dossier de _Skill_ propose deux implémentations :
- `/fr/SKILL.md` : Le design system 100% en français. Facile à lire pour les métiers, le marketing et les développeurs qui gèrent la maintenance.
- `/en/SKILL.md` : Le design system 100% en anglais. Direct et incisif, pensé pour les LLMs.

Il est recommandé de privilégier la version **`/en/SKILL.md`** à l'intérieur du prompt de votre LLM pour lui demander de générer du code complexe sans faille, et bien sûr libre à vous de donner une instruction supplémentaire *explicite* en lui demandant de vous répondre en français de façon naturelle !
