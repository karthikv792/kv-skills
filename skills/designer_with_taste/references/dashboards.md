# Dashboard & Data Visualization Design

Principles drawn from IBM Design, Salesforce Lightning, SAP Fiori, Ant Design, Google PAIR, 
Degreed Digital Product Design, information architecture (Dan Brown), visual usability (Tania 
Schlatter), cognitive load reduction (Jon Yablonski), and the meta-principles for data-heavy 
interfaces across all 212 principle sets.

---

## Core Dashboard Philosophy

A dashboard exists to compress decision-making time. Every element should help the user 
answer a question or take an action faster than they could without it. If a metric doesn't 
drive a decision, it doesn't belong on the dashboard.

---

## Information Architecture for Data

### The Question-First Framework
Before designing any dashboard, answer:
```
1. Who is looking at this? (persona: executive, analyst, operator)
2. What questions do they arrive with? (status, trend, anomaly, comparison)
3. What decisions do they make from answers? (approve, investigate, escalate)
4. How often do they look? (real-time, daily, weekly, quarterly)
5. What's their data literacy? (chart-fluent, needs guidance)
```

### The Inverted Pyramid of Data
```
Level 1: KPI summary    → Answers "how are we doing?" in <3 seconds
Level 2: Trend context   → Answers "is this getting better or worse?"
Level 3: Breakdown       → Answers "where specifically?"
Level 4: Raw detail      → Answers "show me the actual data"
```

Design the dashboard so Level 1 is visible without scrolling. Users drill into 
deeper levels on demand.

---

## Layout Patterns

### The KPI Bar
A row of 3-6 key metrics at the top of the dashboard. This is the most scanned area.
```
Each KPI card:
- Metric label (small, muted)
- Current value (large, bold, primary color)
- Trend indicator: ↑12% or ↓3% with semantic color (green/red)
- Comparison period: "vs. last month" (caption, muted)
- Sparkline (optional): 30-day trend in miniature

Spacing: equal gaps between cards, full-width row
Don't: use more than 6 KPIs — it becomes noise
Don't: mix incompatible timeframes in the same row
```

### The Grid Dashboard
For multi-metric monitoring (ops dashboards, analytics overviews):
```css
/* Recommended grid: 12-column base, gap: 16-24px */
.dashboard-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--space-lg);
  padding: var(--space-xl);
}

/* Card sizes: span 3 (small), 4 (medium), 6 (half), 12 (full) */
.card-sm  { grid-column: span 3; }
.card-md  { grid-column: span 4; }
.card-lg  { grid-column: span 6; }
.card-xl  { grid-column: span 12; }
```

### The Narrative Dashboard
For executive/reporting dashboards that tell a story:
```
Structure:
1. Header: title + date range + filters
2. Hero section: the most important insight (1 chart, full width)
3. Supporting metrics: 2-3 cards explaining the hero
4. Detailed breakdowns: tables or drill-down charts
5. Actions: what to do based on this data

Flow: top-to-bottom like a report, not a grid of disconnected widgets
```

### The Monitoring Dashboard
For real-time operations (server health, live metrics, trading):
```
Principles:
- Scannable at a glance from 6+ feet away
- Status uses traffic-light semantics (green/amber/red) + shape
- Anomalies surface automatically (don't require searching)
- Time axis is always present and consistent
- Auto-refresh with last-updated timestamp visible
- Dense information is acceptable — operators are expert users
```

---

## Chart Selection Guide

Choose the chart type that answers the question, not the one that looks interesting:

```
Question                          → Chart Type
─────────────────────────────────────────────────────
"How much?"                       → Bar chart (horizontal for many items)
"How does it change over time?"   → Line chart (continuous) or bar (discrete)
"What's the proportion?"          → Stacked bar or treemap (NOT pie chart*)
"How do two things correlate?"    → Scatter plot
"What's the distribution?"        → Histogram or box plot
"Where is it?"                    → Map (choropleth or dot)
"What's the flow?"                → Sankey or funnel
"How does it break down?"         → Treemap or sunburst
"What's the ranking?"             → Horizontal bar, sorted descending
"What's the current status?"      → Gauge or KPI card

* Pie charts: use only with ≤5 slices where relative proportion is the 
  primary question. Never use 3D pie charts. When in doubt, use a bar chart.
```

