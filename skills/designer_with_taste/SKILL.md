---
name: designer_with_taste
description: >
  A comprehensive design philosophy skill distilled from 212 real-world design principle sets 
  (principles.design). Use this skill whenever creating any visual interface, UI component, 
  web page, application, dashboard, landing page, presentation, or design system. Also trigger 
  when the user asks to "make it look good", "improve the design", "add polish", requests 
  "beautiful UI", "professional design", or mentions aesthetics, UX, layout, typography, color, 
  spacing, visual hierarchy, or user experience. Apply even when users don't explicitly ask for 
  design — good design should be the default. Also use for mobile apps, dashboards, data 
  visualization, dark mode theming, and AI/ML interfaces. This skill transforms code generation 
  into design with genuine taste and opinionated craft.
---

# Designer With Taste

Design philosophy distilled from **212 real-world design principle sets** — Dieter Rams, Nielsen, 
Don Norman, Maeda, Apple, Google Material, GOV.UK, Airbnb, Spotify, Figma, and 202 others.

## Reference Files

Read the relevant reference file(s) BEFORE designing. Multiple files may apply.

| File | When to Read |
|---|---|
| `references/pillars.md` | **Always.** The 12 core design pillars — hierarchy, consistency, feedback, accessibility, content, typography, color, motion, errors, control, context, iteration. |
| `references/mobile.md` | Building mobile interfaces, responsive layouts, touch interactions, native app design. |
| `references/dashboards.md` | Data visualization, analytics dashboards, charts, tables, metrics displays, admin panels. |
| `references/dark-mode.md` | Dark/light theming, color systems, dynamic themes, system preference detection. |
| `references/ai-interfaces.md` | AI-powered features, chat interfaces, generative UI, ML model outputs, conversational design. |
| `references/anti-patterns.md` | Review after a first draft to check for taste killers and common mistakes. |
| `references/sources.md` | Full list of all 212 principle sets with authors, for citation or deep-dive. |

## Quick-Reference: Design Token Starter

Use `assets/tokens.css` as a starting point for any new interface. It contains a complete 
design token system (spacing, type, color, motion, elevation) ready to import.

Use `templates/component-starter.html` for a batteries-included HTML starter with semantic 
markup, accessible patterns, and the token system pre-loaded.

---

## I. THE FOUNDATIONAL STANCE

Before any pixel or line of code, internalize these four meta-principles that recur across 
virtually all 212 sources:

### 1. Design is for people, not screens
UX starts and ends with people (Erik Dahl). You're designing an experience that helps someone 
accomplish something meaningful (Joshua Porter). Talk to users, watch them, have empathy. What 
they ask for isn't always what they need (GOV.UK).

### 2. Every decision needs a rationale
"Because it's trendy" is never good enough (UX Axioms). Every element, color, animation, and 
word must earn its place. If you can't articulate why something exists, remove it. Dieter Rams: 
concentrate on the essential.

### 3. Simplicity is the hardest work
Making something look simple is easy. Making something simple to *use* is much harder (GOV.UK). 
Simplicity is subtracting the obvious and adding the meaningful (John Maeda). Don't push 
complexity onto users — absorb it yourself.

### 4. Taste is pattern recognition plus courage
Taste means knowing when to follow convention (consistency builds trust) and when to break it 
(differentiation creates delight). Have strong opinions, hold them loosely, validate with humans.

---

## II. THE 12 PILLARS — QUICK REFERENCE

Full details in `references/pillars.md`. Here's the cheat sheet:

### PILLAR 1: Hierarchy & Focus
One primary action per screen. Visual hierarchy is the skeleton. Eliminate before organizing. 
Progressive disclosure. *(Whitney Hess, Degreed, Apple, Nielsen)*

### PILLAR 2: Consistency & Familiarity
Internal consistency (same action = same result). External consistency (respect platform norms). 
Be consistent, not uniform (GOV.UK). Design systems are lego boxes. *(Don Norman, Spotify, Atlassian)*

### PILLAR 3: Feedback & Responsiveness
Every action gets a response. Show system status always. Motion communicates relationships. 
UIs are conversations — close feedback loops. *(Shneiderman, Apple, Material Design, Nielsen)*

### PILLAR 4: Accessibility & Inclusion
Design for the full spectrum — permanent, temporary, situational disabilities. Provide 
comparable experiences. Don't sacrifice clarity for elegance. *(WCAG, Paciello Group, GOV.UK, NHS)*

**Non-negotiable minimums:**
- 4.5:1 contrast ratio for text
- Keyboard navigable, visible focus indicators
- Semantic HTML (headings, landmarks, buttons)
- 16px minimum body text, 1.5 line-height
- `prefers-reduced-motion` respected
- Screen-reader tested

### PILLAR 5: Content & Language
Use the user's language, not jargon. Content-first design (real text, not lorem ipsum). Tone 
is interface. Error messages: what happened + why + how to fix. *(NHS, GOV.UK, Bristol Council)*

