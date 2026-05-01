# UI and Interface Mockups — GPT Image Models

> Source: OpenAI GPT Image Generation Models Prompting Guide — Section 4.8

## When to use this guide

Mobile app mockups, web app screens, product interfaces, visual wireframes, UI previews for presentations.

---

## Key principles (from the official documentation)

> "UI mockups work best when you describe the product as if it already exists. Focus on layout, hierarchy, spacing, and real interface elements, and avoid concept art language so the result looks like a usable, shipped interface rather than a design sketch."

- Describe the product as if it **already exists** and is live
- Focus on: layout, hierarchy, spacing, real interface elements
- Avoid concept art language — the result should look like a shipped interface, not a sketch
- Specify background, typography, colors and decoration
- Place the mockup **in a device frame** (iPhone, browser) for more realism
- Be practical: describe concrete sections (header, item list, highlight section, footer with info)

---

## Elicitation — questions to ask

1. **What type of app/product?** (mobile app, web dashboard, landing page, specific screen)
2. **What does the app do?** (main functionality)
3. **Which sections/elements should appear?** (e.g.: header, list, cards, navigation, form)
4. **Visual style** (e.g.: minimalist, colorful, dark mode, material design, native iOS)
5. **Device frame?** (iPhone, Android, MacBook, browser — or no frame)

---

## Prompt template

```
Create a realistic mobile app UI mockup for [APP TYPE — e.g.: a local farmers market].
Show [MAIN SCREEN — e.g.: today's market] with [COMPONENTS — e.g.: a simple header, a short list of vendors with small photos and categories, a small "Today's specials" section, and basic information for location and hours].
Design it to be [PRINCIPLES — e.g.: practical, and easy to use].
[VISUAL STYLE — e.g.: White background, subtle natural accent colors, clear typography, and minimal decoration].
It should look like a real, well-designed, beautiful app for [CONTEXT — e.g.: a small local market].
Place the UI mockup in an [FRAME — e.g.: iPhone frame].
```

### Real example from the documentation (farmers market app)

```
Create a realistic mobile app UI mockup for a local farmers market.
Show today's market with a simple header, a short list of vendors with small photos and categories, a small "Today's specials" section, and basic information for location and hours.
Design it to be practical, and easy to use. White background, subtle natural accent colors, clear typography, and minimal decoration.
It should look like a real, well-designed, beautiful app for a small local market.
Place the UI mockup in an iPhone frame.
```

---

## Recommended parameters

- **Model:** `gpt-image-2`
- **Size:** `1024x1536` (mobile/app) or `1536x1024` (web/dashboard)
- **Quality:** `medium`

---

## Additional tips

- **Describe real content**, not placeholders — vendor names, categories, fictitious but plausible hours make the mockup much more convincing
- For **web dashboards**: use `1536x1024` and describe columns, metrics, charts and side navigation
- For **dark mode**: explicitly specify "dark background, light text, high contrast"
- For **specific screens** (login, onboarding, checkout): describe the screen state — "user just added item to cart", "first-time user setup screen"
- Avoid asking for a "beautiful app" without specifying elements — the model needs hierarchy and concrete components to generate something usable
