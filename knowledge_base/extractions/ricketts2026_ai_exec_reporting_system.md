# Executive Reporting System (AI-Driven Weekly Readouts)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI system, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/28-ai-executive-reporting-system.md`)
- **User's role:** Sole designer and builder of the readouts; built on the data team's shared Snowflake analyst layer
- **Status:** internal, live in production (forecast readout runs on a schedule)

## Methods & Tools
- **Operational frameworks:** Weekly reporting cadence by audience, reconciliation controls, data confidence statements, executive-depth writing (one-line verdict, capped deal lists, decision-only content)
- **Software/platforms:** Claude Skills, Claude Cowork scheduled tasks, hosted artifacts, Claude in Chrome; MCP connectors for Snowflake, Gong, and Slack; Snowflake (daily opportunity snapshots, goal attainment mart, marketing funnel and MQL history marts, raw Salesforce stage history); SQL; Python; Playwright (PDF export); HTML with inline SVG charts
- **Key techniques:** Four-layer build (data access, report logic, rendering, delivery); queries name tables in full and open with a `WITH` clause to avoid silent row limits; large result sets written to file and processed in Python; executive-approved business rules (coverage color bands, five-deal cap per category) written into each skill; PDF pages rendered to PNG and inspected before delivery

## Key Results
1. Built three weekly AI readouts, each a Claude skill that queries its sources, reconciles, writes the analysis, renders a hosted page, and delivers it: forecast movement (C-suite and revenue leadership), MQL disposition (heads of Demand Gen and SADR), and rep call activity (frontline sales managers)
2. Saves 3 hours per week of manual report prep (user-confirmed 2026-10-08; replaces source placeholder)
3. Reconciliation gates block publishing on any variance: forecast deal-level contributions must sum to each category's weekly change within $0.01 across all five categories; MQL counts must agree three ways across raw CRM stage stamps, mart intervals, and counted MQLs
4. One definition per metric across all three readouts, ending figure drift between audiences
5. Forecast readout runs as a scheduled task (Mondays 7am ET) with no manual trigger; delivers a fixed-URL hosted page, a Playwright PDF, and a three- or four-line Slack summary
6. Every output states its base and filters, date-stamps its counts, and closes with a high/medium/low data confidence level and reason; finished pages are scanned against house style before publishing
7. Coverage bands carry a state word ("covered," "watch," "thin") alongside color for color-vision accessibility

## Novelty Claims
- None claimed in source. Distinctive element: trust controls treated as a design requirement (the run halts rather than publishing an unreconciled number)

## Collaboration & Scope
- **Other groups:** Florence's data team maintains the shared Snowflake analyst skill (connection details, schema map, known query traps). Executives approved business rules (coverage bands, deal caps)
- **User's specific contribution:** Designed and built all three readouts: query sets, business rules, reconciliation gates, rendering, scheduling, and delivery
- **Shared vs. sole work:** Readouts are sole-built; the warehouse access layer and dbt marts are not the user's work

## Provenance Notes
- **Publication status:** N/A — internal system
- **Safe to claim:** Full-ownership verbs (Built, Designed, Automated) for the readouts and their controls; "3 hours per week" time savings
- **Needs hedging:** Data layer — readouts were "built on" Snowflake; never claim to have built the access layer or marts
- **Do NOT claim:**
  - Board or investor delivery (source "[board/investors]" is unconfirmed; board reporting is a separate achievement, FL-14)
  - The source's "[2-4 hours per week]" range
  - Do not cite this 3 hours/week alongside the MQL readout's 2–3 hours/week in the same document (overlap unconfirmed)

## Resume Bullet Seeds
1. Built an AI executive reporting system on Snowflake and Claude that delivers weekly forecast, MQL disposition, and rep call readouts to C-suite leaders and frontline sales managers, saving 3 hours per week of manual prep.
2. Designed reconciliation gates that stop AI-generated forecast reporting from publishing when deal-level movement fails to sum to category totals within $0.01, with a stated data confidence level on every readout.
3. Replaced manual, multi-source leadership reporting with three scheduled AI readouts that share one definition per metric, ending figure drift between audiences.