### PILLAR 6: Typography & Visual Craft
Typography creates hierarchy without effort. Choose fonts with character. Consistent grid + 
baseline. White space is structure, not emptiness. *(Material Design, Edenspiekermann, Apple)*

**Type system:**
```
Display:  32-48px bold     |  Subtitle: 18-20px medium
Title:    24-28px semibold  |  Body:     16px regular, 1.5lh
Caption:  13-14px regular   |  Overline: 11-12px uppercase
```

**Spacing scale (8px base):**  
`4 | 8 | 12 | 16 | 24 | 32 | 48 | 64 | 96 | 128`

### PILLAR 7: Color & Emotion
Every color serves a function. Dominant + accent beats even distribution. Design for emotion. 
Support both dark and light themes. *(Rams, MUJI, UX Axioms, Schlatter)*

### PILLAR 8: Motion & Delight
Motion explains relationships, not decorates. One orchestrated moment > scattered micro-interactions. 
Physics, not math (ease curves, springs). *(Material Design, Calm Technology, Apple)*

**Timing:** Micro: 100-150ms | Small: 200-250ms | Medium: 300-400ms | Large: 400-600ms

### PILLAR 9: Error Prevention & Recovery
Prevent > Guide > Catch > Explain > Recover > Forgive. Undo is sacred. Break error-prone tasks 
into smaller steps. *(Nielsen, Shneiderman, Sandi Wassmer)*

### PILLAR 10: User Control & Autonomy
Users are the pilot, not passengers. Support undo/redo/escape. Let users customize. Do one 
thing well. *(Apple, Nielsen, UNIX Philosophy, Inclusive Design)*

### PILLAR 11: Context & Environment
Context drives usage. Respect the periphery. Design for the full journey. Responsive means 
adaptive, not shrunk. *(GOV.UK, Calm Technology, Whitney Hess)*

### PILLAR 12: Iteration & Humility
Start small, iterate wildly. Data over hunches. Observe behavior, not opinions. Don't be afraid 
to scrap it. *(GOV.UK, Lean Startup, d.school)*

---

## III. THE TASTE TEST

Run these checks before declaring any design done:

| Test | Question |
|---|---|
| **5-Second** | Show someone for 5 seconds — can they say what it's for? |
| **Squint** | Blur your eyes — is hierarchy visible? |
| **Parent** | Could a non-technical person find the primary action? |
| **Deletion** | Remove an element — does the design improve? |
| **Dark Room** | Does it survive in dark mode? |
| **Slow Connection** | Does it handle 3-second delays gracefully? |
| **Keyboard** | Can you navigate fully with Tab/Enter/Escape/Arrows? |
| **"So What"** | For every element — why should the user care? |

---

## IV. INTERACTIVE ELEMENT STATE CHECKLIST

Every interactive element must define ALL of these states:

```
:hover        → subtle lift (desktop only)
:active       → pressed feedback (<100ms)
:focus-visible → 2px outline, offset 2px (keyboard navigation)
:disabled     → 0.5 opacity, not-allowed cursor
[loading]     → skeleton / spinner / progress
[success]     → confirmation
[error]       → specific, kind message
```

---

## V. SEMANTIC HTML SKELETON

```html
<header>
  <nav aria-label="Main">...</nav>
</header>
<main>
  <article>
    <section aria-labelledby="section-heading">
      <h2 id="section-heading">...</h2>
    </section>
  </article>
</main>
<aside aria-label="Sidebar">...</aside>
<footer>...</footer>
```

Never: `<div class="button">` — Always: `<button type="button">`  
Never: `<div class="header">` — Always: `<header>`  
Never: `<span onclick>` — Always: `<a href>` or `<button>`

---

## VI. CSS SYSTEM PATTERN

```css
:root {
  /* Spacing */
  --space-xs: 4px; --space-sm: 8px; --space-md: 16px;
  --space-lg: 24px; --space-xl: 32px; --space-2xl: 48px;
  /* Type */
  --text-sm: 0.875rem; --text-base: 1rem; --text-lg: 1.125rem;
  --text-xl: 1.25rem; --text-2xl: 1.5rem; --text-3xl: 2rem;
  /* Color: semantic names */
  --surface: #fafafa; --surface-raised: #fff;
  --text-1: #1a1a1a; --text-2: #6b6b6b; --text-3: #9b9b9b;
  --accent: #2563eb; --accent-hover: #1d4ed8;
  --error: #dc2626; --success: #16a34a; --warning: #d97706;
  /* Motion */
  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
  --duration-fast: 150ms; --duration-base: 250ms;
}
```

Use ONLY system values. No arbitrary numbers. This is the foundation of taste in code.

---

## FINAL WORD

The 212 principle sets disagree on many things. They all agree on this: **design is an act of 
care.** Care for the person using what you make. That care, applied consistently and 
courageously, is what produces work with taste.

> Good design is as little design as possible. — Dieter Rams
