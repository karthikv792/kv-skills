<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-Plugin-blueviolet?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSJub25lIiBzdHJva2U9IndoaXRlIiBzdHJva2Utd2lkdGg9IjIiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCI+PHBhdGggZD0iTTEyIDJMNiAxMmw2IDEwIDYtMTBMMTIgMnoiLz48L3N2Zz4=" alt="Claude Code Plugin">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="MIT License">
  <img src="https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge" alt="Version 1.0.0">
</p>

<h1 align="center">
  KV Skills
</h1>

<p align="center">
  <strong>A collection of opinionated skills for Claude Code</strong><br>
  <em>Teaching Claude to do things with craft, not just correctness.</em>
</p>

<p align="center">
  <a href="#installation">Install</a> &bull;
  <a href="#skills">Skills</a> &bull;
  <a href="#how-it-works">How It Works</a> &bull;
  <a href="#adding-a-skill">Add a Skill</a> &bull;
  <a href="#contributing">Contributing</a>
</p>

---

## Installation

```bash
claude plugin add karthikv792/kv-skills
```

All skills are automatically available in every Claude Code session.

### Manual Installation

```bash
git clone git@github.com:karthikv792/kv-skills.git ~/.claude/plugins/kv-skills
```

## Skills

| Skill | Description | Details |
|-------|-------------|---------|
| **[Designer With Taste](skills/designer_with_taste/)** | Design philosophy distilled from 212 real-world principle sets. Makes Claude build interfaces with genuine taste — intentional hierarchy, purposeful color, accessible markup, and opinionated craft. | [README](skills/designer_with_taste/README.md) |

> More skills coming soon. Have an idea? [Open an issue](https://github.com/karthikv792/kv-skills/issues) or submit a PR.

## How It Works

Claude Code plugins extend Claude's capabilities through **skills** — structured knowledge documents that Claude reads before performing tasks.

```
┌─────────────────────────────────────────────────┐
│  You: "Build me a dashboard"                    │
│                                                 │
│  Claude detects: UI task                        │
│       ↓                                         │
│  Loads relevant skill(s) from kv-skills         │
│       ↓                                         │
│  Reads specialized references (dashboards,      │
│  dark mode, mobile, etc.)                       │
│       ↓                                         │
│  Builds with craft — not just correctness       │
└─────────────────────────────────────────────────┘
```

Each skill lives in `skills/<skill-name>/` and contains:

- **`SKILL.md`** — The core skill document Claude reads (required)
- **`README.md`** — Human-readable documentation for the skill
- **`references/`** — Deep-dive reference material loaded on demand
- **`assets/`**, **`templates/`** — Supporting files (CSS tokens, starter templates, etc.)

## Project Structure

```
kv-skills/
├── .claude-plugin/
│   └── plugin.json              # Plugin metadata
├── skills/
│   └── designer_with_taste/     # Design philosophy skill
│       ├── SKILL.md
│       ├── README.md
│       ├── references/          # 7 specialized reference files
│       ├── assets/              # Design token system
│       └── templates/           # HTML starter template
├── LICENSE
└── README.md                    # You are here
```

## Adding a Skill

Want to add a new skill to this collection? Here's the structure:

```bash
mkdir -p skills/your-skill-name
```

Create `skills/your-skill-name/SKILL.md` with YAML frontmatter:

```markdown
---
name: your-skill-name
description: Use when [specific triggering conditions and symptoms]
---

# Your Skill Name

Your skill content here...
```

Add a `README.md` in the same directory to document the skill for humans.

### Skill Guidelines

- **Name**: Use kebab-case with letters, numbers, and hyphens only
- **Description**: Start with "Use when..." — describe triggering conditions, not what the skill does
- **Content**: Focus on actionable knowledge — principles, checklists, patterns, code examples
- **References**: Put lengthy reference material in a `references/` subdirectory
- **Assets**: Include reusable templates, tokens, or tools in `assets/` or `templates/`

## Contributing

Contributions welcome!

1. Fork the repo
2. Create your skill in `skills/your-skill-name/`
3. Include both `SKILL.md` (for Claude) and `README.md` (for humans)
4. Submit a PR

### Improving Existing Skills

1. Add reference files to `skills/<skill-name>/references/`
2. Update the skill's `SKILL.md` reference table
3. Submit a PR with context on what domain you're covering

## License

[MIT](LICENSE) — use it, fork it, build something with taste.
