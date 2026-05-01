# Translating Text in Images — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Section 4.2

## When to use this guide

Localizing existing designs (ads, prints, infographics, packaging, UI screenshots) to another language without rebuilding the layout from scratch.

---

## Key principles (from the official documentation)

> "The key is to preserve everything except the text—keep typography style, placement, spacing, and hierarchy consistent—while translating verbatim and accurately, with no extra words, no reflow unless necessary, and no unintended edits to logos, icons, or imagery."

- Preserve **everything** except the text: typography, placement, spacing, hierarchy
- Translate **verbatim and accurately**, with no extra words
- No layout reflow unless strictly necessary
- Do not edit logos, icons, or visual elements
- **Type: Editing** — requires the original image as input

---

## Elicitation — questions to ask

1. **To which language?** (e.g.: Spanish, Portuguese, Japanese, French)
2. **Any specific terms that should not be translated?** (brand names, technical terms)
3. **Is minor layout adjustment allowed if the translated text is much longer?** (yes/no)

---

## Prompt template

```
Translate the text in the [IMAGE TYPE — e.g.: infographic / ad / packaging] to [LANGUAGE].
Do not change any other aspect of the image.
```

> For more explicit preservation:

```
Translate all text in this image to [LANGUAGE]. Preserve the exact typography style, font weight, placement, spacing, and visual hierarchy of every text element. Do not alter logos, icons, illustrations, colors, or layout. Translate verbatim and accurately, with no added words or omissions. Do not reflow or redesign the layout.
```

### Real example from the documentation (infographic → Spanish)

```
Translate the text in the infographic to Spanish. Do not change any other aspect of the image.
```

---

## Recommended parameters

- **Model:** `gpt-image-2`
- **Size:** keep the same size as the original image
- **Quality:** `medium` (use `high` if the original has small or dense text)

---

## Additional tips

- For languages with longer text (German, Portuguese vs. English): mention in the prompt if minimal reflow is acceptable — "minor reflow is acceptable only if text overflows"
- For languages with different scripts (Arabic, Japanese, Hebrew): specify text direction if needed — "right-to-left layout for Arabic"
- If only **part** of the image should be translated: specify exactly what — "translate only the title and body text, keep all labels and button text in English"
