# Forecast Movement Readout (Automated Weekly Forecast Analysis)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI system, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/33-ai-forecast-movement-readout.md`)
- **User's role:** Sole designer and builder; part of the executive reporting system (ricketts2026_ai_exec_reporting_system.md)
- **Status:** internal, live in production (scheduled Mondays 7am ET)

## Methods & Tools
- **Operational frameworks:** Forecast category analysis (Closed, Commit, Best Case, Pipeline, Omitted), movement-cause classification, pipeline coverage by segment
- **Software/platforms:** Snowflake daily opportunity snapshots, SQL, Claude Skills, scheduled tasks, hosted artifacts, Playwright, Slack
- **Key techniques:** Two-snapshot full outer join (current vs. seven days earlier) so deals that appeared or disappeared are both captured; in-quarter and in-scope flags per date; close-date history for repeat pushers; documented plan override when CRM targets lag the live plan

## Key Results
1. Every Monday, answers four questions for leadership: where the quarter stands by forecast category, what changed since last week, which deals caused each change and why, and whether next quarter's pipeline covers target by segment
2. Classifies every moving deal into one of seven causes: pushed out of quarter, pulled in, new opportunity, left forecast scope, category migration, ARR restated, record split
3. Pulls full-year close-date history for every pushed or materially re-scoped deal; source identifies repeat-pusher history as the most useful insight in the report
4. Reconciliation gate: deal-level contributions must sum to each category's weekly change within $0.01 across all five categories, or the run stops
5. Next-quarter raw coverage bands: 3x or more "covered," 2–3x "watch," under 2x "thin," with the state word always shown alongside color
6. Fixed-URL page (executive bookmarks keep working), print-ready PDF, and a Slack summary leading with Closed won plus Commit and its weekly change
7. Executive feedback removed a mix-shift column, chart captions, and omitted-deal commentary because none changed a decision

## Novelty Claims
- None claimed in source. Distinctive element: every dollar of weekly category movement is attributed to a named deal before publishing

## Collaboration & Scope
- **Other groups:** Data team's shared Snowflake analyst layer; executive feedback shaped the format
- **User's specific contribution:** Designed the method, movement taxonomy, reconciliation gate, page structure, and delivery
- **Shared vs. sole work:** Sole-built on the data team's warehouse layer

## Provenance Notes
- **Publication status:** N/A — internal system
- **Safe to claim:** Full-ownership verbs (Automated, Built, Designed)
- **Needs hedging:** Data layer, per config.md
- **Do NOT claim:** No time-savings figure specific to this readout. The 3 hours/week belongs to the overall reporting system (ricketts2026_ai_exec_reporting_system.md)

## Resume Bullet Seeds
1. Automated a weekly forecast movement readout that traces every week-over-week category change to named deals and causes (pushes, pull-ins, re-scopes, record splits), reconciled to the cent before it publishes.
2. Added repeat-pusher close-date history and segment coverage bands (covered, watch, thin) to the Monday forecast readout so leadership sees which deals have slipped three or four times before the forecast call.
