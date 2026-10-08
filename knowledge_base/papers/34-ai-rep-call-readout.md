# Rep Call Readout

> Automated Gong 1:1 call analytics for SADR coaching. Caught a call-classification artifact that would have understated one rep's activity by 75%.

Part of the [executive reporting system](../01-executive-reporting-system.md).

## What it answers

For each SADR, the readout turns a week of recorded phone activity into coaching material a manager can act on: a bottom-line verdict, a metrics table, what is working, what needs attention, one non-obvious pattern, and up to three actions doable that week. A call-by-call log is available in Gong already. The value of the readout is the pattern across calls.

## Scope rule

Only calls where the rep had exactly one other attendee count. Group demos, internal syncs, and buying-committee calls are a different motion and would wash out the prospecting signal. The readout always states how many calls it excluded and why.

## The artifact it caught

Gong displays attendees as a line such as "Rep + 2 more." Applied literally, "+ 2 more" means three people and the call should be excluded. In practice, when Gong cannot match a phone number to a CRM contact, it creates an unresolved speaker entity and counts it as a separate party. A plain dial to voicemail then renders as "+ 2 more" with only two humans involved.

The artifact clusters by rep, depending on their dialer and how clean their contact records are. In the first sample week it affected 12 of one rep's 16 dials and none of the other reps' calls. Applying the scope rule blindly would have removed three quarters of that rep's week and made an active rep look idle in a coaching document that reaches their manager.

The skill now opens a sample of any "+ 2 more" calls and checks the real participant roster before excluding them. Calls where the extra party is an unresolved phone entity are treated as 1:1 and included, and the readout states which convention it applied.

## Method

**Browser automation.** The Gong connector available in Claude is scoped to CRM accounts and deals, with no concept of a rep or an attendee count. The readout drives the Gong web interface through Claude in Chrome instead: participant filter, custom date range, every page of results, and individual call pages for calls with no AI summary. A short call with no summary is often a real connect, so those are opened and checked before classification.

**Classification.** Every included call is bucketed as a connect, a voicemail (noting whether a message was left), a no-connect, or a gatekeeper. Metrics: total 1:1 calls, connect rate, voicemail share, gatekeeper count, firm next steps, live talk time, median connect and voicemail durations, and pipeline touched.

**Patterns.** The readout looks for activity compressed into one block versus spread across the week, repeat dials to the same contact with no reply (a signal to switch channels), live opportunities worked like cold leads, objection arcs followed across several calls on one account, rehearsed language recurring across calls, short calls that produced real outcomes, and the longest call that produced nothing.

## Safeguards

**Approval before sending.** The readout is shown in full and sent to Slack only after explicit approval, since it names individual reps.

**Pronouns from a roster.** A team roster table supplies each rep's pronouns. The skill never infers them from a name and writes around pronouns for anyone missing from the table, because coaching documents get forwarded.

**Name collisions.** Several reps share first names with other employees and many external contacts, so the skill selects reps by title within the internal people list.

**Stated limits.** Voicemails are identified from summary text, attendee counts are read from the rendered page, and a quiet week is reported as thin. The browser route scales to about five reps. Beyond that, the right answer is the Gong API with credentials held in a proper secret store, which the skill documents as the next step.

## Interview angle

"The scope rule was simple: count only 1:1 calls. Applied literally, it would have erased three quarters of one rep's week, because Gong counts an unmatched phone number as a person. I caught it by opening the calls behind the number before trusting it. Knowing where a source system misleads you is most of the work in automating a report."
