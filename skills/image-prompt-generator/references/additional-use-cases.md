# High-Value Additional Use Cases — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Section 6

## When to use this guide

Interior design swap, 3D holiday card, merch/collectible concept, children's book with consistent character.

---

## Index for this section

| Use Case                                      | Section                                                   |
| --------------------------------------------- | --------------------------------------------------------- |
| 6.1 Interior design "swap" (precision edits)  | [see below](#61-interior-design-swap)                     |
| 6.2 3D pop-up holiday card                    | [see below](#62-3d-pop-up-holiday-card)                   |
| 6.3 Collectible Action Figure / Merch         | [see below](#63-collectible-action-figure--merch)         |
| 6.4 Children's Book with consistent character | [see below](#64-childrens-book-with-consistent-character) |

---

## 6.1 Interior Design "Swap" (precision edits)

> "Used for visualizing furniture or decor changes in real spaces without re-rendering the entire scene. The goal is surgical realism: swap a single object while preserving camera angle, lighting, shadows, and surrounding context so the edit looks like a real photograph, not a redesign."

**Type: Editing** (uses environment photo as input)

### Elicitation

1. Environment photo (required as input)
2. Which element to swap? (e.g.: chairs, sofa, rug, lighting)
3. Replace with what? (material, color, desired style)

### Prompt template

```
In this room photo, replace ONLY [ORIGINAL ELEMENT — e.g.: the white chairs] with [NEW ELEMENT — e.g.: chairs made of wood].
Preserve camera angle, room lighting, floor shadows, and surrounding objects.
Keep all other aspects of the image unchanged.
Photorealistic contact shadows and [MATERIAL — e.g.: fabric / wood] texture.
```

### Real example from the documentation

```
In this room photo, replace ONLY white with chairs made of wood.
Preserve camera angle, room lighting, floor shadows, and surrounding objects.
Keep all other aspects of the image unchanged.
Photorealistic contact shadows and fabric texture.
```

**Parameters:** `size: 1536x1024` | `quality: medium`

---

## 6.2 3D Pop-up Holiday Card (product-style mock)

> "Emphasizes tactile realism—paper layers, fibers, folds, and soft studio lighting—so the result reads as a photographed physical product rather than a flat illustration."

**Type: Generation**

### Elicitation

1. Theme/occasion (Christmas, birthday, graduation, New Year)
2. Main scene (what appears in the card)
3. Desired mood/emotion (nostalgic, joyful, sentimental, fun)
4. Exact card text (verbatim)

### Prompt template

```
Create a [TYPE — e.g.: Christmas / birthday / graduation] holiday card illustration.

Scene:
[SCENE DESCRIPTION — e.g.: a cozy Christmas scene with an old teddy bear sitting inside a keepsake box, slightly worn fur, soft stitching repairs, placed near a window with falling snow outside. The scene suggests the child has grown up, but the memories remain.]

Mood:
[MOOD — e.g.: Warm, nostalgic, gentle, emotional.]

Style:
Premium holiday card photography, soft cinematic lighting,
realistic textures, shallow depth of field,
tasteful bokeh lights, high print-quality composition.

Constraints:
- Original artwork only
- No trademarks
- No watermarks
- No logos

Include ONLY this card text (verbatim):
"[EXACT CARD TEXT]"
```

### Real example from the documentation (Christmas card with teddy bear)

```
Create a Christmas holiday card illustration.

Scene:
a cozy Christmas scene with an old teddy bear sitting inside a keepsake box,
slightly worn fur, soft stitching repairs, placed near a window with falling snow outside.
The scene suggests the child has grown up, but the memories remain.

Mood:
Warm, nostalgic, gentle, emotional.

Style:
Premium holiday card photography, soft cinematic lighting,
realistic textures, shallow depth of field,
tasteful bokeh lights, high print-quality composition.

Constraints:
- Original artwork only
- No trademarks
- No watermarks
- No logos

Include ONLY this card text (verbatim):
"Merry Christmas — some memories never fade."
```

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## 6.3 Collectible Action Figure / Merch Concept

> "Used for early merch ideation and pitch visuals. Focuses on premium product photography cues (materials, packaging, print clarity) while keeping designs original and non-infringing."

**Type: Generation**

### Elicitation

1. Product type (action figure, plush, keychain, blister collectible)
2. Character/object description
3. Product concept/narrative (what it evokes or represents)
4. Packaging text (verbatim)

### Prompt template

```
Create a collectible [TYPE — e.g.: action figure / plush keychain / toy] of [CHARACTER/OBJECT DESCRIPTION — e.g.: a vintage-style toy propeller airplane with rounded wings, a front-mounted spinning propeller, slightly worn paint edges, classic childhood proportions, designed as a nostalgic holiday collectible], in blister packaging.

Concept:
[VALUE PROPOSITION — e.g.: A nostalgic holiday collectible inspired by the simple toy airplanes children used to play with during winter holidays. Evokes warmth, imagination, and childhood wonder.]

Style:
Premium toy photography, realistic [MATERIAL — e.g.: plastic and painted metal] textures,
studio lighting, shallow depth of field,
sharp label printing, high-end retail presentation.

Constraints:
- Original design only
- No trademarks
- No watermarks
- No logos

Include ONLY this packaging text (verbatim):
"[PACKAGING TEXT]"
```

### Real example from the documentation (collectible toy plane)

```
Create a collectible action figure of a vintage-style toy propeller airplane with rounded wings,
a front-mounted spinning propeller, slightly worn paint edges,
classic childhood proportions, designed as a nostalgic holiday collectible, in blister packaging.

Concept:
A nostalgic holiday collectible inspired by the simple toy airplanes
children used to play with during winter holidays.
Evokes warmth, imagination, and childhood wonder.

Style:
Premium toy photography, realistic plastic and painted metal textures,
studio lighting, shallow depth of field,
sharp label printing, high-end retail presentation.

Constraints:
- Original design only
- No trademarks
- No watermarks
- No logos

Include ONLY this packaging text (verbatim):
"Christmas Memories Edition"
```

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## 6.4 Children's Book with Consistent Character (multi-image workflow)

> "Designed for multi-page illustration pipelines where character drift is unacceptable. A reusable 'character anchor' ensures visual continuity across scenes, poses, and pages while allowing environmental and narrative variation."

**2-step workflow:**

- **Step 1:** Generation — create the anchor character
- **Step 2:** Editing — use the character as input to continue the story

### Elicitation

1. Character description (appearance, clothing, personality)
2. Story theme/world (forest, space, city, fantasy)
3. Visual style (watercolor, cartoon, flat illustration, hand-painted)
4. Scene for the page to generate

---

### Step 1 — Create the Anchor Character (Generation)

```
Create a children's book illustration introducing a main character.

Character:
[DETAILED CHARACTER DESCRIPTION — e.g.: A young, storybook-style hero inspired by a little forest outlaw, wearing a simple green hooded tunic, soft brown boots, and a small belt pouch. The character has a kind expression, gentle eyes, and a brave but warm demeanor. Carries a small wooden bow used only for helping, never harming.]

Theme:
[THEME — e.g.: The character protects and rescues small forest animals like squirrels, birds, and rabbits.]

Style:
Children's book illustration, [TECHNIQUE — e.g.: hand-painted watercolor look],
soft outlines, warm earthy colors, whimsical and friendly.
Proportions suitable for picture books (slightly oversized head, expressive face).

Constraints:
- Original character (no copyrighted characters)
- No text
- No watermarks
- Plain [ENVIRONMENT — e.g.: forest] background to clearly showcase the character
```

#### Real example from the documentation (forest hero)

```
Create a children's book illustration introducing a main character.

Character:
A young, storybook-style hero inspired by a little forest outlaw,
wearing a simple green hooded tunic, soft brown boots, and a small belt pouch.
The character has a kind expression, gentle eyes, and a brave but warm demeanor.
Carries a small wooden bow used only for helping, never harming.

Theme:
The character protects and rescues small forest animals like squirrels, birds, and rabbits.

Style:
Children's book illustration, hand-painted watercolor look,
soft outlines, warm earthy colors, whimsical and friendly.
Proportions suitable for picture books (slightly oversized head, expressive face).

Constraints:
- Original character (no copyrighted characters)
- No text
- No watermarks
- Plain forest background to clearly showcase the character
```

**Parameters:** `size: 1024x1536` | `quality: medium`

---

### Step 2 — Continue the Story (Editing with anchor character as input)

> Use the image generated in Step 1 as input.

```
Continue the children's book story using the same character.

Scene:
[NEW SCENE — e.g.: The same young forest hero is gently helping a frightened squirrel out of a fallen tree after a winter storm. The character kneels beside the squirrel, offering reassurance.]

Character Consistency:
- Same [ELEMENT 1 — e.g.: green hooded tunic]
- Same facial features, proportions, and color palette
- Same [PERSONALITY — e.g.: gentle, heroic] personality

Style:
Children's book [TECHNIQUE — e.g.: watercolor] illustration,
[LIGHTING — e.g.: soft lighting], [ENVIRONMENT — e.g.: snowy forest environment],
[MOOD — e.g.: warm and comforting] mood.

Constraints:
- Do not redesign the character
- No text
- No watermarks
```

#### Real example from the documentation (snow scene)

```
Continue the children's book story using the same character.

Scene:
The same young forest hero is gently helping a frightened squirrel
out of a fallen tree after a winter storm.
The character kneels beside the squirrel, offering reassurance.

Character Consistency:
- Same green hooded tunic
- Same facial features, proportions, and color palette
- Same gentle, heroic personality

Style:
Children's book watercolor illustration,
soft lighting, snowy forest environment,
warm and comforting mood.

Constraints:
- Do not redesign the character
- No text
- No watermarks
```

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## General tip — Section 6

All these use cases benefit from prompts written as **detailed creative briefs**, not technical specs. The more narrative and emotional context you provide, the more the model produces results with visual coherence and aesthetic intention.
