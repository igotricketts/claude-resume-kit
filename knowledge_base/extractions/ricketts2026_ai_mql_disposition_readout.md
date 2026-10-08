# MQL Disposition Readout (Weekly Cohort Readout for Demand Gen and SADR)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI system, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/30-ai-mql-disposition-readout.md`)
- **User's role:** Sole designer and builder; part of the executive reporting system (ricketts2026_ai_exec_reporting_system.md)
- **Status:** internal, live (weekly)

## Methods & Tools
- **Operational frameworks:** Cohort analysis with fixed maturity windows, benchmark construction, owner-split decision framing (Demand Gen owns volume, mix, and intake quality; SADR owns pickup speed, working rate, and disposition discipline)
- **Software/platforms:** Snowflake marketing funnel mart, MQL contact history mart, raw Salesforce contact stage history replicated to Snowflake; SQL; Claude Skills; hosted artifacts with hand-built SVG charts
- **Key techniques:** Six-query set (shape check, cohort detail, cohort vs. benchmark by segment, trend series, recycle reasons, reconciliation); 11-week benchmark excluding a known re-score week; segment norms divided by 11 to avoid inflating thin segments; date basis is MQL stage entry only

## Key Results
1. Weekly readout of the most recent complete Monday–Sunday MQL cohort against an 11-week benchmark, published as a nine-section hosted page (verdict, six stat tiles with norms, ~16-week trend charts, segment breakdown, cohort table, loss reasons, owner-tagged decisions, method and caveats)
2. Cut MQL pickup time 25% (user-confirmed 2026-10-08; replaces the source's "24-hour SLA adherence" placeholder)
3. Saved 2–3 hours per week each in RevOps and Marketing previously spent reconciling disparate reports (stated in source)
4. Fixed 7-day maturity window from each MQL's stage entry for all cross-week rates, so young cohorts are never compared to mature ones on current state
5. Three-way reconciliation every run: raw CRM MQL stage stamps, mart intervals, and counted MQLs must agree or the gap is named and explained
6. Split lost leads by whether they were worked before loss; surfaced worked leads lost to "no contact" as the largest single loss reason across every readout, with no named owner
7. Documented data traps that each distorted the report at least once: dead activity sync fields, synthetic anchoring rows, automation stage loops, small-sample segments (direction-only reporting), immature cohorts

## Novelty Claims
- None claimed in source. Distinctive element: one date basis and one benchmark shared by two teams that previously read MQL performance from conflicting reports

## Collaboration & Scope
- **Other groups:** Readers are the heads of Demand Gen and SADR; the format settled with them over several on-demand runs. Data team's shared Snowflake analyst layer
- **User's specific contribution:** Designed the cohort method, benchmark, maturity control, reconciliation, page structure, and owner framing
- **Shared vs. sole work:** Sole-built on the data team's warehouse layer

## Provenance Notes
- **Publication status:** N/A — internal system
- **Safe to claim:** Full-ownership verbs; "cut MQL pickup time 25%"; "2–3 hours per week each in RevOps and Marketing"
- **Needs hedging:** Data layer, per config.md
- **Do NOT claim:**
  - "24-hour SLA adherence" lift or "percentage points": the user's confirmed metric is pickup time
  - Any duration for the gain (source "[period]" unconfirmed)
  - That the "no contact" finding led to a specific action or result (source "[Action taken and result]" unconfirmed). Cite the finding on its own
  - Do not cite 2–3 hours/week alongside the reporting system's 3 hours/week in the same document

## Resume Bullet Seeds
1. Designed a weekly MQL disposition readout for Demand Gen and SADR leadership with an 11-week cohort benchmark and fixed 7-day maturity window, cutting MQL pickup time 25%.
2. Split lost-lead analysis into reachability failures and qualification calls with owner-tagged actions, surfacing "no contact" on worked leads as the largest loss reason across every readout.
3. Replaced conflicting Marketing and SADR funnel reports with one date basis reconciled against raw Salesforce stage history every run, saving 2–3 hours per week each in RevOps and Marketing.
