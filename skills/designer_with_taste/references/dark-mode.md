# Dark Mode & Theming Design

Principles drawn from Material Design (dark theme guidance), Apple Human Interface Guidelines,
Android design principles, Microsoft Fluent, Ant Design, Spotify, Figma, and the
color/emotion principles across all 212 principle sets.

---

## Core Theming Philosophy

Dark mode is not "invert the colors." It is a complete re-expression of your visual hierarchy,
emotion, and depth system under different lighting assumptions. A good dark theme should feel
intentional — as if it were designed first — not like a filter applied to a light design.

---

## When Dark Mode Matters

```
Strong case for dark mode:
- Media-heavy apps (video, photo, music): dark backgrounds make content pop
- Developer tools / code editors: reduced glare during long sessions
- Evening / nighttime use: reduced eye strain and blue light
- OLED screens: true black saves battery and enables infinite contrast
- Entertainment / ambient: dashboard, kiosk, gaming contexts
- User expectation: users overwhelmingly expect theme choice

Dark mode is NOT ideal for:
- Long-form reading (studies show light backgrounds with dark text are
  more readable for extended text — though personal preference varies)
- Document editing (mismatch with printed output)
- But: always let the user choose. Preference overrides research.
```

---

## Architecture: Semantic Color Tokens

The foundation of good theming is **never using raw color values in components**. Instead, 
create a semantic token layer that maps to different values per theme.

### Three-Layer Color Architecture
```
Layer 1: Primitives (raw values)
  --blue-500: #2563eb;
  --gray-900: #1a1a1a;
  --gray-50:  #fafafa;

Layer 2: Semantic Tokens (meaning-based, theme-aware)
  --color-surface:         var(--gray-50);       /* light */
  --color-surface:         var(--gray-900);       /* dark */
  --color-text-primary:    var(--gray-900);       /* light */
  --color-text-primary:    var(--gray-50);        /* dark */
  --color-accent:          var(--blue-500);       /* same in both */

Layer 3: Component Tokens (specific usage)
  --button-bg:             var(--color-accent);
  --card-bg:               var(--color-surface-raised);
  --input-border:          var(--color-border);
```

### CSS Implementation
```css
/* Define primitives */
:root {
  --blue-500: #2563eb;
  --blue-400: #60a5fa;
  /* ... full primitive scale ... */
}

/* Light theme (default) */
:root, [data-theme="light"] {
  --surface-0: #ffffff;
  --surface-1: #f8f9fa;
  --surface-2: #f1f3f5;
  --surface-3: #e9ecef;
  
  --text-1: #1a1a2e;
  --text-2: #495057;
  --text-3: #868e96;
  
  --border: #dee2e6;
  --border-subtle: #f1f3f5;
  
  --accent: var(--blue-500);
  --accent-text: #ffffff;
  --accent-hover: #1d4ed8;
  
  --shadow-color: 220 3% 15%;
  --shadow-sm: 0 1px 2px hsl(var(--shadow-color) / 0.08);
  --shadow-md: 0 4px 12px hsl(var(--shadow-color) / 0.12);
  --shadow-lg: 0 8px 24px hsl(var(--shadow-color) / 0.16);
}

/* Dark theme */
[data-theme="dark"] {
  --surface-0: #0f0f13;
  --surface-1: #1a1a23;
  --surface-2: #24242f;
  --surface-3: #2e2e3a;
  
  --text-1: #e8e8ed;
  --text-2: #a0a0b0;
  --text-3: #6b6b80;
  
  --border: #2e2e3a;
  --border-subtle: #1f1f2a;
  
  --accent: var(--blue-400);  /* lighter blue for dark bg */
  --accent-text: #0f0f13;
  --accent-hover: #93bbfd;
  
  --shadow-color: 220 40% 2%;
  --shadow-sm: 0 1px 3px hsl(var(--shadow-color) / 0.4);
  --shadow-md: 0 4px 16px hsl(var(--shadow-color) / 0.5);
  --shadow-lg: 0 8px 32px hsl(var(--shadow-color) / 0.6);
}
```

---

## Dark Mode Design Rules

### Surface & Elevation (Material Design Approach)
In light mode, elevation is expressed through shadows. In dark mode, **elevation is expressed 
through surface lightness** — higher elements are lighter.

```
Dark mode surface hierarchy:
Lowest (background):  #0f0f13  ← darkest
Level 1 (card):       #1a1a23
Level 2 (dialog):     #24242f  
Level 3 (tooltip):    #2e2e3a
Highest (dropdown):   #38384a  ← lightest

Each step: ~8-12% lighter than the previous
Shadows still apply but with much higher opacity (dark shadows on dark backgrounds
need more intensity to be visible)
```

### Text Contrast in Dark Mode
```
Light mode text hierarchy:
Primary:    #1a1a2e (very dark)      → 15:1 contrast on white
Secondary:  #495057 (medium)          → 7:1 contrast on white
Tertiary:   #868e96 (light)           → 4.5:1 contrast on white

Dark mode text hierarchy:
Primary:    #e8e8ed (very light)      → 14:1 contrast on #0f0f13
Secondary:  #a0a0b0 (medium)          → 7:1 contrast on #0f0f13
Tertiary:   #6b6b80 (muted)           → 4.5:1 contrast on #0f0f13

Rule: NEVER use pure white (#fff) on dark backgrounds. It creates excessive 
      contrast that causes eye strain. Max brightness: #e8e8ed or similar.
      Similarly, NEVER use pure black (#000) as dark background unless on 
      OLED where true black is deliberate.
```

