# Designer With Taste

A comprehensive design philosophy distilled from **212 real-world design principle sets** — Dieter Rams, Nielsen, Don Norman, Maeda, Apple, Google Material, GOV.UK, Airbnb, Spotify, Figma, and 202 others.

## What This Skill Does

When Claude Code loads this skill, every interface it builds gets the benefit of 212 design systems' collective wisdom. It transforms generic AI output into work with intentional hierarchy, purposeful color, and genuine craft.

### Before & After

**Without this skill:**
```
"Build me a dashboard"
→ Generic card grid, random spacing, no hierarchy,
  default component library look, no loading states
```

**With this skill:**
```
"Build me a dashboard"
→ KPI bar with trend indicators, intentional hierarchy,
  semantic color system, skeleton loading states,
  responsive breakpoints, accessible markup, dark mode support
```

## The 12 Pillars

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

## Specialized References

| Reference | When to Use |
|-----------|-------------|
| [`pillars.md`](references/pillars.md) | **Always.** Deep-dive into each of the 12 design pillars. |
| [`mobile.md`](references/mobile.md) | Touch targets, thumb zones, platform conventions (iOS/Android), responsive breakpoints. |
| [`dashboards.md`](references/dashboards.md) | KPI bars, chart selection, data tables, filter patterns, real-time monitoring. |
| [`dark-mode.md`](references/dark-mode.md) | Semantic token architecture, elevation through lightness, theme switching. |
| [`ai-interfaces.md`](references/ai-interfaces.md) | Chat UI, confidence indicators, streaming responses, generative output patterns. |
| [`anti-patterns.md`](references/anti-patterns.md) | The 30+ taste killers to avoid — gradient plague, shadow soup, div soup, and more. |
| [`sources.md`](references/sources.md) | Full list of all 212 principle sets with authors, for citation or deep-dive. |

## Included Assets

- **[`assets/tokens.css`](assets/tokens.css)** — A complete, production-ready CSS custom property system covering spacing, typography, color (light + dark), motion, elevation, and z-index
- **[`templates/component-starter.html`](templates/component-starter.html)** — A batteries-included HTML template with semantic markup, accessible patterns, responsive layout primitives, and example components

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

## File Structure

```
designer_with_taste/
├── SKILL.md                        # Core skill document
├── README.md                       # This file
├── references/
│   ├── pillars.md                  # The 12 pillars — full reference
│   ├── mobile.md                   # Mobile-specific design patterns
│   ├── dashboards.md               # Data visualization & dashboards
│   ├── dark-mode.md                # Theming & dark mode architecture
│   ├── ai-interfaces.md            # AI/ML interface patterns
│   ├── anti-patterns.md            # Common taste killers
│   └── sources.md                  # All 212 source principle sets
├── assets/
│   └── tokens.css                  # Complete design token system
└── templates/
    └── component-starter.html      # HTML starter template
```

## Sources

Synthesizes design wisdom from **212 principle sets** including:

> Dieter Rams, Jakob Nielsen, Don Norman, John Maeda, Ben Shneiderman, Bruce Tognazzini, Apple, Google Material Design, GOV.UK, NHS, Spotify, Airbnb, Figma, Atlassian, Salesforce, IBM, Microsoft Fluent, Adobe Spectrum, Ant Design, Inclusive Design Principles, WCAG, and 191 others.

Full list in [`references/sources.md`](references/sources.md).

---

*"Good design is as little design as possible." — Dieter Rams*
