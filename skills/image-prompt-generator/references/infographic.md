# Infographics and Diagrams — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Sections 4.1 and 4.9

## When to use this guide

Explanatory infographics, posters, diagrams with labels, timelines, "visual wiki", scientific/technical diagrams, data slides, educational assets.

---

## Key principles (from the official documentation)

> "Use infographics to explain structured information for a specific audience: students, executives, customers, or the general public."

- Define **audience** and **learning objective**
- Specify the **visual format** (explainer, poster, labeled diagram, timeline)
- List **required components** and what **should not** appear
- For dense layouts or lots of text in the image: use `quality: high`
- Request clean white background, consistent icons, clear arrows, readable labels, sufficient white space

---

## Elicitation — questions to ask

1. **What needs to be explained?** (main topic/concept)
2. **For whom?** (audience: students, executives, general customers, specialists)
3. **Format?** (general explainer, timeline, flow diagram, comparison, poster)
4. **Required elements?** (specific components, labels, data, icons)
5. **Is there specific text that must appear?** (titles, exact labels)

---

## Prompt template — General infographic

```
Create a detailed infographic about [TOPIC].
[DESCRIBE THE FLOW OR STRUCTURE — e.g.: from X to Y, showing steps A, B, C]
Target audience: [AUDIENCE].
Include: [REQUIRED ELEMENTS — e.g.: arrows connecting steps, labels for main components, a title].
Style: clean classroom/explainer layout, white background, simple icons, clear labels, easy-to-read text.
Avoid tiny text, extra decoration, or anything that makes the diagram hard to understand.
```

### Real example from the documentation (coffee machine)

```
Create a detailed Infographic of the functioning and flow of an automatic coffee machine like a Jura.
From bean basket, to grinding, to scale, water tank, boiler, etc.
I'd like to understand technically and visually the flow.
```

---

## Prompt template — Scientific/educational visual

```
Create a simple [SUBJECT — e.g.: biology / chemistry / physics] diagram titled "[TITLE]" for [AUDIENCE — e.g.: high school students].

Show [MAIN CONCEPT]. Include [COMPONENTS — e.g.: glycolysis, the Krebs cycle, and the electron transport chain].
Use arrows to connect the steps, and label the main molecules/elements: [LIST OF LABELS].
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

---

## Prompt template — Slide / Pitch Deck

```
Create one [SLIDE TYPE — e.g.: pitch-deck slide] titled "[TITLE]" that feels like a real [CONTEXT — e.g.: Series A fundraising slide].

Use a clean white background, modern sans-serif typography, and a crisp, minimal layout. The slide should include:
* [ELEMENT 1 — e.g.: TAM/SAM/SOM concentric-circle diagram]
* [ELEMENT 2 — e.g.: specific market sizing numbers: TAM: $X, SAM: $X, SOM: $X]
* [ELEMENT 3 — e.g.: bar chart showing growth from YEAR to YEAR]
* [ELEMENT 4 — e.g.: small footnotes: "Source, Year"]

The design should look like [QUALITY STANDARD — e.g.: it belongs in a deck that actually raised money]: highly readable text, clear data hierarchy, polished spacing, and professional visual language.

Avoid clip art, stock photography, gradients, shadows, decorative elements, or anything that feels generic or overdesigned.
```

### Real example from the documentation (market slide)

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

---

## Recommended parameters

| Type                 | Size        | Quality                  |
| -------------------- | ----------- | ------------------------ |
| Vertical infographic | `1024x1536` | `medium` (dense: `high`) |
| Scientific diagram   | `1536x1024` | `high`                   |
| Slide / pitch deck   | `1536x864`  | `high`                   |

- **Model:** always `gpt-image-2`

---

## Tip on translating infographics

To localize an existing infographic to another language, use the **editing** function (not generation):

```
Translate the text in the infographic to [LANGUAGE]. Do not change any other aspect of the image.
```

This preserves typography, positioning, spacing and hierarchy — it only translates the text.
