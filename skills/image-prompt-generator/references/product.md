# Product Photography and E-commerce — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Sections 5.4 and 5.5

## When to use this guide

Product extraction with clean background, e-commerce packshots, product mockups in scenes, billboards with product, marketing creatives using a real product photo (via editing).

---

## Key principles (from the official documentation)

> "Product extraction and mockup prep is commonly used for catalogs, marketplaces, and design systems. Success depends on edge quality (clean silhouette, no fringing/halos) and label integrity (text stays sharp and unchanged)."

- **Silhouette quality**: clean outline, no fringing or halos
- **Label integrity**: product text must remain sharp and unchanged
- For a final transparent background: remove the background in a separate step after generation
- For realism without re-styling: ask only for light polish and a subtle contact shadow
- For creatives with a product in a scene: use the **editing** function passing the real photo as input

---

## Elicitation — questions to ask

1. **Do you have a product photo to use as input?** (essential for editing)
2. **Goal** (white background for catalog, product in scene, billboard, packaging mockup)
3. **Desired scene** (if not white background — e.g.: wooden table, outdoor environment, shelf)
4. **Any text/copy to appear in the image?** (tagline, ad headline)
5. **Shadow** (yes/no, and what type — subtle, dramatic)

---

## Prompt template — Product extraction (white background)

> **Type: Editing** (uses product photo as input)

```
Extract the product from the input image and place it on a plain white opaque background.
Output: centered product, crisp silhouette, no halos/fringing.
Preserve product geometry and label legibility exactly.
Add only light polishing and a subtle realistic contact shadow.
Do not restyle the product; only remove background and lightly polish.
```

### Real example from the documentation (shampoo — extraction)

```
Extract the product from the input image and place it on a plain white opaque background.
Output: centered product, crisp silhouette, no halos/fringing.
Preserve product geometry and label legibility exactly.
Add only light polishing and a subtle realistic contact shadow.
Do not restyle the product; only remove background and lightly polish.
```

---

## Prompt template — Product in scene / marketing creative

> **Type: Editing** (uses product photo as input)

```
Create a realistic [TYPE — e.g.: billboard mockup / lifestyle shot / social media ad] of [PRODUCT] on [ENVIRONMENT/SCENE — e.g.: a highway scene during sunset / a minimalist kitchen counter / a city street at night].
[TEXT IN IMAGE, if any]:
"[EXACT TEXT]"
Typography: [STYLE — e.g.: bold sans-serif], high contrast, centered, clean kerning.
Ensure text appears once and is perfectly legible.
No watermarks, no logos.
```

### Real example from the documentation (shampoo billboard)

```
Create a realistic billboard mockup of the shampoo on a highway scene during sunset.
Billboard text (EXACT, verbatim, no extra characters):
"Fresh and clean"
Typography: bold sans-serif, high contrast, centered, clean kerning.
Ensure text appears once and is perfectly legible.
No watermarks, no logos.
```

---

## Prompt template — Collectible packaging mockup

> **Type: Generation** (no input)

```
Create a collectible [TYPE — e.g.: action figure / toy] of [CHARACTER/PRODUCT DESCRIPTION], in blister packaging.

Concept:
[PRODUCT CONTEXT AND VALUE PROPOSITION — e.g.: A nostalgic holiday collectible inspired by...]

Style:
Premium toy photography, realistic [MATERIALS — e.g.: plastic and painted metal] textures,
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

---

## Recommended parameters

- **Model:** `gpt-image-2`
- **Size:** `1024x1536`
- **Quality:** `medium`

---

## Additional tips

- For a **transparent background**: gpt-image-2 produces an opaque background — use a background removal tool (e.g.: Remove.bg, Canva) after generating the image
- To **preserve the product label**: emphasize "Preserve product geometry and label legibility exactly" — without this the model may alter text and packaging design
- For **multiple scenes with the same product**: use the editing function in series, always with the same product photo as input
