# Mobile-Specific Design Patterns

Principles drawn from Apple iOS (7, 11, UX Guidelines), Android Design Principles, Android 
Wear (original + OS), Google Glass, Fjord Wearable Principles, Responsive Principles, 
GOV.UK ("Understand Context"), and the ecology of multi-device design.

---

## Core Mobile Philosophy

Mobile is not a small desktop. It is a fundamentally different context: held in one hand, used 
in motion, interrupted constantly, competing with the real world for attention. Respect this.

---

## Touch & Gesture Design

### Target Sizes
```
Minimum touch target:  44×44px (Apple) / 48×48dp (Android)
Comfortable target:    48×48px or larger
Spacing between targets: minimum 8px gap to prevent mis-taps
Thumb zone (one-handed): primary actions in the bottom 2/3 of screen
```

### Gesture Principles
- **Discoverable first, gestural second.** Every gesture shortcut must have a visible button 
  alternative. Hidden gestures are power-user features, not primary interactions.
- **Standard gestures are sacred.** Swipe-back, pull-to-refresh, pinch-to-zoom — never hijack 
  platform-standard gestures for custom behavior.
- **Physics and momentum.** Scrolling should feel like flicking a physical object. Use inertia, 
  rubber-banding, and momentum-based scrolling. Apple: people physically interact with the screen.
- **Confirm destructive gestures.** A swipe-to-delete must be reversible (undo toast) or 
  confirmed (action sheet). Accidental swipes happen constantly.

### Touch Feedback
```
Touch down:   immediate highlight (<50ms) — opacity or scale change
Touch up:     ripple (Material) or highlight clear — confirms the tap registered
Long press:   after 500ms, haptic + context menu
Drag:         element follows finger precisely, show destination hints
Release:      snap to position or animate to final state
```

---

## Mobile Navigation Patterns

### Tab Bar (Bottom Navigation)
Best for: 3-5 top-level destinations. The dominant mobile pattern because it keeps navigation 
in the thumb zone while showing current location.
```
- 3-5 items maximum (more = shrink targets below usable)
- Always show labels (icons alone fail accessibility)
- Active state: filled icon + color + label bold
- Badge for notifications: small, high-contrast dot or count
- Never hide the tab bar on scroll for primary navigation
```

### Stack Navigation (Push/Pop)
Best for: drill-down content hierarchies (settings, detail views, threading).
```
- Back button always top-left (iOS) or back gesture (Android)
- Title in navbar shows current location
- Transition: new screen slides in from right, old slides left
- Maintain scroll position when returning
```

### Sheets & Modals
Best for: focused tasks, confirmations, supplementary content.
```
- Bottom sheet: draggable, partial cover, maintains context
- Full sheet: focused task requiring full attention
- Alert: critical confirmation, 2-3 options max
- Always: clear dismiss target (X, swipe down, tap outside)
```

### When NOT to Use a Hamburger Menu
The hamburger (☰) hides navigation, reducing discoverability. Avoid it when:
- You have ≤5 destinations (use tab bar instead)
- Key features are hidden and usage drops
- Your analytics show <5% hamburger open rate

Use hamburger only for: secondary features, settings, account management.

---

## Mobile Content Strategy

### Above the Fold
On a ~375×667 viewport, you get about 500px of content before scroll. Use it:
```
- Primary headline: what this screen is about
- Primary action: the ONE thing to do here
- Context cue: where am I, how did I get here
- Visual hook: image, illustration, or data that rewards arriving
```

### Scannable Lists
Mobile users scan, they don't read. Optimize for scanning:
```
- Left-align text (most natural scan direction)
- Bold key info (name, title, amount) — secondary info regular weight
- Consistent layout per item (image left, text center, action right)
- Row height: minimum 48dp, comfortable at 56-72dp
- Dividers: subtle (1px, low-contrast) or use spacing instead
```

### Typography on Mobile
```
Body:       16px minimum (17px on iOS for retina)
Headlines:  24-34px (bigger on larger phones)
Caption:    13-14px, but use sparingly
Line length: ~35-45 characters (natural for phone width)
Line height: 1.4-1.6 for body text
Paragraph spacing: 1em between paragraphs
```

---

## Performance as Design

On mobile, speed IS the experience. A beautiful app that loads in 4 seconds loses to an ugly 
one that loads in 1 second.

### Perceived Performance
```
- Skeleton screens: show content structure immediately on load
- Optimistic updates: show the result before confirming with server
- Progressive loading: text first, then images, then rich media
- Prefetch: load the next likely screen while user reads current one
- Offline-first: cache aggressively, sync in background
```

### Interaction Latency Budget
```
Instant feedback:     <100ms  (button highlight, toggle switch)
Acknowledged:         <300ms  (navigation start, form submit)
Noticeable delay:     <1000ms (network request with spinner)
Risk of abandonment:  >3000ms (must show meaningful progress)
```

---

## Responsive Breakpoints

Don't design "mobile" and "desktop" — design for content and context:

```css
/* Content-based breakpoints, not device-based */
--bp-compact:   320px;   /* Small phones */
--bp-medium:    600px;   /* Large phones / small tablets */
--bp-expanded:  840px;   /* Tablets / small laptops */
--bp-large:     1200px;  /* Desktop */
--bp-xlarge:    1600px;  /* Wide desktop */

/* Use container queries when available for component-level responsiveness */
@container (min-width: 400px) { /* component adapts to its container, not viewport */ }
```

### Layout Adaptation Strategy
```
Compact (320-599):   Single column, full-width cards, bottom sheet nav
Medium (600-839):    Optional 2-column for lists, rail navigation possible
Expanded (840-1199): Sidebar + content, card grids, split view
Large (1200+):       Multi-panel, persistent sidebar, detailed tables
```

---

## Platform-Specific Conventions

### iOS Conventions (Apple HIG)
- Navigation: tab bar bottom, navigation bar top
- Actions: trailing swipe actions, long-press context menus
- Modals: sheet presentation (card stacking from bottom)
- Haptics: use Taptic Engine for feedback on meaningful actions
- Dynamic Type: support system font scaling
- Safe area: respect notch, home indicator, status bar

### Android / Material Conventions
- Navigation: bottom bar or navigation rail
- Actions: FAB for primary action, overflow (⋮) for secondary
- Modals: bottom sheets preferred over center dialogs
- Back gesture: system back navigation from left edge
- Edge-to-edge: content behind system bars with proper insets
- Adaptive layouts: use WindowSizeClass for responsive design

### Shared Principles
Both platforms agree: respect system accessibility settings (font size, bold text, 
reduce motion, high contrast), support dark mode, handle interruptions gracefully 
(incoming calls, notifications, multitasking).

---

## Mobile-First Design Checklist

```
□ Primary action visible without scrolling
□ Touch targets ≥44px with ≥8px spacing
□ One-hand reachable primary actions (thumb zone)
□ Skeleton loading states for all async content
□ Offline state handled gracefully
□ Pull-to-refresh where appropriate
□ System back/swipe-back navigation works
□ Keyboard doesn't obscure focused input
□ Landscape orientation considered
□ Dynamic Type / font scaling supported
□ Safe areas respected (notch, home indicator)
□ Dark mode supported
□ Tested on small phone (320px) AND large phone (430px)
□ Form inputs use correct keyboard type (email, phone, number)
```
