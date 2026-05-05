# NovaCorp Data Analytics & Invoice Audit Platform
## Design Walkthrough — Yossi P.

---

## 1. Design Approach & Principles

**The guiding framing:** This platform is a *decision engine*, not a reporting tool. Every screen is designed around the question: *"What action does the user need to take next, and how quickly can they reach it?"*

Three design principles drove every choice:

1. **Clarity over decoration** — enterprise users are under time pressure. No illustrations, no lifestyle imagery, no flourish. Data speaks.
2. **Progressive disclosure** — show summaries at the top, drill-down within one click. Dashboard → Vendor row → Invoice → Exception.
3. **Automation is a first-class citizen** — the AI agent is visible, trusted, and always explains its reasoning. It never acts silently.

---

## 2. Visual Language (ZoomInfo-Inspired)

The visual system mirrors ZoomInfo's B2B SaaS aesthetic:

| Element | Choice | Rationale |
|---|---|---|
| Sidebar | Dark (#0D1117) with blue accent | Matches ZoomInfo's navigation: orientation without distraction |
| Background | Light grey (#F0F2F5) | Creates visual hierarchy between cards and page |
| Primary color | #003DA5 (NovaCorp deep blue) | All interactive elements, data accents, primary CTAs |
| Typography | IBM Plex Sans + IBM Plex Mono | Plex Sans: refined enterprise feel. Mono: data values need fixed-width for scannability |
| Status colors | Green / Amber / Red | Universal compliance semantics — no learning required |
| AI accent | Purple (#6D28D9) | Distinct from brand and status colors — AI activity is immediately identifiable |

---

## 3. Screen-by-Screen Rationale

### Screen 1: Compliance Overview (Main Dashboard)

**Information hierarchy:** KPIs first (5-second summary), then financial impact (waterfall + donut), then vendor table (action layer).

**Filter bar:** Positioned above KPIs, not buried in a sidebar. Filters are "first-class" as requested — changing them should feel like changing the lens, not digging through settings.

**Vendor table:** Sortable, with compliance rate shown as both a percentage and a visual bar — dual encoding for fast pattern recognition. AI flags are shown inline as badges, not in a separate pane.

**Agentic AI placement:** A collapsible panel just below the filters. It's prominent but dismissible — users who trust the agent will leave it open; power users can collapse it. Crucially, the AI shows *evidence and impact* before offering any action button. No black-box automation.

---

### Screen 2: Data Quality Report

**Score circles:** Before/after as two circular gauges side by side — the single most important message is "we improved the data", and this makes it visual and immediate.

**Agentic pipeline flow:** A vertical step-by-step showing exactly what the AI did, what it resolved, and where it stopped. The agent always shows its work. Step 4 uses amber (warning) instead of green because 6 vendors need human confirmation — the design communicates this status without requiring users to read every detail.

**Log panel:** An append-only event log with timestamps. Enterprise users (especially operations analysts) want to see exactly what happened and when. Paired with the issue breakdown on the left, this gives both summary and audit trail.

---

### Screen 3: Invoice Detail / Exception View

**Invoice header band:** All key metadata visible in 3 seconds — vendor, amount, contract reference, and the compliance badge. The deviation (+$4,185) is highlighted in red immediately.

**Line-item table:** Invoiced vs. Expected columns side by side, with a Deviation column. Green $0 deviations visually recede; red deviations stand out. Users don't have to calculate — the math is done.

**Exception cards:** Each exception is a self-contained card with four fields: Deviation Type, Financial Impact, Root Cause, Recommended Action. This mirrors the mental model of a finance controller reviewing an audit report.

**AI recommendation:** Shown at the bottom of the exception panel, after the facts. The AI connects this invoice to the 17 others with the same issue — providing systemic context that a human reviewer would miss. Two action buttons are offered: batch recovery (high-confidence) and a more cautious option requiring verification first.

---

### Screen 4: Root Cause Analysis

**Category cards grid:** All 8 exception categories visible at once as scannable cards. Sorted by financial impact. Each shows frequency, impact, and a severity badge — three data points without needing to open a table.

**Pareto chart:** Bar chart (financial impact) + cumulative line (% of total) on a dual axis. This directly answers the question: "Which 2–3 things should I fix to resolve 80% of the problem?" The answer is visual — bars 1–4 cover the first plateau.

**AI pattern detection:** Three insights with different risk levels: a systemic issue (red), a predictive alert (amber/blue), and a quick-win opportunity (green). Structured this way to match how a procurement manager actually triages — fix systemic first, prevent future, automate easy wins.

**Trend line:** Compact 4-quarter compliance trend card showing the platform is working. This validates past investment and sets expectation for continued improvement.

---

## 4. Agentic Flow Design — Key Decisions

The brief asked for AI agents that "proactively identify, flag, and resolve problems." I made the following design choices:

**Transparency over magic:** Every AI action is explained. The agent shows confidence levels, source data, and specific financial impact before offering action buttons. Trust is earned through visibility, not assumed.

**Three action states:**
- 🔴 *Flag for human review* — high-impact, requires confirmation
- 🟡 *Suggest action, await approval* — medium-confidence, shows reasoning
- ✅ *Auto-resolved* — low-risk, routine, logged and auditable

**Agentic pipeline on Screen 2:** Shows the AI cleaning pipeline as a step-by-step flow with clear status indicators. Human handoffs are clearly marked (step 4 stops at amber). This makes the human-AI collaboration model explicit.

**Purple = AI throughout:** Every AI-generated insight, action, or resolution uses the purple (#6D28D9) color system exclusively. This creates a consistent visual language: "if it's purple, the agent did it."

---

## 5. Interaction Design Notes

- **Vendor rows are clickable** — clicking any vendor drills to their invoice list
- **Sidebar navigation reflects the 3-phase model** — Phase badges (P1, P2, P3) communicate progress
- **AI panel is collapsible** — respects users who prefer a data-only view
- **Status badges use dot indicators** — visible even at small sizes in dense tables
- **Tables show hover states** — row highlights on hover signal clickability
- **Export buttons on every screen** — enterprise users always need to export

---

## 6. What I Would Build Next (If Time Allowed)

- **Empty states** for data ingestion before any files are uploaded
- **Loading skeleton states** for charts and KPI cards during data refresh
- **Notification center** for async AI agent actions completed in background
- **Mobile-responsive companion view** for executive summary only
- **Dark mode** — many finance/operations users prefer dark for long sessions

---

*Platform designed for NovaCorp — Proof of Value phase. All data is illustrative.*
