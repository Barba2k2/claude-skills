# Image Editing — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Sections 5.1 to 5.9

## When to use this guide

Style transfer, virtual try-on (clothing swap), sketch to photo, compositing, object removal, inserting a person into a scene, lighting/weather transformation, multiple inputs.

> **Important:** All cases here use the **editing** function (edit), not generation — you need one or more input images.

---

## Quick index

| What you want to do                      | Section                    |
| ---------------------------------------- | -------------------------- |
| Apply the style of one image to another  | Style Transfer             |
| Swap a person's clothing                 | Virtual Try-On             |
| Turn a drawing into a realistic photo    | Sketch → Photo             |
| Remove an object from a photo            | Object Removal             |
| Insert a person into a different scene   | Person in Scene            |
| Combine elements from two images         | Compositing                |
| Change lighting, weather, or time of day | Environment Transformation |

---

## Style Transfer

> "Describe what must stay consistent (style cues) and what must change (new content), and add hard constraints like background, framing, and 'no extra elements' to prevent drift."

```
Use the same style from the input image and generate [NEW SUBJECT/SCENE DESCRIPTION — e.g.: a man riding a motorcycle] on a [BACKGROUND — e.g.: white background].
```

### Real example from the documentation

```
Use the same style from the input image and generate a man riding a motorcycle on a white background.
```

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## Virtual Try-On (Clothing Swap)

> "Explicitly lock the person (face, body shape, pose, hair, expression) and allow changes only to garments, then require realistic fit (draping, folds, occlusion) plus consistent lighting/shadows."

```
Edit the image to dress the [person] using the provided clothing images. Do not change [his/her] face, facial features, skin tone, body shape, pose, or identity in any way. Preserve [his/her] exact likeness, expression, hairstyle, and proportions. Replace only the clothing, fitting the garments naturally to [his/her] existing pose and body geometry with realistic fabric behavior. Match lighting, shadows, and color temperature to the original photo so the outfit integrates photorealistically, without looking pasted on. Do not change the background, camera angle, framing, or image quality, and do not add accessories, text, logos, or watermarks.
```

> Use multiple input images: 1 photo of the person + photos of each clothing item.

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## Sketch → Realistic Photo (Rendering)

> "Treat the prompt like a spec: preserve layout and perspective, then add realism by specifying plausible materials, lighting, and environment. Include 'do not add new elements/text' to avoid creative reinterpretations."

```
Turn this drawing into a photorealistic image.
Preserve the exact layout, proportions, and perspective.
Choose realistic materials and lighting consistent with the sketch intent.
Do not add new elements or text.
```

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## Object Removal

```
Remove the [OBJECT — e.g.: flower from man's hand]. Do not change anything else.
```

### Real example from the documentation

```
Remove the flower from man's hand. Do not change anything else.
```

> For removals with greater fidelity to the original, use `input_fidelity: high` (available in gpt-image-1.5).

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## Inserting a Person into a Scene

> "Anchor realism by specifying a grounded photographic look (natural lighting, believable detail, no cinematic grading), and lock what must not change about the subject."

```
Generate a highly realistic [SCENE TYPE — e.g.: action scene] where this person is [ACTION — e.g.: running away from a large, realistic brown bear attacking a campsite]. The image should look like a real photograph someone could have taken, not an overly enhanced or cinematic movie-poster image.
[PERSON DESCRIPTION — e.g.: She is centered in the image but looking away from the camera, wearing outdoorsy camping attire, with dirt on her face and tears in her clothing].
The [ENVIRONMENT — e.g.: campsite is in Yosemite National Park, with believable natural details]. The time of day is [TIME — e.g.: dusk], with natural lighting and realistic colors. Everything should feel grounded, authentic, and unstyled, as if captured in a real moment. Avoid cinematic lighting, dramatic color grading, or stylized composition.
```

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## Compositing — Combining Elements from Multiple Images

> "Clearly specify what to transplant, where it should go, and what must remain unchanged, while matching lighting, perspective, scale, and shadows."

```
Place the [ELEMENT — e.g.: dog] from the [NUMBER — e.g.: second] image into the setting of image [NUMBER — e.g.: 1], [POSITIONING — e.g.: right next to the woman], use the same style of lighting, composition and background. Do not change anything else.
```

### Real example from the documentation

```
Place the dog from the second image into the setting of image 1, right next to the woman, use the same style of lighting, composition and background. Do not change anything else.
```

> Reference inputs by number and description: "Image 1: ...", "Image 2: ..."

**Parameters:** `size: 1024x1536` | `quality: medium`

---

## Environment Transformation (Lighting, Weather, Time of Day)

> "Change only environmental conditions—lighting direction/quality, shadows, atmosphere, precipitation, and ground wetness—while preserving identity, geometry, camera angle, and object placement."

```
Make it look like [NEW CONDITION — e.g.: a winter evening with snowfall / golden hour at sunset / a rainy night].
```

### Real example from the documentation

```
Make it look like a winter evening with snowfall.
```

> Use `input_fidelity: high` to maintain greater fidelity to the original during large environment edits (available in gpt-image-1.5).

**Parameters:** `size: keep the same as original` | `quality: medium`

---

## Interior Editing — Element Swap (Precision Edit)

> "Swap a single object while preserving camera angle, lighting, shadows, and surrounding context so the edit looks like a real photograph, not a redesign."

```
In this room photo, replace ONLY [ORIGINAL ELEMENT — e.g.: white chairs] with [NEW ELEMENT — e.g.: chairs made of wood].
Preserve camera angle, room lighting, floor shadows, and surrounding objects.
Keep all other aspects of the image unchanged.
Photorealistic contact shadows and [MATERIAL — e.g.: fabric] texture.
```

### Real example from the documentation (chair swap)

```
In this room photo, replace ONLY white with chairs made of wood.
Preserve camera angle, room lighting, floor shadows, and surrounding objects.
Keep all other aspects of the image unchanged.
Photorealistic contact shadows and fabric texture.
```

**Parameters:** `size: 1536x1024` | `quality: medium`

---

## Golden rule for edits

For every edit, always use this structure:

- **"Change only X"** — what should change
- **"Keep everything else the same"** — what should be preserved
- Repeat the preservation list in each iteration to avoid drift
