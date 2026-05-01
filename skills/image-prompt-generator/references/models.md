# Models and Parameters — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide (April 2026)

## Summary of available models

| Model              | Available Quality       | Recommended use                                                                                                                              |
| ------------------ | ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `gpt-image-2`      | `low`, `medium`, `high` | **Recommended default** for new projects. Best overall quality, editing, text in image, photorealism, compositing, identity-sensitive edits. |
| `gpt-image-1.5`    | `low`, `medium`, `high` | Keep only for already validated workflows while migrating.                                                                                   |
| `gpt-image-1`      | `low`, `medium`, `high` | Legacy compatibility only.                                                                                                                   |
| `gpt-image-1-mini` | `low`, `medium`, `high` | When cost and volume are a priority: batch generation, rapid ideation, drafts.                                                               |

**General rule: always use `gpt-image-2`.**

---

## Available sizes in gpt-image-2

gpt-image-2 accepts any resolution as long as:

- Maximum side: less than `3840px`
- Both sides multiples of `16`
- Ratio between long and short side: maximum `3:1`
- Total pixels: between `655,360` and `8,294,400`
- Above `2560x1440` (2K): results may be more variable

### Popular sizes

| Label            | Resolution  | When to use                           |
| ---------------- | ----------- | ------------------------------------- |
| Square           | `1024x1024` | General default                       |
| HD Portrait      | `1024x1536` | Vertical — posts, stories, mobile     |
| HD Landscape     | `1536x1024` | Horizontal — banners, ads, thumbnails |
| Widescreen slide | `1536x864`  | Presentations, pitch decks            |
| 2K / QHD         | `2560x1440` | Recommended reliability limit         |

---

## When to use which quality

| Quality  | When to use                                                                                                                |
| -------- | -------------------------------------------------------------------------------------------------------------------------- |
| `low`    | High speed, high volume, experimentation, drafts. Good quality for many cases.                                             |
| `medium` | General use — best balance between speed and quality.                                                                      |
| `high`   | Small or dense text, detailed infographics, diagrams, close-up portraits, identity-sensitive edits, print or slide assets. |

---

## Golden rule by image type

| Type                 | Recommended size | Quality            |
| -------------------- | ---------------- | ------------------ |
| Logo                 | `1024x1536`      | `medium`           |
| Infographic          | `1024x1536`      | `medium` or `high` |
| Realistic photo      | `1024x1536`      | `medium`           |
| Ad (vertical)        | `1024x1536`      | `medium`           |
| UI mockup            | `1024x1536`      | `medium`           |
| Product photo        | `1024x1536`      | `medium`           |
| Slide / pitch deck   | `1536x864`       | `high`             |
| Scientific diagram   | `1536x1024`      | `high`             |
| Edit with dense text | any              | `high`             |
