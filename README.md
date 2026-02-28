<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-Plugin-blueviolet?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSJub25lIiBzdHJva2U9IndoaXRlIiBzdHJva2Utd2lkdGg9IjIiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCI+PHBhdGggZD0iTTEyIDJMNiAxMmw2IDEwIDYtMTBMMTIgMnoiLz48L3N2Zz4=" alt="Claude Code Plugin">
  <img src="https://img.shields.io/badge/Design_Principles-212-orange?style=for-the-badge" alt="212 Design Principles">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="MIT License">
  <img src="https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge" alt="Version 1.0.0">
</p>

<h1 align="center">
  KV Skills
</h1>

<p align="center">
  <strong>Opinionated design skills for Claude Code</strong><br>
  <em>Distilled from 212 real-world design principle sets. Makes Claude build interfaces with genuine taste.</em>
</p>

<p align="center">
  <a href="#installation">Install</a> &bull;
  <a href="#whats-inside">What's Inside</a> &bull;
  <a href="#how-it-works">How It Works</a> &bull;
  <a href="#skills">Skills</a> &bull;
  <a href="#contributing">Contributing</a>
</p>

---

## The Problem

AI code generators build functional UIs, but they lack **taste**. You get correct HTML, valid CSS, accessible markup... and it all looks like every other AI-generated interface. Generic gradients, uniform border-radius, shadow soup, placeholder-as-label, the works.

**KV Skills fixes this.** It teaches Claude Code the design principles behind 212 of the world's best design systems — from Dieter Rams to Apple HIG, from GOV.UK to Spotify — so every interface it builds has intentional hierarchy, purposeful color, and genuine craft.

## Installation

```bash
claude plugin add karthikv792/kv-skills
```

That's it. The skills are automatically available in all your Claude Code sessions.

### Manual Installation

If you prefer to install manually:

```bash
git clone git@github.com:karthikv792/kv-skills.git ~/.claude/plugins/kv-skills
```

## What's Inside

```
kv-skills/
├── .claude-plugin/
│   └── plugin.json            # Plugin metadata
├── skills/
│   └── designer_with_taste/
│       ├── SKILL.md            # Core skill — the 12 pillars of design
│       ├── references/
│       │   ├── pillars.md      # Deep-dive into each design pillar
│       │   ├── mobile.md       # Mobile-specific design patterns
│       │   ├── dashboards.md   # Data viz & dashboard design
│       │   ├── dark-mode.md    # Theming architecture & dark mode
│       │   ├── ai-interfaces.md# AI/ML interface patterns
│       │   ├── anti-patterns.md# Common taste killers to avoid
│       │   └── sources.md      # All 212 source principle sets
│       ├── assets/
│       │   └── tokens.css      # Complete design token system
│       └── templates/
│           └── component-starter.html  # Batteries-included HTML starter
├── LICENSE
└── README.md
```

## How It Works

Claude Code plugins extend Claude's capabilities through **skills** — structured knowledge documents that Claude reads before performing tasks. When you ask Claude to build a UI, it will:

```
1. Detect the task involves visual interface design
2. Load the "designer_with_taste" skill automatically
3. Read the relevant reference files (mobile, dashboard, dark mode, etc.)
4. Apply the 12 design pillars to every decision
5. Use the design token system for consistent spacing, color, and typography
6. Run the "Taste Test" checklist before declaring the work done
```

### Before & After

**Without KV Skills:**
```
"Build me a dashboard"
→ Generic card grid, random spacing, no hierarchy,
  default component library look, no loading states
```

**With KV Skills:**
```
"Build me a dashboard"
→ KPI bar with trend indicators, intentional hierarchy,
  semantic color system, skeleton loading states,
  responsive breakpoints, accessible markup, dark mode support
```

## Skills

### Designer With Taste

The flagship skill. A comprehensive design philosophy distilled from **212 real-world design principle sets** — Dieter Rams, Nielsen, Don Norman, Maeda, Apple, Google Material, GOV.UK, Airbnb, Spotify, Figma, and 202 others.

#### The 12 Pillars

