# Executive Reporting System

> Built an AI-driven executive reporting system on Snowflake and Claude that delivers weekly forecast, MQL disposition, and rep call readouts to C-suite leaders, frontline sales managers, and [board/investors]. Reconciliation gates block publishing on any data variance, and the system saves [2-4 hours per week] of manual prep.

## The problem

Weekly leadership reporting depended on manual pulls from disparate reports, assembled by hand for each audience. Prep time grew with every audience added. Figures drifted between reports because each pull applied slightly different filters. And the reports described what happened without explaining why, so leadership meetings spent their opening minutes reconstructing the week before anyone could make a decision.

## What it does

Three readouts run on a weekly cadence. Each is a Claude skill that queries its source systems, runs reconciliation checks, writes the analysis, renders a hosted page, and delivers it to its audience.

| Readout | Audience | Cadence | Source data | Delivery |
|---|---|---|---|---|
| Forecast movement | C-suite and revenue leadership | Mondays at 7am ET, scheduled | Snowflake daily opportunity snapshots and goal attainment mart | Hosted page at a fixed URL, PDF, Slack channel summary |
| MQL disposition | Heads of Demand Gen and SADR | Weekly | Snowflake marketing funnel and MQL history marts, raw Salesforce stage history | New hosted page each week, forming a browsable archive |
| Rep call activity | Frontline sales managers | Weekly | Gong, read through browser automation | Slack, sent only after approval |

Detail on each: [forecast movement](supporting/forecast-movement-readout.md), [MQL disposition](03-mql-disposition-readout.md), [rep call activity](supporting/rep-call-readout.md).

## How it's built

The system has four layers.

**Data access.** Warehouse queries run through a Snowflake MCP connector, using a shared analyst skill maintained by the data team for connection details, schema map, and known query traps. Every query names its tables in full and opens with a `WITH` clause so the tooling never appends a silent row limit. Result sets too large for the context window are written to a file and processed in Python.

**Report logic.** Each readout is its own `SKILL.md`: the query set, business rules (cohort definitions, scope filters, benchmark windows), the page structure, and the house style. Business rules that executives had to approve, such as coverage color bands or the cap of five deals per forecast category, are written into the skill so every run applies them the same way.

**Rendering.** Output is a hosted HTML page with a consistent visual system per readout, full light and dark themes, and hand-built inline SVG charts. The forecast page updates in place at a fixed URL so executive bookmarks keep working. The MQL readout publishes a new page each week so leaders can browse the series.

**Delivery.** The forecast readout runs as a scheduled task bound to a desktop device, because the Snowflake connector runs through that device link. It exports a PDF with Playwright using a dedicated print stylesheet, then posts a three or four line Slack summary that leads with Closed won plus Commit and its weekly change. Before delivery, each PDF page is rendered to PNG and inspected; this step has caught layout bugs invisible on the web page.

## Trust controls

AI-generated reporting earns trust only when it can prove its numbers. Each readout carries controls that stop a run before a bad number reaches an executive.

| Control | Readout | What it enforces |
|---|---|---|
| Delta reconciliation | Forecast | Deal-level contributions must sum to each forecast category's weekly change within $0.01, across all five categories. Any failure halts publishing. |
| Three-way count reconciliation | MQL | Raw CRM stage stamps, mart intervals, and counted MQLs must agree, or the gap is identified and explained. |
| Maturity control | MQL | Cross-week rates use a fixed 7-day window from each MQL, so young cohorts are never compared to mature ones. |
| Attendee verification | Rep call | Calls flagged as multi-party are opened and checked before exclusion, since Gong can count an unresolved phone number as a person. |
| Confidence statement | All | Every output states its base and filters, date-stamps its counts, and closes with a data confidence level (high, medium, or low) and the reason. |
| House style check | All | Finished pages are scanned for em dashes, British spellings, and antithesis phrasing before publishing. |

## Impact

| Measure | Result |
|---|---|
| Manual prep time | [2-4 hours per week] saved |
| Audiences served | C-suite leaders, frontline sales managers, [board/investors] |
| Consistency | One definition per metric across all three readouts |
| Reliability | Forecast readout runs on schedule with no manual trigger |

## Design decisions

**Write at executive depth.** Every readout opens with a one-line verdict. Deal lists are capped, multi-sentence summaries become bullets, and anything that does not change a decision (mix-shift columns, explanatory chart captions) was cut.

**Approve the format before automating it.** Each readout ran on demand several times while the format was refined. A schedule was attached only after the output was approved.

**Match delivery to how each audience reads.** Executives get a stable URL they can bookmark. Demand Gen and SADR leaders get an archive, since their questions are about trends across weeks. Coaching material goes to a private channel because it names individual reps.

**Design for accessibility.** Coverage bands carry a state word ("covered," "watch," "thin") alongside the color, because amber and red are hard to separate under color-vision deficiency in dark mode.

## Interview angle

**Question it answers:** "How do you get executives to trust AI-generated reporting?"

Leadership reporting was manual and the numbers drifted between versions. I built three AI readouts on top of our Snowflake warehouse, and I treated trust as a design requirement from the start. Each one reconciles its own numbers before it publishes, and the forecast readout refuses to run if deal-level detail misses the category totals by a cent. Every output states its confidence level. The result was [2-4 hours per week] back, and leadership meetings that start on decisions.

## Skills demonstrated

Revenue analytics and forecasting, SQL on dbt-modeled marts, AI workflow design, data governance and reconciliation, executive communication, report automation and scheduling.