### Color Adjustments for Dark Mode
Colors that work in light mode often need adjustment in dark mode:
```
Saturated colors:   Reduce saturation 10-20% to prevent vibrating on dark surfaces
Accent colors:      Use a lighter variant (blue-400 instead of blue-600)
Semantic green:     Use a more luminous green (#4ade80 not #16a34a)
Semantic red:       Use a warmer, lighter red (#f87171 not #dc2626)
Borders:            Use lighter borders (more visible) or glow instead of shadow
Images:             Consider reducing brightness/contrast slightly with a filter

/* Optional image adjustment for dark mode */
[data-theme="dark"] img:not([data-no-dim]) {
  filter: brightness(0.9) contrast(1.05);
}
```

---

## Theme Switching Implementation

### JavaScript Theme Toggle
```javascript
function setTheme(theme) {
  document.documentElement.setAttribute('data-theme', theme);
  localStorage.setItem('theme-preference', theme);
}

function getPreferredTheme() {
  const stored = localStorage.getItem('theme-preference');
  if (stored) return stored;
  return window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light';
}

// Initialize
setTheme(getPreferredTheme());

// Listen for system changes
window.matchMedia('(prefers-color-scheme: dark)')
  .addEventListener('change', (e) => {
    if (!localStorage.getItem('theme-preference')) {
      setTheme(e.matches ? 'dark' : 'light');
    }
  });
```

### CSS-Only System Preference Detection
```css
/* For apps without a toggle — pure system preference */
@media (prefers-color-scheme: dark) {
  :root {
    --surface-0: #0f0f13;
    --text-1: #e8e8ed;
    /* ... dark tokens ... */
  }
}
```

### Three-Way Toggle Pattern
Best practice: offer three options — Light, Dark, System.
```
[☀️ Light] [🌙 Dark] [💻 System]

"System" follows the OS preference. This respects user agency 
while providing a sensible default.
```

---

## Theme Transition Animation

Avoid a jarring flash when switching themes:
```css
/* Smooth theme transition */
[data-theme-transitioning] * {
  transition: background-color 300ms ease, color 200ms ease, 
              border-color 200ms ease, box-shadow 300ms ease !important;
}
```
Add the attribute before switching, remove after transition completes. Don't apply 
transitions permanently — it causes unintended animation on every state change.

---

## Advanced Theming Patterns

### Multiple Brand Themes
For white-label products or multi-brand systems:
```css
/* Brand A */
[data-brand="alpha"] {
  --accent: #e63946;
  --font-display: 'Space Grotesk', sans-serif;
  --radius: 8px;
}

/* Brand B */  
[data-brand="beta"] {
  --accent: #2a9d8f;
  --font-display: 'DM Sans', sans-serif;
  --radius: 4px;
}

/* Each brand × each theme = 4 combinations, all from tokens */
```

### High Contrast Mode
Respect `prefers-contrast: more`:
```css
@media (prefers-contrast: more) {
  :root {
    --text-2: var(--text-1);         /* Promote secondary text */
    --border: var(--text-3);          /* Stronger borders */
    --shadow-sm: none;                /* Remove subtle shadows */
    --surface-1: var(--surface-0);    /* Flatten elevation */
  }
}
```

### Dim / Night Mode
A third option between light and dark, popular in reading apps:
```css
[data-theme="dim"] {
  --surface-0: #1a1a2e;       /* Navy-ish, not pure dark */
  --surface-1: #22223a;
  --text-1: #c8c8d8;          /* Softer than full dark mode */
  --accent: #7c7cf0;          /* Muted accent */
}
```

---

## Common Dark Mode Mistakes

```
❌ Inverting all colors mechanically (filter: invert)
   → Breaks images, icons, semantic colors, brand identity

❌ Pure white text on pure black background  
   → Causes halation (text appears to bleed/glow), eye strain

❌ Same saturation levels as light mode
   → Saturated colors vibrate on dark backgrounds, causing strain

❌ Flat dark surfaces with no elevation distinction
   → Everything looks the same depth; hierarchy is destroyed

❌ Forgetting about images, illustrations, and media
   → Bright images blast the user's eyes in an otherwise dark UI

❌ Not testing in actual dark environments
   → Dark mode looks different at 2 AM in bed vs. a lit office

❌ Flash of wrong theme on page load (FOWT)
   → Set theme in <head> before any content renders, or use CSS-only approach
```

---

## Theming Design Checklist

```
□ Semantic color tokens (no raw hex in components)
□ Three-layer architecture (primitives → semantic → component)
□ Light theme: tested, polished, complete
□ Dark theme: designed independently (not just inverted)
□ Dark mode elevation: lighter surfaces = higher elevation
□ No pure white (#fff) text on dark backgrounds
□ No pure black (#000) backgrounds (unless deliberate OLED)
□ Accent colors adjusted for dark backgrounds (lighter variants)
□ Semantic colors (green/red/amber) tested in both themes
□ Shadows: increased opacity for dark mode
□ Images: considered brightness reduction or overlay
□ System preference (prefers-color-scheme) respected
□ Three-way toggle: Light / Dark / System
□ Theme persisted across sessions
□ No flash of wrong theme on load
□ Smooth transition between themes
□ High contrast mode (prefers-contrast) supported
□ All WCAG contrast ratios met in BOTH themes
□ Tested in actual dark environment (not just IDE preview)
```
