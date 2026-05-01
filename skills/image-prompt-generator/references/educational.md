# Educational and Scientific Visuals — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Sections 4.9 and 4.10

## When to use this guide

Scientific diagrams, educational visuals, classroom posters, data slides, pitch decks, historical timelines, concept maps, course assets and teaching materials.

---

## Key principles (from the official documentation)

> "Prompt them like an instructional design brief: define the audience, lesson objective, visual format, required labels, and scientific constraints."

- Define **audience** (high school students, executives, specialists)
- Define **learning objective** (what the viewer should understand)
- Specify **visual format** (flow diagram, poster, concept map, slide)
- List **required components** and what **should not** appear
- Request consistent visual system: icons in the same style, clear arrows, readable labels
- Use `quality: high` for dense labels, diagrams, assets for slides or printed materials
- Clean white background as default; sufficient white space to scan the concept

---

## Elicitation — questions to ask

1. **Subject/topic** (biology, history, product, business, technology)
2. **Audience** (students, executives, customers, general public)
3. **Format** (process diagram, timeline, concept map, data slide, explanatory poster)
4. **Title** (if any — exact)
5. **Required components** (which steps, molecules, dates, metrics, labels)
6. **Final use** (classroom, presentation, social media post, printed material)

---

## Prompt template — Scientific/educational diagram

```
Create a simple [SUBJECT — e.g.: biology / chemistry / physics] diagram titled "[EXACT TITLE]" for [AUDIENCE — e.g.: high school students / university students].

Show [MAIN CONCEPT — e.g.: how glucose turns into energy inside a cell]. Include [COMPONENTS — e.g.: glycolysis, the Krebs cycle, and the electron transport chain].
Use arrows to connect the steps, and label the main [ELEMENTS — e.g.: molecules]: [LIST OF LABELS — e.g.: glucose, pyruvate, ATP, NADH, FADH2, CO2, O2, and H2O].
Make it look like a clean classroom handout or slide, with a white background, simple icons, clear labels, and easy-to-read text.

Avoid tiny text, extra decoration, or anything that makes the diagram hard to understand.
```

### Real example from the documentation (cellular respiration)

```
Create a simple biology diagram titled "Cellular Respiration at a Glance" for high school students.

Show how glucose turns into energy inside a cell. Include glycolysis, the Krebs cycle, and the electron transport chain.
Use arrows to connect the steps, and label the main molecules: glucose, pyruvate, ATP, NADH, FADH2, CO2, O2, and H2O.
Make it look like a clean classroom handout or slide, with a white background, simple icons, clear labels, and easy-to-read text.

Avoid tiny text, extra decoration, or anything that makes the diagram hard to understand.
```

**Parameters:** `size: 1536x1024` | `quality: high`

---

## Prompt template — Pitch / Data / Presentation Slide

```
Create one [SLIDE TYPE — e.g.: pitch-deck slide / data slide / explainer slide] titled "[TITLE]" that feels like a real [CONTEXT — e.g.: Series A fundraising slide from a YC-backed startup / corporate strategy slide].

Use a clean white background, modern sans-serif typography, and a crisp, minimal layout. The slide should include:
* [VISUAL ELEMENT 1 — e.g.: TAM/SAM/SOM concentric-circle diagram in muted blues and grays]
* [DATA — e.g.: specific numbers: $42B / $8.7B / $340M]
* [VISUAL ELEMENT 2 — e.g.: bar chart showing growth from 2021 to 2026]
* [FOOTER — e.g.: small footnotes: "Source, Year" and "Internal analysis"]
* [OPTIONAL ELEMENT — e.g.: company logo placeholder in bottom-right corner]

The design should look like [QUALITY STANDARD — e.g.: it belongs in a deck that actually raised money]: highly readable text, clear data hierarchy, polished spacing, and professional visual language.

Avoid clip art, stock photography, gradients, shadows, decorative elements, or anything that feels generic or overdesigned.
```

### Real example from the documentation (Market Opportunity slide)

```
Create one pitch-deck slide titled "Market Opportunity" that feels like a real Series A fundraising slide from a YC-backed startup.

Use a clean white background, modern sans-serif typography like Inter, and a crisp, minimal layout. The slide should include:

* A TAM/SAM/SOM concentric-circle diagram in muted blues and grays
* Specific, believable market sizing numbers:
  * TAM: $42B
  * SAM: $8.7B
  * SOM: $340M
* A clean bar chart below showing market growth from 2021 to 2026, with a subtle upward trend
* Small footnotes: "AGI Research, 2024" and "Internal analysis"
* A company logo placeholder in the bottom-right corner

The design should look like it belongs in a deck that actually raised money: highly readable text, clear data hierarchy, polished spacing, and professional startup-style visual language.

Avoid clip art, stock photography, gradients, shadows, decorative elements, or anything that feels generic or overdesigned.
```

**Parameters:** `size: 1536x864` | `quality: high`

---

## Recommended parameters by format

| Format                  | Size        | Quality            |
| ----------------------- | ----------- | ------------------ |
| Scientific diagram      | `1536x1024` | `high`             |
| Educational poster      | `1024x1536` | `high`             |
| Presentation slide      | `1536x864`  | `high`             |
| Explanatory infographic | `1024x1536` | `medium` or `high` |

- **Model:** always `gpt-image-2`

---

## Additional tips

- For **real data in charts**: include the numbers directly in the prompt — the model uses the exact values when provided
- For **technical labels**: list each label explicitly; don't assume the model will include what isn't asked for
- For **icon consistency**: say "use a consistent flat icon style throughout" — this prevents mixing visual styles in the same diagram
- For **assets that will be printed or projected on a large screen**: always use `quality: high` and the maximum size compatible with the use
