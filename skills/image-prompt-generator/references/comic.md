# Story-to-Comic Strip — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Section 4.7

## When to use this guide

Creating comic strips, sequential visual Reels, panel stories, visual narratives with multiple scenes.

---

## Key principles (from the official documentation)

> "For story-to-comic generation, define the narrative as a sequence of clear visual beats, one per panel. Keep descriptions concrete and action-focused so the model can translate the story into readable, well-paced panels."

- Define the narrative as a **sequence of clear visual beats**, one per panel
- Keep descriptions **concrete and action-focused**
- Specify the number of panels and orientation (vertical, horizontal)
- Describe each panel separately with specific action and composition
- Avoid abstract descriptions — the model needs visible actions, not feelings

---

## Elicitation — questions to ask

1. **What is the story/idea?** (summary in 1-2 sentences)
2. **How many panels?** (default: 4)
3. **Character(s)** (visual description of the protagonist)
4. **Visual style** (e.g.: cartoon, manga, watercolor, minimalist, children's book)
5. **Orientation** (vertical for Reel/Stories, horizontal for classic strip)

---

## Prompt template

```
Create a short vertical comic-style [FORMAT — e.g.: reel / strip] with [NUMBER] equal-sized panels.
Panel 1: [BEAT 1 — concrete action, composition, what the character is doing, expression]
Panel 2: [BEAT 2 — concrete action, what changes, reaction]
Panel 3: [BEAT 3 — climax or development]
Panel 4: [BEAT 4 — resolution or punchline]
```

### Real example from the documentation (pet home alone)

```
Create a short vertical comic-style reel with 4 equal-sized panels.
Panel 1: The owner leaves through the front door. The pet is framed in the window behind them, small against the glass, eyes wide, paws pressed high, the house suddenly quiet.
Panel 2: The door clicks shut. Silence breaks. The pet slowly turns toward the empty house, posture shifting, eyes sharp with possibility.
Panel 3: The house transformed. The pet sprawls across the couch like it owns the place, crumbs nearby, sunlight cutting across the room like a spotlight.
Panel 4: The door opens. The pet is seated perfectly by the entrance, alert and composed, as if nothing happened.
```

---

## Recommended parameters

- **Model:** `gpt-image-2`
- **Size:** `1024x1536` (vertical — ideal for Reels and Stories)
- **Quality:** `medium`

---

## Additional tips

- **For consistent characters across panels**: describe the character the same way in each panel — "the same orange tabby cat", not just "the cat"
- **For a strong visual punchline**: panel 4 should have an action that subverts or completes the expectation created in the previous panels
- **For a specific style**: add at the beginning of the prompt — "in a clean cartoon style", "in a Japanese manga style", "in a warm watercolor children's book style"
- **For longer stories**: generate in blocks of 4 panels using the editing function to maintain character consistency
