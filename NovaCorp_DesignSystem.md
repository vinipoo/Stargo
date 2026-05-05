# NovaCorp Design System v1.0

A ZoomInfo-inspired component library for the NovaCorp Data Analytics & Invoice Audit Platform. This spec is the textual mirror of `NovaCorp_DesignSystem.html` and is the source of truth for component contracts.

> **Guiding principle:** *"Benchmarking starts with data cleaning."*

---

## Table of contents

1. [Principles](#1-principles)
2. [Color tokens](#2-color-tokens)
3. [Typography](#3-typography)
4. [Spacing & radius](#4-spacing--radius)
5. [Elevation & motion](#5-elevation--motion)
6. [Buttons](#6-buttons)
7. [Badges & status](#7-badges--status)
8. [Inputs & filters](#8-inputs--filters)
9. [Cards & KPIs](#9-cards--kpis)
10. [Tables](#10-tables)
11. [Navigation](#11-navigation)
12. [AI patterns](#12-ai-patterns)
13. [Charts & data viz](#13-charts--data-viz)
14. [Composite patterns](#14-composite-patterns)
15. [States](#15-states)
16. [Sortable + Filterable](#16-sortable--filterable)
17. [Score gauge](#17-score-gauge)
18. [Stale & partial-data](#18-stale--partial-data)
19. [Live state patterns](#19-live-state-patterns)

---

## 1. Principles

| # | Principle | What it means |
|---|---|---|
| 01 | Clarity over decoration | Enterprise users are time-pressured. No illustrations, no flourish. Data speaks. White space separates sections — it is never decorative. |
| 02 | Progressive disclosure | Summary at the top, drill-down within one click. Dashboard → Vendor → Invoice → Exception. Every screen answers *"what do I do next?"* |
| 03 | Automation is first-class | The AI agent is visible, trusted, and always explains its reasoning. Purple `#6D28D9` is its consistent visual signature. |

When components disagree, principles win.

---

## 2. Color tokens

All colors are exposed as CSS custom properties on `:root`. Status colors are reserved for compliance semantics — never decoration. Purple is exclusive to AI-generated content.

### Brand

| Token | Hex | Use |
|---|---|---|
| `--brand-primary` | `#003DA5` | Primary CTAs, active nav, selected rows, links |
| `--brand-primary-hover` | `#002F80` | Hover state |
| `--brand-primary-active` | `#00245F` | Active / pressed state |
| `--brand-primary-tint` | `#E5EBF6` | Selected row background, applied filter chip |

### AI

| Token | Hex | Use |
|---|---|---|
| `--ai-primary` | `#6D28D9` | All AI-generated insights, badges, action buttons |
| `--ai-hover` | `#5B21B6` | Hover state on AI buttons |
| `--ai-tint` | `#F1ECFB` | AI panel background, AI badges |

### Status

| Token | Hex | Semantic |
|---|---|---|
| `--status-success` | `#16A34A` | Compliant, passed, auto-resolved |
| `--status-warning` | `#D97706` | Partial, awaiting review, pending |
| `--status-danger` | `#DC2626` | Non-compliant, error, flagged |
| `--status-info` | `#2563EB` | Informational, in review |

### Surfaces & sidebar

| Token | Hex | Use |
|---|---|---|
| `--sidebar-bg` | `#0D1117` | Dark sidebar background |
| `--sidebar-text` | `#C9D1D9` | Sidebar default text |
| `--sidebar-text-muted` | `#8B949E` | Sidebar group labels |
| `--sidebar-active-bg` | `rgba(0,61,165,.18)` | Active nav item background |
| `--bg-page` | `#F0F2F5` | Page canvas |
| `--bg-surface` | `#FFFFFF` | Cards, tables, panels |
| `--bg-subtle` | `#F8F9FB` | Table headers, input affordances |
| `--bg-hover` | `#F3F4F7` | Row hover, ghost button hover |

### Text & borders

| Token | Hex | Use |
|---|---|---|
| `--text-primary` | `#0F172A` | Headings, key data |
| `--text-secondary` | `#475569` | Body copy |
| `--text-tertiary` | `#64748B` | Metadata, captions |
| `--text-disabled` | `#94A3B8` | Disabled affordances |
| `--border-subtle` | `#E5E7EB` | Card outlines, table dividers |
| `--border-default` | `#D1D5DB` | Inputs, chips |
| `--border-strong` | `#9CA3AF` | Pending steps, dashed boundaries |

### Color usage rule

Status colors live on **badges, dots, and chart marks** only — never as panel backgrounds. Brand blue is the only color that signifies interactivity. AI purple is exclusive to AI-generated insights.

---

## 3. Typography

Two faces only:

- **IBM Plex Sans** — UI and prose. Modern, refined, enterprise-credible.
- **IBM Plex Mono** — numerics, refs (invoice IDs, contract numbers), code. Fixed-width is essential for scannability across rows of financial figures.

### Scale

| Style | Size / weight | Family | Use |
|---|---|---|---|
| Display | 36 / 700 | Sans | Page hero, screen-level titles |
| H1 | 24 / 700 | Sans | Section headers |
| H2 | 18 / 600 | Sans | Sub-section headers |
| H3 | 14 / 600 | Sans | Card titles |
| Body | 14 / 400 | Sans | Default prose |
| Small | 12 / 400 | Sans | Metadata, helper text |
| Caps | 11 / 600 / .06em | Sans, uppercase | Labels, KPI captions |
| Numeric XL | 28 / 600 | Mono | KPI values |
| Numeric | 14 / 500 | Mono | Table cells with money |
| Code | 12 / 400 | Mono | IDs, references |

### Import

```html
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600&family=IBM+Plex+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---

## 4. Spacing & radius

Strict 4-pt rhythm.

| Token | Value | |
|---|---|---|
| `--sp-1` | 4px | tightest |
| `--sp-2` | 8px | inline gap |
| `--sp-3` | 12px | default gap |
| `--sp-4` | 16px | card padding |
| `--sp-5` | 20px | KPI card padding |
| `--sp-6` | 24px | section gap |
| `--sp-8` | 32px | major section gap |
| `--sp-10` | 40px | hero padding |
| `--sp-12` | 48px | page-level rhythm |

### Radius

| Token | Value | Use |
|---|---|---|
| `--r-sm` | 4px | code chips, small badges |
| `--r-md` | 6px | buttons, inputs |
| `--r-lg` | 8px | cards, tables |
| `--r-xl` | 12px | hero, modals |
| `--r-pill` | 999px | badges, chips |

---

## 5. Elevation & motion

Three shadow tiers. Motion is intentionally fast (120–180ms) using a single ease curve.

| Token | Value | Use |
|---|---|---|
| `--shadow-sm` | `0 1px 2px rgba(15,23,42,.06)` | Resting cards, KPI cards |
| `--shadow-md` | `0 2px 6px rgba(15,23,42,.08), 0 1px 2px rgba(15,23,42,.04)` | Hover, dropdowns |
| `--shadow-lg` | `0 8px 24px rgba(15,23,42,.10)` | Modals, drawers, command palette |

### Motion

| Token | Value | Use |
|---|---|---|
| `--dur-fast` | 120ms | Hover, focus, button states |
| `--dur-base` | 180ms | Drawer open, dropdown reveal |
| `--ease` | `cubic-bezier(.2,.8,.2,1)` | All UI transitions |

---

## 6. Buttons

Five variants × three sizes. Primary blue is exclusive to the most important call-to-action on a screen.

| Variant | Use |
|---|---|
| `btn--primary` | The single most important CTA on the screen |
| `btn--secondary` | Supporting actions (Export, Cancel-to-edit) |
| `btn--ghost` | Tertiary / dismissive actions |
| `btn--danger` | Destructive (Reject, Delete) |
| `btn--ai` | AI-driven actions (Apply AI fix, Open batch recovery) |

### Sizes

- Default: 36px height
- Medium: 38px
- Large: 42px (use sparingly — empty states, hero CTAs)

### States

`hover`, `active`, `focus`, `disabled`. Focus uses a 3px brand-tinted ring.

```html
<button class="btn btn--primary">Run audit</button>
<button class="btn btn--ai">✦ Apply AI fix</button>
```

---

## 7. Badges & status

Badges always carry a colored dot. The dot makes status legible at small sizes inside dense tables.

### Compliance badges

| Class | Label |
|---|---|
| `badge--success` | Fully Compliant |
| `badge--warning` | Partially Compliant |
| `badge--danger` | Non-Compliant |

### Other badges

`badge--info`, `badge--neutral`, `badge--ai`. AI badges replace the status dot with a purple dot.

```html
<span class="badge badge--success">
  <span class="dot"></span>Fully Compliant
</span>
```

### AI three-state pattern

| State | Trigger | Behavior |
|---|---|---|
| Flag for human | Confidence ≥ 75% AND impact above threshold | Always presents evidence first; no auto-action |
| Suggest action | Confidence 50–75% | Shows reasoning; action button requires explicit approval |
| Auto-resolved | High confidence + low impact | Logged with rationale; user can audit at any time |

---

## 8. Inputs & filters

Filters are first-class UI. Applied filters surface as chips at the top of the canvas (never buried in a sidebar).

### Form fields

- Inputs are 36px high with 12px horizontal padding.
- Focus state: brand-blue border + 3px brand-tinted ring.
- Search inputs use a leading magnifier icon at 14px.

### Filter chips

| State | Style |
|---|---|
| Default | White background, neutral border |
| Hover | Brand-blue text + border |
| Applied | Brand tint background + brand text + close affordance |

A `+ Add filter` chip and a `Clear all` ghost button anchor either end of the chip row.

### Toggles

20px high pill toggles. Use for binary view modes (compact/comfortable, by frequency / by impact).

---

## 9. Cards & KPIs

KPI cards stand in a single row at the top of every dashboard view. They show **one** metric, **one** delta, and (where applicable) **one** progress encoding.

### KPI anatomy

| Slot | Purpose |
|---|---|
| Label (caps, 11/600) | Metric name |
| Value (Mono, 28/600) | Headline number |
| Delta | `▲` up or `▼` down with semantic color |
| Bar (optional) | Visual progress bar mirroring the value |

### Hover

KPI hover elevates to `--shadow-md` and signals interactivity (the user can click through to the underlying view).

---

## 10. Tables

Dense tables with inline badges, sortable columns, dual-encoded ratios. Every row is clickable; hover tints the row.

### Table rules

- Header: `--bg-subtle`, 11/600 caps, brand-blue sort arrow on the active column
- Body row height: 40px (compact), 48px (comfortable)
- Numeric cells: Mono font, right-aligned
- Dual encoding: a percentage column shows both the number AND a 6px progress bar
- Status column: badge with dot
- Selected row: `--brand-primary-tint` background

### Invoiced vs Expected pattern

Three columns side-by-side: `Invoiced | Expected | Deviation`. `$0` deviations recede in green; non-zero deviations stand out in red. The math is done for the user.

---

## 11. Navigation

### Sidebar

- Width: 240px collapsed → 64px when minimized
- Background: `--sidebar-bg` (#0D1117)
- Group labels (caps, 10/600/.08em) separate the three platform phases
- Active item: brand-tinted background + 2px left border + white text
- Each item carries a `P1`, `P2`, or `P3` phase badge in mono

### Breadcrumbs

`<a>Audit</a> / <a>Invoices</a> / <span class="current">INV-2024-08812</span>`

The current item is `--text-primary` and 500-weight; preceding items are `--text-secondary` links.

### Tabs

Horizontal tabs with a 2px brand-blue underline on the active tab. Tabs may carry a count badge inline (e.g., `Exceptions [3]`).

---

## 12. AI patterns

If it's purple, the agent did it. AI components always lead with **evidence and confidence** — actions appear last.

### AI insight panel anatomy

```
[ ✦ ]  Pattern detected · Globex Freight              Confidence 84%
       17 invoices in the last 90 days show the same surcharge
       miscalculation. Estimated recovery: $48,210.

       Evidence: 17 invoices · 3 contracts · ingestion-log-7841

       [ Open batch recovery (17) ]  [ Review one-by-one ]  [ Dismiss ]
```

Mandatory elements:

1. Purple icon + descriptive title
2. Confidence percentage (always shown)
3. Body explanation in plain language
4. Evidence chain (pointers to the source data)
5. Two paths: confident action + cautious action

### AI tone-of-voice rules

- Never speak in absolutes ("definitely", "always")
- Always anchor a recommendation to a $ figure
- Never act silently — log everything

---

## 13. Charts & data viz

### Chart-to-question mapping

| Chart | Answers | Where used |
|---|---|---|
| Waterfall | Where did the net come from? | Compliance overview · financial impact |
| Pareto | Which 20% causes 80%? | Root cause analysis |
| Heatmap | Where is leakage concentrated? | Vendor × geography |
| Quadrant | Risk vs volume by vendor | Vendor strategy view |
| Trend line | Are we improving over time? | Compliance over quarters |
| Donut | Distribution of one variable | Compliance status share |
| Ranked bar | Top / bottom N comparison | Vendor leaderboard |

### Chart styling rules

- Bars use brand blue by default; only switch to status colors when the data IS the status
- Always include a legend AND a tooltip with the exact figure
- Negative deltas in financial waterfalls render in `--status-danger`; positive in `--status-success`
- Charts are responsive but never below 320px wide — collapse to a table below that breakpoint

### Score gauge (before/after)

Two circular gauges side-by-side with a `→` between. The single most important message is *"we improved the data."* The gauge fill color reflects the score:

- 0–60: warning amber
- 61–85: brand blue
- 86–100: status success

---

## 14. Composite patterns

Pre-assembled patterns mapped to specific screens.

### 14.1 Agentic pipeline (Screen 2)

A vertical step list with status markers. Each step has:

- 28px circular marker (success ✓, warning !, running pulse, pending number)
- Title + status badge
- One line of metadata (rows processed, FX rate, etc.)
- A 2px connector line linking sequential steps

When the agent stops at a step requiring human input, that step uses warning amber instead of green and the badge reads "Needs review."

### 14.2 Exception card (Screen 3)

Four-field grid mirroring the mental model of a finance controller:

| Field | Content |
|---|---|
| Deviation type | Rate card vs invoice / Currency / Volume / Surcharge / etc. |
| Financial impact | $-amount in mono, status-colored |
| Root cause | One sentence in plain language |
| Recommended action | Specific, dollar-anchored, batch-aware |

Card has a 3px left border in `--status-danger`.

### 14.3 Invoice header band (Screen 3)

Single-row card containing: Invoice ID (mono) · Vendor · Amount + deviation · Contract ref (mono) · Status badge (right-aligned).

All key metadata visible in 3 seconds.

### 14.4 Vendor compliance row

| Slot | Content |
|---|---|
| Vendor | Name (bold) + ID and region in mono caption |
| Status | Compliance badge |
| Compliance rate | Dual-encoded: 6px bar + percentage |
| Invoices | Mono right-aligned count |
| Exposure | Mono right-aligned $ |
| AI flags | AI badge with count, or em-dash if none |

---

## 15. States

Empty, loading, and error states are part of every screen — designed once, used everywhere.

### Empty state

- 2px dashed border, subtle background
- Icon (28px, 60% opacity)
- Title (14/600 secondary)
- Helper line (12/400 tertiary)
- Single primary CTA

### Loading state

- Use shimmer skeletons, never spinners (except for inline async operations)
- Shimmer animation: 1.4s infinite, gradient sweep
- Match the rough shape of the content being loaded

### Error / partial-data

- Render as a card with a 3px `--status-danger` left border
- Lead with a danger badge
- State the failure plainly + show the last successful sync time
- Provide a recovery action (Retry sync)

---

## Appendix · file inventory

| File | Purpose |
|---|---|
| `NovaCorp_DesignSystem.html` | Live interactive styleguide |
| `NovaCorp_DesignSystem.md` | This document — text spec |
| `NovaCorp_DesignSystem.docx` | Polished Word version for handoff |
| `Design_Walkthrough_NovaCorp.md` | Original design rationale baseline |

---

## 16. Sortable + Filterable

The brief mandates "tables must be sortable and filterable (show interaction states in your design)." This section specifies how that requirement is met.

### Sort indicator · column header states

| State | Visual | When applied |
|---|---|---|
| Default | `↕` at 50% opacity, `--text-disabled` | Sortable column at rest |
| Hover | `↕` at 100% opacity, `--text-secondary` | Cursor over the column header |
| Sorted | `▼` (desc) or `▲` (asc) in `--brand-primary`; column label brand blue | Active sort applied |

```html
<th class="sortable sorted" data-sort-key="exposure" data-sort-dir="desc">
  Exposure <span class="sort-arrow">▼</span>
</th>
```

### Filter buttons · 5-dimension row

Distinct from chip pattern (Section 8). Filter buttons sit above the table and represent the five filter dimensions required by the brief: **Vendor, Date Range, Geography, Contract, Service Level**. Each carries an inline applied value when filtered.

| State | Style |
|---|---|
| Default | White background, neutral border, `--text-secondary` |
| Hover | Brand blue text + border |
| Applied | Brand-tint background + brand text, label includes value (e.g., `Date: Q1 2026`) |

```html
<button class="filter-btn">Vendor <span class="caret">▾</span></button>
<button class="filter-btn filter-btn--applied">Date: Q1 2026 <span class="caret">▾</span></button>
```

### Filter dropdown popover

Opens on click of any filter button. Anchored below the button.

| Slot | Content |
|---|---|
| Title (caps, 10/600) | Filter dimension name |
| Options | Checkbox + value rows (multi-select) |
| Footer | `Clear` (ghost) and `Apply` (primary) buttons, equal width |

---

## 17. Score gauge

Circular SVG gauge used for the data-quality before/after pattern on Screen 2.

### Score-to-color mapping

| Score range | Stroke color | Token |
|---|---|---|
| 0–60 · Poor | Warning amber | `--status-warning` |
| 61–85 · Acceptable | Brand blue | `--brand-primary` |
| 86–100 · Excellent | Success green | `--status-success` |

### Math

```
circumference = 2 × π × 52 ≈ 326.7
fill-length   = (score / 100) × 326.7

// Examples
score 67 → stroke-dasharray="218.9 326.7"
score 81 → stroke-dasharray="264.6 326.7"   // live, brand
score 94 → stroke-dasharray="307.1 326.7"   // success
```

---

## 18. Stale & partial-data

Inline indicator that data is out-of-date or only partially available. Used in error/partial states to signal compromised data without hiding it.

- Background: `--status-warning-tint`
- Text: `#92400E` (warning text)
- Size: 10/600, 2px vertical / 7px horizontal padding
- Border-radius: `--r-sm`

Example labels: `stale`, `partial`, `PARTIAL DATA` (uppercase variant for page titles).

---

## 19. Live state patterns

Detailed specs for the four state variants in the submission. Each composite combines tokens from sections 1–15.

### 19.1 Empty state · pre-data

- 2px dashed border container, light surface, 56px vertical padding
- 80px circular icon · brand-tint background, brand-blue stroke
- Headline 22/700 + supporting line 14/400 secondary
- Two CTAs side-by-side (primary + secondary), large size
- Format chips below (mono font, 11px, neutral surface)
- Optional: 3-step "what happens next" preview row

### 19.2 Loading state · syncing

- Progress banner: brand-tint background, 3px brand left border
- Pulsing 10px brand dot, headline 13/600 brand, sub 11/400 tertiary
- Inline progress bar (8px high, brand fill, percentage in mono)
- AI panel below renders dimmed; italic line "✦ Agent will surface insights once sync completes…"

### 19.3 Error state · partial data

- Error banner: light-red background (#FFF5F5), 3px danger left border
- 32px circular icon (danger-tint, danger text, "!")
- Title 14/600 in danger-text color
- KPIs below render at 0.7 opacity with stale tags
- Affected-sources list (mono, badge per row showing failure reason)
- Paused-AI panel: `Paused` badge inline, message that agent never operates on incomplete data

### 19.4 Agent-running state · in-flight cleaning

- Progress banner uses AI purple variant of the loading banner pattern
- "Live" gauge in brand blue (interim, not yet success-green)
- Active pipeline step has a pulsing brand-blue marker and inline progress bar
- Streaming activity log on the right shows recent agent actions in mono
- Required text: every agent-narrated string starts with `✦ Agent…`

---

*Design System v1.1 · Yossi P. · Includes sortable/filterable patterns, score gauge, stale tags, and full state library*