---

## Data Visualization Best Practices

### Color in Data
```
Sequential data (low → high):      Single hue, light to dark
Diverging data (negative ↔ positive): Two hues (e.g., blue ↔ red) with neutral center
Categorical data (groups):          Distinct hues, max 7 before labels are needed
Status/semantic:                    green=good, amber=warning, red=critical, blue=info

Never: rely on color alone — add patterns, labels, or icons
Never: use rainbow gradients for sequential data
Always: test with color-blindness simulator (deuteranopia, protanopia)
Always: use colorblind-safe palettes (avoid pure red/green pairs)
```

### Axes & Labels
```
- Always label both axes (even when "obvious")
- Start Y-axis at 0 for bar charts (truncated axes mislead)
- Line charts: Y-axis can start at non-zero IF clearly labeled
- Format numbers: 1.2M not 1,200,000 / $45K not $45,000
- Date formats: consistent, locale-aware, abbreviated for space
- Grid lines: subtle (low opacity), horizontal only for most charts
- Remove chartjunk: no decorative borders, shadows, or 3D effects
```

### Interaction Patterns
```
Hover/tap:       Tooltip with exact value + context
Click:           Drill down to detail view or filter
Brush/select:    Select range on a chart to filter others (crossfiltering)
Zoom:            Scroll to zoom on time-series, pinch on mobile
Reset:           Always provide "reset all filters" — users get lost
Compare:         Overlay, side-by-side, or toggle between datasets
Export:           Allow CSV/PNG download for further analysis
```

---

## Table Design

Tables are often the most efficient data display. Don't underestimate them.

### Layout Rules
```
- Right-align numbers (they compare better when decimal-aligned)
- Left-align text
- Consistent column widths (don't let content push columns around)
- Row height: 40-52px for comfortable scanning
- Alternating row backgrounds: subtle (2-3% opacity) or use borders
- Sticky header: always visible during scroll
- Sticky first column: for wide tables on smaller screens
```

### Interactive Table Features
```
Essential:
- Sortable columns (click header to sort, show direction arrow)
- Pagination or virtual scroll (never dump 10,000 rows)
- Row hover highlight
- Search/filter

Nice to have:
- Column resizing
- Column reordering (drag headers)
- Expandable rows for detail
- Bulk selection + actions
- Keyboard navigation (arrow keys between cells)
```

### Responsive Tables
```
Wide screen:    Full table with all columns
Medium:         Hide secondary columns, show on expand
Narrow:         Card layout — each row becomes a card with label:value pairs
                OR horizontal scroll with sticky first column
```

---

## Dashboard-Specific UX Patterns

### Filters & Controls
```
Position:    Top of dashboard or left sidebar (not bottom)
Persistence: Filters survive navigation and page refresh
Defaults:    Smart defaults (current month, user's team, active status)
Feedback:    Show active filter count/summary above results
Clear all:   Always available, one click
Applied:     Show filter chips/tags that are individually removable
```

### Loading States for Data
```
Initial load:  Skeleton screens matching the chart/table layout
Refresh:       Keep stale data visible, show subtle "updating" indicator  
Error:         Show last-good data + error message + retry button
Empty state:   Explain why empty + guide toward data (not just "No data")
Streaming:     Animate data arrival for real-time feeds
```

### Dashboard Header Pattern
```
┌──────────────────────────────────────────────────────┐
│  Dashboard Title          [Date Range ▾] [Filters ▾] │
│  Last updated: 2 min ago  [Export ↓] [⟳ Refresh]     │
└──────────────────────────────────────────────────────┘
```

---

## Dashboard Design Checklist

```
□ Primary question answerable in <3 seconds (KPI bar)
□ Chart types match the questions being asked
□ Consistent time ranges across all widgets
□ Color used semantically (not decoratively)
□ All charts labeled (axes, legends, units)
□ Tooltips on hover for exact values
□ Loading/error/empty states for every data widget
□ Filters visible, persistent, and clearable
□ Mobile: KPIs stack vertically, charts simplify or convert to tables
□ Colorblind-safe palette
□ Numbers formatted for readability (1.2M, $45K)
□ Export option available
□ Auto-refresh with visible timestamp
□ No pie charts with >5 slices
□ No 3D charts ever
□ Tables: right-aligned numbers, sticky headers
```
