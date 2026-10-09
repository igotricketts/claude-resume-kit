# Forecast Movement Readout

> Automated forecast movement analysis that traces every week-over-week category change to named deals and root causes (pushes, pull-ins, re-scopes, record splits), including repeat-pusher close date history.

Part of the [executive reporting system](../01-executive-reporting-system.md).

## What it answers

Every Monday at 7am ET, leadership gets four answers: where the current quarter stands by forecast category (Closed, Commit, Best Case, Pipeline), what changed since last Monday, which specific deals caused each change and why, and whether next quarter's pipeline covers its target by segment.

## Method

**Two snapshots, one join.** The readout compares the most recent daily opportunity snapshot to the snapshot seven days earlier, using a full outer join so deals that appeared or disappeared are both captured. Each deal is flagged for whether it sits inside the current quarter and inside forecast scope on each date. A category's weekly change is the in-quarter total for that category this week minus the same total last week.

**Movement classification.** Every deal that moved is assigned a cause:

| Cause | How it is detected |
|---|---|
| Pushed out of quarter | Close date moved past quarter end |
| Pulled into quarter | Close date moved inside the quarter |
| New opportunity | Absent from the prior snapshot |
| Left forecast scope | In scope last week, out of scope this week |
| Category migration | Forecast category changed |
| ARR restated | Bookable ARR changed with category unchanged |
| Record split | Offsetting pair of changes on one account |

**Repeat pushers.** For any deal that pushed or was materially re-scoped, the readout pulls its full close-date history for the year and lists each change. A deal on its fourth push reads very differently from one on its first, and this is where the most useful insight in the report usually sits.

**Top movers.** Each category lists up to five movers by current-week bookable ARR, with the total count of movers stated.

**Next quarter.** Open pipeline by segment against target, as raw unweighted coverage. Coverage of 3x or more reads green ("covered"), 2x to 3x amber ("watch"), and under 2x red ("thin"). The state word always appears with the color.

## Reconciliation gate

Deal-level contributions must sum to each category's weekly change within $0.01, for all five categories including Omitted. If any category fails, the run stops and the gap is investigated before anything is published. This is the control that makes deal-level attribution trustworthy: every dollar of movement is accounted for by a named deal.

## Page structure

Masthead with as-of date, comparison date, and days left in the quarter. A one-line verdict leading with Closed won plus Commit. Four position tiles: Closed won plus Commit, open forecast, booked to date, and coverage on the remaining gap. A waterfall showing the week as two or three named drivers plus a residual. A category ledger. Every deal that moved, with its cause. Next-quarter coverage by segment. A basis footer stating which ARR basis was used, since booked-to-date differs between the opportunity basis and the quote-line basis.

## Delivery

The page updates in place at a fixed URL so executive bookmarks keep working. A PDF export uses a print stylesheet (two-column stat grid, tables fitted to letter width, page breaks that never split a deal card) rendered with Playwright, and every page is rendered to an image and inspected before delivery. A Slack post carries the link and a three or four line summary: Closed won plus Commit and its weekly change, the one or two deals that drove it, and anything genuinely at risk.

## Design choices

Prior targets in the CRM can lag the live plan, so the readout supports a documented plan override until goal records are updated. Executive feedback removed a mix-shift column, explanatory chart captions, and commentary on omitted deals, because none of them changed a decision.

## Interview angle

"Forecast reviews stall when nobody can say why a category moved. The readout names every deal behind every change before the meeting starts, and it will not publish unless those deals add up to the total to the cent. The repeat-pusher history turned out to be the most valuable part: it shows which deals have slipped three or four times, and those deals call for a harder conversation."
