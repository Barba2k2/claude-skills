# Claude Skills Marketplace

> A curated, open registry of skills for [Claude Code](https://claude.ai/code).  
> Add this marketplace in Claude Code via `/plugins` → **Add Marketplace** → `Barba2k2/claude-skills`

---

## How to add this marketplace

1. Open Claude Code
2. Run `/plugins`
3. Select **Add Marketplace**
4. Enter: `Barba2k2/claude-skills`

---

## Skills

| Skill | Description | Tags |
|---|---|---|
| [image-prompt-generator](skills/image-prompt-generator/SKILL.md) | Expert skill for crafting optimized prompts for OpenAI's GPT Image models (gpt-image-2). Covers generation and editing: logos, infographics, product photos, UI mockups, ads, photorealistic portraits, educational diagrams, pitch deck slides, style transfer, virtual try-on, comic strips, and more. | `images` `ai` `prompts` `design` `marketing` |

---

## Submit a skill

Want to add your skill to this registry?

1. Fork this repo
2. Copy your skill into `skills/<your-skill-name>/` (must contain `SKILL.md`)
3. Add an entry to `registry.json`
4. Open a Pull Request

### Skill structure

```
skills/
└── your-skill-name/
    ├── SKILL.md          ← required (frontmatter: name, description)
    └── references/       ← optional supporting docs
```

### registry.json entry format

```json
{
  "name": "your-skill-name",
  "description": "What your skill does (1-2 sentences)",
  "path": "skills/your-skill-name",
  "version": "1.0.0",
  "tags": ["tag1", "tag2"],
  "author": "github-username"
}
```

### Skill requirements

- Must have a `SKILL.md` with valid frontmatter (`name` + `description`)
- Must be in English
- Must be original content

---

## Browse by tag

`images` · `ai` · `prompts` · `design` · `marketing`

---

<sub>Open registry — contributions welcome via Pull Request.</sub>