| # | Pillar | Core Idea |
|---|--------|-----------|
| 1 | **Hierarchy & Focus** | One primary action per screen. Eliminate before organizing. |
| 2 | **Consistency & Familiarity** | Design systems are lego boxes. Be consistent, not uniform. |
| 3 | **Feedback & Responsiveness** | Every action gets a response. Motion communicates relationships. |
| 4 | **Accessibility & Inclusion** | 4.5:1 contrast, keyboard nav, semantic HTML. Non-negotiable. |
| 5 | **Content & Language** | Use the user's language. Error messages: what + why + how to fix. |
| 6 | **Typography & Visual Craft** | Typography creates hierarchy without effort. White space is structure. |
| 7 | **Color & Emotion** | Every color serves a function. Dominant + accent beats even distribution. |
| 8 | **Motion & Delight** | Motion explains relationships, not decorates. Physics, not math. |
| 9 | **Error Prevention & Recovery** | Prevent > Guide > Catch > Explain > Recover > Forgive. |
| 10 | **User Control & Autonomy** | Users are the pilot, not passengers. Undo is sacred. |
| 11 | **Context & Environment** | Responsive means adaptive, not shrunk. |
| 12 | **Iteration & Humility** | Data over hunches. Don't be afraid to scrap it. |

#### Specialized References

| Reference | Use Case |
|-----------|----------|
| **Mobile** | Touch targets, thumb zones, platform conventions (iOS/Android), responsive breakpoints |
| **Dashboards** | KPI bars, chart selection, data tables, filter patterns, real-time monitoring |
| **Dark Mode** | Semantic token architecture, elevation through lightness, theme switching |
| **AI Interfaces** | Chat UI, confidence indicators, streaming responses, generative output patterns |
| **Anti-Patterns** | The 30+ taste killers to avoid — gradient plague, shadow soup, div soup, and more |

#### Included Assets

- **`tokens.css`** — A complete, production-ready CSS custom property system covering spacing, typography, color (light + dark), motion, elevation, and z-index
- **`component-starter.html`** — A batteries-included HTML template with semantic markup, accessible patterns, responsive layout primitives, and example components

## The Taste Test

Every interface built with this skill gets checked against these gates:

| Test | Question |
|------|----------|
| **5-Second** | Show someone for 5 seconds — can they say what it's for? |
| **Squint** | Blur your eyes — is hierarchy visible? |
| **Parent** | Could a non-technical person find the primary action? |
| **Deletion** | Remove an element — does the design improve? |
| **Dark Room** | Does it survive in dark mode? |
| **Slow Connection** | Does it handle 3-second delays gracefully? |
| **Keyboard** | Can you navigate fully with Tab/Enter/Escape/Arrows? |
| **"So What"** | For every element — why should the user care? |

## Contributing

Contributions welcome! If you have design skills, patterns, or specialized references to add:

1. Fork the repo
2. Create a new skill in `skills/your-skill-name/SKILL.md`
3. Follow the [SKILL.md structure](https://docs.anthropic.com/en/docs/claude-code/skills) with YAML frontmatter
4. Submit a PR

### Adding References to Existing Skills

If you want to add a reference to `designer_with_taste`:

1. Add your reference file to `skills/designer_with_taste/references/`
2. Update the reference table in `SKILL.md`
3. Submit a PR with context on the design domain covered

## Sources

This skill synthesizes design wisdom from **212 principle sets** including:

> Dieter Rams, Jakob Nielsen, Don Norman, John Maeda, Ben Shneiderman, Bruce Tognazzini, Apple, Google Material Design, GOV.UK, NHS, Spotify, Airbnb, Figma, Atlassian, Salesforce, IBM, Microsoft Fluent, Adobe Spectrum, Ant Design, Inclusive Design Principles, WCAG, and 191 others.

Full list in [`skills/designer_with_taste/references/sources.md`](skills/designer_with_taste/references/sources.md).

## License

[MIT](LICENSE) — use it, fork it, make beautiful things.

---

<p align="center">
  <em>"Good design is as little design as possible." — Dieter Rams</em>
</p>
