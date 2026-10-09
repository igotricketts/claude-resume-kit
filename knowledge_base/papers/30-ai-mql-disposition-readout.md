# MQL Disposition Readout

> Designed a weekly MQL disposition readout for Demand Gen and SADR leadership using cohort benchmarks and a fixed 7-day maturity window. It lifted 24-hour SLA adherence on marketing-sourced leads [25% / 25 points], sustained for [period], and saved RevOps and Marketing 2-3 hours per week each.

## The problem

Demand Gen and the SADR team each read MQL performance from their own reports, and the reports disagreed. Volume, pickup speed, and loss reasons lived in separate places with different date bases. Current-state disposition made older cohorts look better than recent ones, since they had more time to convert. Lost leads were analyzed by picklist value alone, so nobody could tell whether a lead was lost because no one reached it or because it was disqualified. And when a finding pointed at a problem, it was unclear which team owned the fix.

## What it does

Each week the readout takes the most recent complete Monday-to-Sunday cohort of counted MQLs and reports how they were dispositioned, against a benchmark of prior weeks. It publishes as a hosted page in nine sections:

1. **Masthead** with cohort dates, counted MQLs, data freshness, and cohort age.
2. **Verdict** in two or three sentences, leading with what moved.
3. **Six stat tiles**, each with its norm and a severity marker: counted MQLs, 24-hour pickup, median hours to first touch, worked within 7 days, still untouched, and recycled or rejected.
4. **Trend charts** for 24-hour pickup and worked within 7 days across roughly 16 weeks, with a dashed norm line, so a multi-week drift is visible.
5. **Segment breakdown** across enterprise sponsor/CRO, SMB sponsor/CRO, research site, and unsegmented, each rate paired with its segment norm.
6. **Cohort table** listing every MQL by hours to first touch, with the highest-value untouched lead flagged as the single action for the day.
7. **Loss reasons**, split by whether the lead was worked before it was lost. Leads the SADR team worked but could not reach, and leads disqualified without being worked, are different problems with different owners.
8. **Decisions needed**, numbered and tagged to SADR, Demand Gen, both, or RevOps.
9. **Method and caveats**, closing with a data confidence line for each class of claim.

Where findings split by owner, a two-panel block lets each leader read their own column. Demand Gen owns volume, mix, and intake quality. The SADR team owns pickup speed, working rate, and disposition discipline.

## Data sources

| Source | Used for |
|---|---|
| Snowflake marketing funnel mart | Counted MQLs, stage timestamps, SLA compliance, disposition, recycle reasons, segment |
| Snowflake MQL contact history mart | MQL intervals for reconciliation |
| Raw Salesforce contact stage history (replicated to Snowflake) | Independent count of MQL stage stamps, and verification of suspicious stage moves |

The date basis is the moment a contact entered the MQL stage. Lead-created and marketing automation dates are never used.

## How it's built

**Six-query set.** The skill defines each query: a weekly shape check that catches re-score spikes, cohort detail, cohort versus benchmark by segment and in aggregate, weekly trend series, recycle reasons over the trailing window, and a reconciliation query.

**Benchmark construction.** The benchmark is the 11 complete weeks before the cohort, always excluding one known week when a manual re-score inflated counted MQLs to roughly six times normal volume. Segment norms divide each segment's benchmark count by 11, since dividing by the number of weeks a segment appeared would inflate the norm for thin segments.

**Maturity control.** Every rate compared across weeks uses a fixed 7-day window from each MQL's stage entry. A four-day-old cohort is never compared to a ten-week-old one on current state.

**Reconciliation, every run.** Three counts must agree, or the difference is identified and explained: raw MQL stage stamps from CRM history, MQL intervals in the history mart, and counted MQLs in the funnel mart. Raw stamps routinely exceed counted MQLs because some lead sources (such as product signups) are excluded from the funnel by design. The readout names those contacts and says so.

**Rendering.** The page uses a fixed visual system (typefaces, palette, light and dark tokens) lifted from the previous week's page, so the series reads consistently. Charts are hand-built SVG. Before publishing, the page is screenshotted in both themes and checked for overflow at phone width and for label collisions. Each week publishes to a new URL, building an archive.

## Data traps it handles

These are documented in the skill because each one has distorted the report at least once.

**Dead activity fields.** Call, email, and meeting counts read zero across nearly every recent cohort because an upstream activity sync stopped. The readout never reports outreach effort from those fields. Time to first touch, taken from stage history, is the proxy, and the method notes say so every week.

**Synthetic rows.** Rows created by an anchoring process swing wildly week to week. They are filtered out, and the shape check flags any spike because it would distort unfiltered funnel queries for the same week.

**Automation loops.** Some contacts bounce out of Working and back within minutes, an automation artifact that corrupts the working outcome field. Any backward move is verified against raw stage history before it is read as real.

**Small samples.** Enterprise and unsegmented groups often carry one to three MQLs, where a single record moves a rate by 25 to 50 points. The readout reports direction only for those groups and labels the confidence.

**Immature cohorts.** Zero conversions at the SADR-qualified stage for a cohort under two weeks old reflects maturity, and the readout labels it that way.

## Impact

| Measure | Result |
|---|---|
| 24-hour SLA adherence, marketing-sourced leads | [+25% relative / +25 points], from [baseline] to [current] |
| Durability | Sustained week over week for [period] |
| Analysis time | 2-3 hours per week saved in RevOps and 2-3 in Marketing, previously spent reconciling disparate reports |
| Finding surfaced | Worked leads lost to "no contact" were the largest single loss reason across every readout, with no named owner. [Action taken and result] |

## Design decisions

**Built on demand first.** The skill ran on demand for several readouts before any schedule was considered, so the format could settle with its two readers.

**Archive by week.** Each readout gets its own page, because the leaders' questions are about trends across weeks.

**Ask before calling a trend.** When a new recycle reason starts trending up, the readout flags it and asks whether it reflects a real change or a new rep habit before naming it either.

**Terminology enforced.** The team was renamed from BDR to SADR, and the readout uses the current name in all prose while leaving literal data values untouched.

## Interview angle

**Question it answers:** "Tell me about a time data changed how two teams worked together."

Marketing and the SADR team each had their own view of MQL performance, and the views disagreed. I built a weekly readout with one date basis, one benchmark, and a fixed maturity window, reconciled against raw CRM history every run. It split lost leads into reachability failures and qualification calls, and gave each team its own column of actions. It surfaced that worked leads lost to "no contact" were our largest loss category with no owner. 24-hour SLA adherence rose [25%] and held for [period], and both teams got 2-3 hours a week back.

## Skills demonstrated

Funnel analytics, cohort analysis and benchmarking, cross-functional alignment between marketing and sales development, data quality management, SQL, executive reporting.
