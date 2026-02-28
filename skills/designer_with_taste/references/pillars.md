# The 12 Pillars of Design With Taste — Full Reference

Detailed implementation guidance for each pillar. Read SKILL.md first for the quick reference.

---

## PILLAR 1: HIERARCHY & FOCUS

**Sources**: Whitney Hess (20 Guiding Principles), Degreed, Apple iOS, Nielsen, Shneiderman, 
Joshua Porter, Digital Product Design Principles

The single most impactful design skill is controlling where attention goes.

- **One primary action per screen.** Guide users by focusing on one primary task. Be ruthless 
  with prioritization (Degreed). Every extra unit of information competes with the relevant 
  units and diminishes their visibility (Nielsen).
- **Visual hierarchy is the skeleton.** Size, color, contrast, position, proximity, and 
  whitespace create unmistakable reading order. The most important element should be obvious 
  within 0.5 seconds.
- **Eliminate, don't organize.** Before adding navigation to manage complexity, ask: can I 
  remove this entirely? The best interface element is one that doesn't exist.
- **Progressive disclosure.** Show only what's needed now. Reveal complexity as users demonstrate 
  readiness (Shneiderman, Nielsen).

### Implementation
```
1. Identify the ONE thing the user came to do
2. Make it visually dominant (largest, highest contrast, center of attention)
3. Everything else supports that one thing
4. If an element doesn't support the primary task, challenge its existence
5. Use whitespace aggressively — it's breathing room, not emptiness
```

---

## PILLAR 2: CONSISTENCY & FAMILIARITY

