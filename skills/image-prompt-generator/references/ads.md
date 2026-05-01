# Ads and Creative Marketing — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Sections 4.6 and 5.5

## When to use this guide

Generating ads, campaigns, social media creatives, fashion shots, images with marketing copy, billboards, campaign concepts.

---

## Key principles (from the official documentation)

> "Ad generation works best when the prompt is written like a creative brief rather than a purely technical image spec. Describe the brand, audience, culture, concept, composition, and exact copy, then let the model make taste-driven creative decisions inside those boundaries."

- Write the prompt like a **creative brief**, not a technical spec
- Include: brand positioning, target audience, desired vibe, scene, tagline
- The model interprets audience cues, infers art direction and proposes visual details
- If text must appear in the image: put it **in quotes** and request verbatim rendering
- Ask for clean, legible typography
- No watermarks, no extra logos, no unsolicited text

---

## Elicitation — questions to ask

1. **Brand name and what it does** (brief)
2. **Target audience** (e.g.: urban youth, executives, mothers, gamers)
3. **Vibe/mood** (e.g.: energetic, premium, nostalgic, minimalist, street)
4. **Scene or visual concept** (what should appear in the image)
5. **Text/tagline** that should appear in the image (exact, if any)
6. **Format/use** (Instagram post, banner, billboard, story)

---

## Prompt template — Ad / Fashion Shot

```
Give me a [TYPE — e.g.: cool in-culture ad / fashion shot] for a brand called [BRAND NAME].
It's a [BRAND DESCRIPTION — e.g.: hip young street brand]. The ad shows [SCENE/CONCEPT — e.g.: a group of friends hanging out together] with the tagline "[EXACT TAGLINE]."
Make it feel like a polished campaign image for [AUDIENCE — e.g.: a youth streetwear audience]: [ADJECTIVES — e.g.: stylish, contemporary, energetic, and tasteful].
Use clean composition, strong color direction, natural poses, and premium fashion photography cues.
Render the tagline exactly once, clearly and legibly, integrated into the ad layout.
No extra text, no watermarks, no unrelated logos.
```

### Real example from the documentation (Thread streetwear)

```
Give me a cool in culture ad / fashion shot for a brand called Thread.
It's a hip young street brand. The ad shows a group of friends hanging out together with the tagline "Yours to Create."
Make it feel like a polished campaign image for a youth streetwear audience: stylish, contemporary, energetic, and tasteful.
Use clean composition, strong color direction, natural poses, and premium fashion photography cues.
Render the tagline exactly once, clearly and legibly, integrated into the ad layout.
No extra text, no watermarks, no unrelated logos.
```

---

## Prompt template — Creative marketing with product + text in image

> Use when the creative includes an existing product (via input image) and copy text in the scene.

```
Create a realistic [SCENARIO TYPE — e.g.: billboard mockup / social media ad] of [PRODUCT] on [ENVIRONMENT — e.g.: a highway scene during sunset / a city street at night].
Billboard/Ad text (EXACT, verbatim, no extra characters):
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

> **Note:** This example uses the **editing** function (not generation), with a product image as input.

---

## Recommended parameters

- **Model:** `gpt-image-2`
- **Size:** `1024x1536` (vertical/stories/posts) or `1536x1024` (horizontal/banners)
- **Quality:** `medium` for concepts; `high` when text in the image needs to be precise

---

## Additional tips

- For **text in the image**: if text fidelity is imperfect, keep the prompt strict and iterate — small wording or layout adjustments usually improve legibility
- For **multiple campaign variations**: generate with `n=4` describing color or scene variations
- For **ads with a real product**: use the editing function passing the product photo as input
- Always include the word **"polished"** or **"premium"** when you want a brand campaign look, not a casual photo
