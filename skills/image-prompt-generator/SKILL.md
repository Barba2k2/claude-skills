---
name: image-prompt-generator
description: Expert skill for crafting optimized prompts for OpenAI's GPT Image models (gpt-image-2). Covers generation and editing workflows across all major use cases. Trigger this skill whenever the user wants to create or edit images with AI — including logos, infographics, product photos, UI mockups, ads, photorealistic portraits, educational diagrams, pitch deck slides, style transfer, virtual try-on, compositing, comic strips, children's book illustrations, collectible mockups, holiday cards, interior design swaps, and image text translation. Also trigger on phrases like "generate an image of", "create a prompt for", "make a logo in ChatGPT", "how do I ask AI to generate X", or any request about creating visuals with AI.
---

# Image Prompt Generator

Skill for generating structured and optimized prompts for OpenAI's GPT Image models, based on the official gpt-image-2 prompting guide.

## Usage Flow

1. **Identify the mode** (generation or editing — see below)
2. **Identify the image type** from the index
3. **Read the corresponding reference file**
4. **Ask elicitation questions** specific to that type
5. **Generate the final prompt** + recommended parameters

---

## Mode: Generation vs. Editing

**First of all, identify the mode:**

| Mode | When to use | What the user needs |
|---|---|---|
| **Generation** (text → image) | Create something from scratch, without a reference image | Nothing — just the prompt |
| **Editing** (text + image → image) | Modify, combine or transform an existing image | One or more input images |

> If the user has no input image → **Generation**
> If the user wants to change/combine images they already have → **Editing**

---

## Full Index — which file to read

### 🟢 Generation (text → image)

| Use Case | Image type | File |
|---|---|---|
| 4.1 | Infographic, diagram, timeline, explanatory poster | `references/infographic.md` |
| 4.3 | Realistic photo, portrait, photographic scene | `references/photorealism.md` |
| 4.4 | Historical scenes or with world knowledge | `references/photorealism.md` |
| 4.5 | Logo, brand, visual identity | `references/logo.md` |
| 4.6 | Ad, campaign, creative marketing | `references/ads.md` |
| 4.7 | Comic strip, panel narrative | `references/comic.md` |
| 4.8 | UI mockup, app screen, interface | `references/ui-mockup.md` |
| 4.9 / 4.10 | Educational, scientific visual, slide, pitch deck | `references/educational.md` |
| 6.2 | 3D holiday card | `references/additional-use-cases.md` |
| 6.3 | Collectible, action figure, merch concept | `references/additional-use-cases.md` |

### 🔵 Editing (text + image → image)

| Use Case | What to do | File |
|---|---|---|
| 4.2 | Translate text in an image to another language | `references/translation.md` |
| 5.1 | Apply the style of one image to another | `references/editing.md` |
| 5.2 | Change a person's outfit (virtual try-on) | `references/editing.md` |
| 5.3 | Transform a drawing/sketch into a realistic photo | `references/editing.md` |
| 5.4 | Extract product with clean background (packshot) | `references/product.md` |
| 5.5 | Place product in a scene with marketing copy | `references/ads.md` |
| 5.6 | Change lighting, weather or time of day | `references/editing.md` |
| 5.7 | Remove an object from a photo | `references/editing.md` |
| 5.8 | Insert a person into a different scene | `references/editing.md` |
| 5.9 | Combine elements from multiple images | `references/editing.md` |
| 6.1 | Swap furniture/decor in a room photo | `references/additional-use-cases.md` |
| 6.4 | Children's book with consistent character | `references/additional-use-cases.md` |

### ⚙️ Parameters and models

| Question | File |
|---|---|
| Which model to use, sizes, quality settings | `references/models.md` |
| General prompting principles | `references/fundamentals.md` |

---

## Universal elicitation questions

If the type is not yet clear, ask **at most 2 questions**:

1. **What do you want to create/modify?** (main object, scene or concept)
2. **Do you have a reference image to use as a base?** (determines whether it's generation or editing)

After identifying the type → read the correct file and ask the specific questions from there.

---

## Default output

Always deliver the result in this format:

```
📋 PROMPT
[full prompt here]

⚙️ RECOMMENDED PARAMETERS
- Model: gpt-image-2
- Mode: Generation / Editing
- Size: [e.g. 1024x1536]
- Quality: [low / medium / high]

💡 TIP
[short and relevant observation about this image type, if any]
```

---

## General principles (always apply)

Read `references/fundamentals.md` if you need guidance on prompt structure, specificity, composition, text in images, or iteration. For most cases, the specific files already have everything needed.
