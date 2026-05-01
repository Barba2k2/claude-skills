# Logo Generation — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Section 4.5

## When to use this guide

Creating logos, brands, icons, visual marks, brand identity.

---

## Key principles (from the official documentation)

> "Strong logo generation comes from clear brand constraints and simplicity. Describe the brand's personality and use case, then ask for a clean, original mark with strong shape, balanced negative space, and scalability across sizes."

- Describe the **brand personality** and use context
- Ask for a **clean and original** mark with strong shape
- Balanced negative space and **legibility at all sizes**
- Flat, minimal design, no gradients (unless essential)
- Simple background, centered logo with generous padding
- No watermark

You can specify the `n` parameter to generate multiple variations (e.g.: 4 versions).

---

## Elicitation — questions to ask

Before generating, ask:

1. **Brand/company name** (exact, as it should appear if there is text)
2. **What does the brand do?** (segment, product, service)
3. **Personality/vibe** (e.g.: modern and tech, artisanal and warm, institutional, playful)
4. **Visual preferences** (icon + text? Symbol only? Monogram? Specific colors?)
5. **How many variations?** (default: 1; recommended maximum: 4)

---

## Prompt template (based on the official example)

```
Create an original, non-infringing logo for a company called [COMPANY NAME], [SHORT BUSINESS DESCRIPTION].
The logo should feel [PERSONALITY/VIBE — e.g.: warm, simple, and timeless / bold and modern / playful and friendly].
Use clean, vector-like shapes, a strong silhouette, and balanced negative space.
Favor simplicity over detail so it reads clearly at small and large sizes.
Flat design, minimal strokes, no gradients unless essential.
Plain background. Deliver a single centered logo with generous padding. No watermark.
```

### Real example from the documentation

```
Create an original, non-infringing logo for a company called Field & Flour, a local bakery.
The logo should feel warm, simple, and timeless. Use clean, vector-like shapes, a strong silhouette, and balanced negative space.
Favor simplicity over detail so it reads clearly at small and large sizes. Flat design, minimal strokes, no gradients unless essential.
Plain background. Deliver a single centered logo with generous padding. No watermark.
```

---

## Recommended parameters

- **Model:** `gpt-image-2`
- **Size:** `1024x1536`
- **Quality:** `medium`
- **n:** `4` (if you want variations to choose from)

---

## Additional tips

- If you need variations with different colors, generate with `n=4` and describe the desired palette in the prompt
- For logos with specific text: put the name **in quotes** in the prompt and reinforce that it must appear exactly as written
- For symbol-only logos (no text): explicitly say "no text, symbol only"
- For monogram: say "lettermark using the initials [XY]"