**Sources**: Don Norman, Nielsen (#4), Apple, GOV.UK, Spotify, Atlassian, Shneiderman, 
Android, IBM, Material Design, Ant Design

- **Internal consistency.** Same action = same result, everywhere. If a blue element navigates, 
  every blue tappable element should navigate (Don Norman).
- **External consistency.** Respect platform conventions. A hamburger menu contains navigation. 
  A trash icon deletes. Don't be clever where convention serves users better.
- **Be consistent, not uniform.** Every circumstance is different (GOV.UK). Consistency means 
  predictable, not identical. Spotify: "coherence" — everything feels reassuringly itself.
- **Design systems are lego boxes.** Pre-defined building blocks create consistent experiences 
  (Degreed). Start by reusing, not reinventing (Spotify).

### Implementation
```
- Type scale: 4-6 sizes max, stick to it
- Spacing scale: 4px or 8px base, use nothing else
- Color system: semantic names (primary, secondary, surface, error)
- Interaction patterns: define once (hover, focus, transitions)
- Component hierarchy: atoms → molecules → organisms
- Document the system, even if only for yourself
```

---

## PILLAR 3: FEEDBACK & RESPONSIVENESS

**Sources**: Shneiderman, Apple iOS, Material Design, Nielsen, Don Norman, IBM, Android, 
Weinschenk, Tognazzini

- **Every action gets a response.** Minor actions = modest response. Major actions = substantial 
  response (Shneiderman).
- **Show system status.** Users should always know what's happening (Nielsen #1). Progress 
  indicators, loading states, confirmations, errors are not optional.
- **Motion communicates.** Animation explains relationships, indicates state changes, maintains 
  spatial context (Material Design, Apple). Movement should feel physically plausible.
- **Feedback loops build confidence.** UIs are conversations — create and close feedback loops 
  (UX Axioms).

### Implementation
```
Every interactive element needs:
- Hover state (desktop): subtle color shift, shadow, or scale
- Active/pressed: immediate visual response (<100ms)
- Focus state: visible ring for keyboard navigation
- Loading: skeleton, spinner, or progress bar
- Success: confirmation of completion
- Error: clear, specific, kind
- Transitions: 150-300ms, ease-out entries, ease-in exits
```

---

## PILLAR 4: ACCESSIBILITY & INCLUSION

**Sources**: Inclusive Design Principles (Paciello Group), WCAG 2.0, GOV.UK, NHS, Sandi 
Wassmer, Design Council, Heydon Pickering, Wayfindr

This is not optional. Accessible design is good design.

- **Design for the full spectrum.** Permanent, temporary, situational, or changing disabilities 
  are not edge cases — they are everyone. A parent holding a baby, a person in sunlight, 
  someone with a broken arm — they all benefit.
- **Provide comparable experiences.** Different paths to the same goal are legitimate.
- **Don't sacrifice clarity for elegance.** If you must sacrifice elegance, so be it (GOV.UK). 
  Build for needs, not audiences.
- **Inclusive design celebrates diversity.** It doesn't attempt to meet every need, but 
  considering diversity achieves superior solutions for everyone (Design Council).

### Non-Negotiable Checklist
```
- Color contrast: 4.5:1 text, 3:1 large text
- Don't rely on color alone (add icons, text, patterns)
- All images: descriptive alt text
- Keyboard navigable: Tab/Enter/Space/Arrow for everything
- Visible focus indicators (high contrast)
- Semantic HTML: h1-h6, landmarks, lists, real <button>s
- Responsive: 320px to 4K
- Readable: 16px min body, 1.5 line-height, max 80ch
- Motion: respect prefers-reduced-motion
- Screen reader: does it make sense read aloud?
```

---

## PILLAR 5: CONTENT & LANGUAGE

**Sources**: Bristol Council, Co-op, NHS, GOV.UK, Voice Interface, Google Conversation, 
Degreed Digital Product Design

- **Use the user's language.** Not your internal jargon. Clarity first, personality second.
- **Don't make people think about words.** Labels should be self-evident. Error messages should 
  say what went wrong, where, and how to fix it (Sandi Wassmer).
- **Content-first design.** Start with real text, real data, real images. Design around truth, 
  not lorem ipsum.
- **Tone is interface.** How you say something matters as much as what. Design with compassion (NHS).

### Implementation
```
Headlines:  3-8 words, action-oriented or benefit-driven
Body:       Short paragraphs (2-4 sentences), scannable
CTAs:       Start with verb, be specific ("Save your work" not "Submit")
Errors:     [What happened] + [Why] + [How to fix] — never blame user
Labels:     Nouns for navigation, verbs for actions
Microcopy:  Helpful, warm, never condescending
Empty states: Guide toward first action, never blank
```

---

## PILLAR 6: TYPOGRAPHY & VISUAL CRAFT

**Sources**: Material Design, Apple, Rams, Edenspiekermann, Adobe Spectrum, Fluent, MUJI, 
Ant Design, Willem Sandberg

- **Typography creates hierarchy without effort.** A well-chosen type scale does more than 
  colors, borders, or icons.
- **Choose fonts with character.** Avoid defaults. Pick fonts with personality appropriate to 
  context — never sacrifice readability for style.
- **The grid is invisible architecture.** Consistent baseline grids and column systems create 
  rhythm and comfort.
- **White space is structure.** Don't eliminate space to save space. Use it for breathing room (IBM).

---

## PILLAR 7: COLOR & EMOTION

**Sources**: Material Design, Rams, Apple, MUJI, Mindfulness Everywhere, UX Axioms, 
Weinschenk, Schlatter

- **Every color serves a function.** Brand identity, state communication, hierarchy, atmosphere.
- **Dominant + accent > even distribution.** Strong neutral base with sharp accent colors.
- **Design for emotion.** Warm activates, cool calms, saturated energizes, muted reassures.
- **Support both themes.** Dark and light are both valid. Consider context.

### Color System Structure
```
Background:  1-2 neutrals (surface, elevated surface)
Text:        2-3 shades (primary, secondary, disabled)
Brand:       1 primary + 1 secondary
Accent:      1 action color (buttons, links, focus)
Semantic:    success/green, warning/amber, error/red, info/blue
Each color:  light variant, base, dark variant
```

---

## PILLAR 8: MOTION & DELIGHT

**Sources**: Material Design, Apple, Android, Calm Technology, Mindfulness, Airbnb, Tizen

- **Motion explains relationships.** Expansion shows spatial continuity. Collapse shows causality.
- **Respect attention.** Technology should require the smallest possible amount of attention 
  (Amber Case). Distracting animation is hostile design.
- **One orchestrated moment > scattered micro-interactions.** Focus animation budget on 
  high-impact moments.
- **Physics, not math.** Spring physics and ease-out curves feel natural.

### Timing Guide
```
Micro (hover, press):     100-150ms, ease-out
Small (expand, collapse): 200-250ms, ease-in-out
Medium (modal, page):     300-400ms, ease-out / spring
Large (route transition): 400-600ms, ease-in-out

Stagger children: base-delay + (index × 50ms)
Entry:  fade + translateY(8-20px), ease-out
Exit:   fade + scale(0.98), ease-in (faster than entry)

Always: respect prefers-reduced-motion
Never:  animate longer than 600ms
Never:  block interaction during animation
```

---

## PILLAR 9: ERROR PREVENTION & RECOVERY

**Sources**: Nielsen (#5, #9), Shneiderman, Weinschenk, Apple, GOV.UK, Sandi Wassmer, 
Jessica Enders

- **Prevent, don't report.** Design so users can't make serious errors (Shneiderman). 
  Disable invalid actions. Validate inline. Confirm destructive operations.
- **When errors happen, be kind.** Handle respectfully. Never blame the user. Never use 
  technical codes without human explanation.
- **Undo is sacred.** Reversible actions encourage exploration (Shneiderman).
- **Chunk error-prone tasks.** Multi-step wizard > single giant form (Weinschenk).

### Error Hierarchy
```
1. Prevent:  constraints, smart defaults, disabled states
2. Guide:    inline validation, hints, auto-complete
3. Catch:    graceful inline errors near the problem
4. Explain:  specific message + how to fix
5. Recover:  undo, auto-save, draft preservation
6. Forgive:  "Try again" is always an option
```

### Form Design
```
- Label above input (never placeholder-as-label)
- Show format hints BEFORE input, not as error after
- Validate on blur, not every keystroke
- Group related fields, one concept per step
- Let users review before final submission
```

---

## PILLAR 10: USER CONTROL & AUTONOMY

**Sources**: Apple iOS, Nielsen (#3), Tognazzini, Don Norman, Shneiderman, UNIX Philosophy, 
Inclusive Design

- **The user is the pilot.** Suggest, don't mandate. Recommend, don't force (Apple).
- **Support undo, redo, escape.** Users need a clearly marked emergency exit (Nielsen).
- **Let users customize.** Different needs, abilities, preferences. Multiple paths to completion.
- **Do one thing well.** UNIX Philosophy applied to UI. Composability beats monoliths.

---

## PILLAR 11: CONTEXT & ENVIRONMENT

**Sources**: GOV.UK, Whitney Hess, UX Axioms, Calm Technology, Android Wear, Voice Interface, 
VR Design, Responsive Principles

- **Context drives usage.** Phone on the bus? Desk with a monitor? Voice while cooking? 
  Never assume a single context.
- **Respect the periphery.** Move information between center and periphery fluidly (Amber Case).
- **Design the full journey.** Don't just design your part — consider the entire experience, 
  including how people begin and end (NHS).
- **Responsive = adaptive, not shrunk.** Each context has unique constraints and opportunities.

---

## PILLAR 12: ITERATION & HUMILITY

**Sources**: GOV.UK, Lean Startup, Agile UX, Code for America, d.school, UX Axioms, 37 Signals

- **Start small, iterate wildly.** Ship MVPs, test with real users, add/delete/refine (GOV.UK).
- **Data over hunches.** But data shows what; talking to people tells you why.
- **Observe behavior, not opinions.** People know when problems exist but not how to fix them 
  (Joshua Porter). Watch what they do.
- **Don't be afraid to scrap it.** Many things we make are sacrificial concepts (UX Axioms).
