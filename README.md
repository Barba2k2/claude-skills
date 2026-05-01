# Claude Skills Marketplace

> A curated, open registry of skills for [Claude Code](https://claude.ai/code).  
> Install any skill directly from the command line.

---

## How to install a skill

```bash
claude skill install <repo>
```

Example:

```bash
claude skill install Barba2k2/image-geneartor-gpt-image-2
```

---

## Skills

| Skill | Description | Tags | Install |
|---|---|---|---|
| [image-prompt-generator](skills/image-prompt-generator/SKILL.md) | Expert skill for crafting optimized prompts for OpenAI's GPT Image models (gpt-image-2). Covers generation and editing: logos, infographics, product photos, UI mockups, ads, photorealistic portraits, educational diagrams, pitch deck slides, style transfer, virtual try-on, comic strips, and more. | `images` `ai` `prompts` `design` `marketing` | `claude skill install Barba2k2/claude-skills/skills/image-prompt-generator` |

---

## Submit a skill

Want to add your skill to this registry?

1. Fork this repo
2. Add your skill to `registry.json` following the existing format
3. Open a Pull Request

### registry.json format

```json
{
  "name": "your-skill-name",
  "description": "What your skill does (1-2 sentences)",
  "repo": "github-username/repo-name",
  "branch": "main",
  "version": "1.0.0",
  "tags": ["tag1", "tag2"],
  "author": "github-username",
  "install": "claude skill install github-username/repo-name"
}
```

### Skill requirements

- Must have a `SKILL.md` at the root of the repository
- `SKILL.md` must include a valid frontmatter block with `name` and `description`
- Must be in English
- Must be original content

---

## Browse by tag

`images` · `ai` · `prompts` · `design` · `marketing`

---

<sub>Open registry — contributions welcome via Pull Request.</sub>
