# Anti-Patterns: The Taste Killers

What separates work with taste from generic output is knowing what to avoid. Review this 
after your first draft of any interface.

---

## Visual Anti-Patterns

### The Purple Gradient Plague
If your first instinct is a purple-to-blue gradient on white, stop. This is the default 
"AI-generated" aesthetic. Choose a real palette with character, derived from the brand, the 
content, or the audience — not from the most popular Dribbble shot.

### Border-Radius Uniformity
Rounded corners are fine. Identical rounding on every element (buttons, cards, inputs, images, 
containers) creates visual monotony. Vary your radii intentionally: sharp corners for data/
professional, generous rounds for friendly/playful, mixed for visual interest.

### Shadow Soup
Box-shadows should create a depth hierarchy, not decorate every surface. Define an elevation 
system (2-4 levels) and apply it consistently. Most elements should be at ground level.

### Icon Salad
Don't use an icon for every concept. Research shows icons without labels fail for all but 
the most universal symbols (home, search, close). When you use icons, choose one family and 
stick with it. Never mix outlined, filled, and line-drawn styles.

### The Centered-Everything Layout
Center alignment is appropriate for heroes, CTAs, and short content. For content-heavy 
interfaces, left-aligned text with an intentional grid is more readable and professional. 
Center-aligned paragraphs are almost never correct.

### Thin Light Gray Text
Using #ccc or similar low-contrast text for "aesthetic" reasons fails accessibility and 
readability. Secondary text should still meet 4.5:1 contrast. Hierarchy comes from size and 
weight, not from making text invisible.

### The Card Wall of Sameness
A grid of identically-sized, identically-styled cards with no visual differentiation. When 
everything is equal, nothing is important. Feature one item prominently, vary card sizes, or 
use visual weight to guide attention.

### Gratuitous Glassmorphism
Frosted glass effects (backdrop-filter: blur) look elegant in demos but create readability 
problems when the background content varies. Use only where the background is controlled and 
contrast is guaranteed.

### Rainbow Status Indicators
Using five different colors for five statuses when two (active/inactive or on-track/needs-
attention) would suffice. More colors = more cognitive load. Simplify your status model first.

### Decorative Empty Space
There's a difference between intentional white space (creating rhythm, grouping, breathing 
room) and accidentally huge gaps from lazy spacing. White space should feel designed, not like 
something is missing.

---

## UX Anti-Patterns

### Placeholder-as-Label
When a user clicks a field and the placeholder disappears, they lose the label. For complex 
forms, they can't review what each field is for. Always use persistent labels above inputs.

### Confirm-Shaming
"No, I don't want to save money" — manipulative decline copy erodes trust permanently. Let 
users say "No thanks" with dignity.

### Infinite Scroll Without Position
If users can't tell where they are in a list (how many items remain, how far they've scrolled), 
they feel disoriented. Provide scroll position indicators, "back to top" buttons, or pagination.

### Auto-Play Everything
Sound, video, animations that start without user consent. Respect that users didn't ask for 
this. Let them opt in. Exception: muted background video is sometimes acceptable if it can be 
paused.

### Hiding the Close Button
Modals, banners, popups, cookie notices — if a user wants to dismiss something, the exit should 
be immediately visible (top-right corner, X icon, minimum 44px target). Don't make them hunt.

### CAPTCHA as Punishment
Requiring CAPTCHA on routine actions (login, search, comment) punishes real users to filter 
bots. Use invisible verification first; show CAPTCHA only as fallback.

### Dark Patterns Disguised as Personalization
"Based on your preferences, you've been opted into..." — personalization should serve the user, 
not extract value from them without informed consent.

### Newsletter Popup on First Visit
The user hasn't even read your content yet and you're asking for their email. Wait until they've 
demonstrated engagement (scroll depth, time on site, return visit).

### Progress Bars That Lie
A progress bar that sits at 99% for 30 seconds is worse than an honest spinner. If you can't 
measure real progress, use an indeterminate indicator instead.

