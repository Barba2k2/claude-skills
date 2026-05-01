# Photorealism — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Sections 4.3 and 4.4

## When to use this guide

Realistic photos, portraits, photographic scenes, people in environments, "captured in the moment" style photos, world knowledge scenes.

---

## Key principles (from the official documentation)

> "To get believable photorealism, prompt the model as if a real photo is being captured in the moment. Use photography language (lens, lighting, framing) and explicitly ask for real texture (pores, wrinkles, fabric wear, imperfections). Avoid words that imply studio polish or staging."

- Write the prompt as if a real photo is being taken
- Use photography language: lens, lighting, framing
- Ask for **real textures**: pores, wrinkles, fabric wear, imperfections
- Avoid words that suggest studio polish or artificial staging
- Use `quality: high` when detail matters
- Include the word **"photorealistic"** directly in the prompt to activate the model's photorealistic mode
- Phrases like _"real photograph"_, _"taken on a real camera"_, _"professional photography"_, _"iPhone photo"_ also help

---

## Elicitation — questions to ask

1. **Main subject** (who or what is in the photo?)
2. **Environment/scene** (where is it? type of place, time of day)
3. **Framing** (close-up, medium shot, full body, wide?)
4. **Photographic style** (candid/spontaneous, editorial, documentary, iPhone, 35mm film?)
5. **Action or pose** (what is the person/object doing?)
6. **Mood/lighting** (natural light, golden hour, diffuse light, nighttime?)

---

## Prompt template

```
Create a photorealistic [TYPE — e.g.: candid photograph / portrait / scene] of [MAIN SUBJECT].
[PHYSICAL DETAILS — e.g.: weathered skin with visible wrinkles, pores, and sun texture].
[ACTION/POSE — e.g.: calmly adjusting a net while his dog sits nearby on the deck].
Shot like a [STYLE — e.g.: 35mm film photograph], [FRAMING — e.g.: medium close-up at eye level], using a [LENS — e.g.: 50mm lens].
[LIGHTING — e.g.: Soft coastal daylight], [DEPTH — e.g.: shallow depth of field], [TEXTURE — e.g.: subtle film grain], [COLOR — e.g.: natural color balance].
The image should feel [MOOD — e.g.: honest and unposed], with real skin texture, worn materials, and everyday detail.
No glamorization, no heavy retouching.
```

### Real example from the documentation (sailor)

```
Create a photorealistic candid photograph of an elderly sailor standing on a small fishing boat.
He has weathered skin with visible wrinkles, pores, and sun texture, and a few faded traditional sailor tattoos on his arms.
He is calmly adjusting a net while his dog sits nearby on the deck. Shot like a 35mm film photograph, medium close-up at eye level, using a 50mm lens.
Soft coastal daylight, shallow depth of field, subtle film grain, natural color balance.
The image should feel honest and unposed, with real skin texture, worn materials, and everyday detail. No glamorization, no heavy retouching.
```

---

## World Knowledge — historical and contextual scenes

gpt-image-2 has world knowledge and can infer context. For example: when asking for a scene in Bethel, New York, in August 1969, it infers Woodstock without needing to be told explicitly.

### Prompt template — World Knowledge

```
Create a realistic [SCENE TYPE — e.g.: outdoor crowd scene] in [LOCATION], on [DATE].
Photorealistic, period-accurate [ELEMENTS — e.g.: clothing, staging, and environment].
```

### Real example from the documentation (Woodstock)

```
Create a realistic outdoor crowd scene in Bethel, New York on August 16, 1969.
Photorealistic, period-accurate clothing, staging, and environment.
```

---

## Recommended parameters

- **Model:** `gpt-image-2`
- **Size:** `1024x1536` (portrait/vertical) or `1536x1024` (landscape/horizontal)
- **Quality:** `medium` for general use; `high` for face close-ups or when skin texture is critical

---

## Additional tips

- For **people in action**: describe scale, body framing, gaze direction and object interaction — "full body visible, feet included", "looking down at the open book, not at the camera"
- For **cinematic scenes, low-light, rain or neon**: add extra details about scale, atmosphere and color — the model tends to swap mood for superficial realism without guidance
- For **portraits**: specify whether the person looks at the camera or not — the default is usually looking at the camera
