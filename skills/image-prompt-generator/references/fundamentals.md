# Prompting Fundamentals — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide

## Structure of a good prompt

Always write prompts in this order:
**background/scene → subject → key details → constraints**

Include the intended use (ad, UI mock, infographic) to set the "mode" and polish level.

For complex requests, use short segments with labels or line breaks instead of a long paragraph.

---

## Prompt format

Works well: minimal prompts, descriptive paragraphs, instruction style, tag structure. What matters is that the intent and constraints are clear. In production, prioritize a readable template over elaborate syntax.

---

## Specificity and quality

- Be concrete about materials, shapes, textures and the visual medium (photo, watercolor, 3D render)
- Add "quality levers" only when necessary: _film grain_, _textured brushstrokes_, _macro detail_
- For photorealism: include the word **"photorealistic"** directly in the prompt
- Phrases like _"real photograph"_, _"taken on a real camera"_, _"professional photography"_, _"iPhone photo"_ also help
- Technical camera specs can be interpreted broadly — use mainly for overall look and composition

---

## Composition

- Specify framing and point of view: close-up, wide, top-down
- Perspective/angle: eye-level, low-angle
- Lighting/mood: soft diffuse, golden hour, high-contrast
- If layout matters, declare positioning: "logo top-right", "subject centered with negative space on left"
- For wide, cinematic, low-light, rain or neon scenes: add extra details about scale, atmosphere and color

---

## People, pose and action

For people in scenes, describe:

- Body scale and framing: "full body visible, feet included"
- Relative size: "child-sized relative to the table"
- Gaze direction: "looking down at the open book, not at the camera"
- Interaction with objects: "hands naturally gripping the handlebars"

These details help with body proportions, action geometry and gaze alignment.

---

## Constraints — what to change vs. preserve

- Explicitly declare exclusions and invariants: "no watermark", "no extra text", "no logos/trademarks", "preserve identity/geometry/layout/brand elements"
- For edits: use "change only X" + "keep everything else the same"
- Repeat the preservation list on each iteration to reduce drift
- For surgical edits: also say not to alter saturation, contrast, layout, arrows, labels, camera angle or surrounding objects

---

## Text in images

- Put the literal text **in quotes** or in **ALL CAPS**
- Specify typography: font style, size, color, positioning
- For difficult words (brand names, unusual spellings): spell it out letter by letter
- Use `quality: medium` or `high` for small text, dense information panels, multi-font layouts

---

## Multiple input images (editing)

- Reference each input by **index and description**: "Image 1: product photo… Image 2: style reference…"
- Describe how they interact: "apply Image 2's style to Image 1"
- For compositing: be explicit about what goes where: "put the bird from Image 1 on the elephant in Image 2"

---

## Iterate instead of overloading

- Long prompts can work, but it's easier to debug starting with a clean base prompt and refining with small changes: "make lighting warmer", "remove the extra tree", "restore the original background"
- Use references like "same style as before" or "the subject" to leverage context
- But re-specify critical details if they start to drift

---

## Latency vs. fidelity

| Situation                                                                                                 | Recommended Quality |
| --------------------------------------------------------------------------------------------------------- | ------------------- |
| High volume, experimentation, drafts                                                                      | `low`               |
| General use, most cases                                                                                   | `medium`            |
| Small or dense text, detailed infographics, close-up portraits, identity-sensitive edits, high resolution | `high`              |