### Triple-Nested Modals
A modal on a modal on a modal. If your information architecture requires this depth, your 
information architecture is broken. Redesign the flow.

---

## Structural Anti-Patterns

### Designing for Yourself
You are not the user. Your comfortable familiarity with your own interface is not evidence 
of usability. Test with real users or at minimum, the "parent test."

### Feature Addition as Progress
More features ≠ better product. The best product features are those that will actually be 
used (Joshua Porter). Every additional feature adds choices, complexity, and maintenance burden. 
Dare to say "no."

### Ignoring the Zero State
The first-time experience is crucial yet often overlooked. When nothing has happened yet, 
provide direction and guidance — never a blank canvas (Joshua Porter). "No data yet" should 
show what will appear here and how to create it.

### Designing for the Demo
The 10-minute demo impresses differently than the 10-hour workday. Design for sustained daily 
use, not first impressions alone. What feels exciting once becomes exhausting repeated 100 times.

### Responsive as Afterthought
"We'll figure out mobile later" means mobile gets a broken version of desktop. Design for the 
most constrained context first (mobile, slow connection, small screen) and enhance from there.

### Copy-Paste from Component Libraries
Using Material UI / Chakra / shadcn components without customization produces generic interfaces 
that look like every other project using the same library. The library is a starting point, 
not the finish. Customize colors, typography, spacing, and interaction patterns to create 
something that belongs to your specific product.

### The Kitchen Sink Settings Page
Dumping every possible option onto one settings page. Group settings by task, provide sensible 
defaults, and hide advanced options behind progressive disclosure.

### Carousel of Neglect
Carousels / image sliders where the user never clicks past the first slide. Research 
consistently shows that carousel engagement drops dramatically after the first frame. If 
content matters, give it a permanent visible home.

### The Footer Graveyard
Important links buried in a massive footer that no one scrolls to. If something is important 
enough to link, it's important enough to surface in the main navigation or content flow.

---

## Code Anti-Patterns

### Div Soup
```html
<!-- Taste killer -->
<div class="header">
  <div class="nav">
    <div class="button" onclick="navigate()">Home</div>
  </div>
</div>

<!-- With taste -->
<header>
  <nav aria-label="Main">
    <a href="/">Home</a>
  </nav>
</header>
```

### Magic Numbers
```css
/* Taste killer */
.card { padding: 13px 17px; margin-bottom: 23px; border-radius: 7px; }

/* With taste — every number from the system */
.card { 
  padding: var(--space-sm) var(--space-md); 
  margin-bottom: var(--space-lg);
  border-radius: var(--radius-md);
}
```

### Inline Styles for Layout
```html
<!-- Taste killer -->
<div style="display:flex; justify-content:space-between; margin:20px;">

<!-- With taste — semantic class, system values -->
<div class="header-actions">
```

### Z-Index Wars
```css
/* Taste killer */
.modal { z-index: 99999; }
.tooltip { z-index: 999999; }
.dropdown { z-index: 9999999; }  /* who will win? nobody */

/* With taste — defined stacking system */
:root {
  --z-dropdown: 100;
  --z-sticky: 200;
  --z-overlay: 300;
  --z-modal: 400;
  --z-toast: 500;
  --z-tooltip: 600;
}
```

---

## The Anti-Pattern Audit

After completing any design, run this check:

```
□ No elements present "just because" — everything has a purpose
□ No identical styling on everything (varied sizes, weights, colors)
□ No placeholder-as-label in forms
□ No manipulative decline copy
□ No auto-playing media without consent
□ No hidden close/dismiss buttons
□ No pure decorative animations (all motion communicates something)
□ Close/dismiss is always visible on modals, banners, popups
□ Empty states provide guidance, not blank space
□ Component library defaults have been customized
□ Magic numbers replaced with system tokens
□ Semantic HTML used throughout (no div-as-button)
□ Z-index follows a defined stacking system
□ Mobile is designed, not just reflowed
```
