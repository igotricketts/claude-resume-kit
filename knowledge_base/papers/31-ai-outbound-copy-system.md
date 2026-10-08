# Outbound Copy System

> Built an outbound copy system that generates three distinct strategies per prospect from enriched CRM data, governed by a verified claims library and voice rules. It lifted reply rates [30% / from X% to Y%] within 60 days.

## The problem

Cold outreach to clinical operations leaders fails in predictable ways. Generic copy gets ignored. AI-written copy is recognizable within a sentence and gets deleted. Copy built on public trial data can read as surveillance or criticism ("your activations are concentrated in one study"), which puts the reader on the defensive. And reps under volume pressure reach for unverified stats or name customers they are not approved to name.

The system needed to produce copy that sounds like a peer who did their homework, stays grounded in facts the rep can stand behind, and gives the rep a real choice of approach.

## What it does

For one prospect, the system returns three ready-to-send options, either cold emails or LinkedIn connection invites. Each option uses a different strategy and asks a differently shaped question, and each comes with a one-line rationale for the rep.

**Inputs.** The contact's enriched CRM description (role, company stage, ClinicalTrials.gov footprint with programs, phases, countries, site counts, and recent signals), or a contact CSV from which the rep picks rows. The rep also chooses the channel, the goal to optimize for (reply, open, click, or event attendance), and any Florence facts to feature.

**The read.** Before writing, the system states two lines for the rep. The nerve: the one thing this person answers to leadership for, such as a timeline, a cost line, or oversight across sites. The seat read: the value driver that fits the role and the buyer tier (large pharma, mid-cap, emerging biotech, or CRO).

**Angle selection.** The three angles are chosen to fit the contact, drawn from a repertoire of nine for email and six for LinkedIn.

| Situation | Angles that fit |
|---|---|
| Rich trial footprint | Registry read, cross-portfolio pattern, trajectory read |
| Thin intel | Operator reality, seat angle, peer comparison |
| Fresh signal (funding, new program, expansion, hire) | Signal-led |
| Goal is clicks | One asset-led option with a single link |
| Goal is event attendance | One event-led option with the registration ask |

**Goal tuning.** Reply is the default and strongest for cold outreach: a curious read and one easy, single-line question, with no link and no meeting ask. An open goal puts the work into three genuinely different subject lines and a strong first sentence. A click goal delivers the useful takeaway first, then one link. LinkedIn invites optimize for acceptance regardless of goal, and the system offers a follow-up message when a link is needed.

## How it's built

The skill is a `SKILL.md` workflow plus two reference files.

**Copywriting guidelines.** The governing rule is curiosity. Every observation reads as a peer who assumes the reader is good at their job and wants to hear how they run it. Words that imply a problem (risk, bottleneck, gap, behind, inefficient) are banned. The guidelines also ban the patterns that mark copy as machine-written: em and en dashes, antithesis constructions, rule-of-three cadences, stock cold-email phrases, hype words, emoji, exclamation points, and false urgency. Email bodies carry no salutation and no sign-off, since those are templated downstream. LinkedIn invites stay at or under 300 characters, with the count reported.

**Verified facts library.** Proof points, industry statistics, and downloadable assets the copy may cite, each matched to the seat and buyer tier it suits. The copy uses at most one proof point per email, never invents a number, and never names the customer behind a proof.

**Grounding rules.** Every fact about the prospect must trace to the supplied intel. Thin intel produces shorter, plainer copy. Internally inconsistent figures get the more conservative framing or are dropped. The copy never references whether a prospect's trial results have been posted, since that reads as compliance surveillance and is usually wrong.

**Self-check.** Before returning, the system verifies every rule: tone, banned patterns, distinct angles and question shapes, greeting and sign-off placement, character counts, proof-point limits, and traceability of every prospect fact.

**Refinements from testing.** After testing against live trial portfolio data, the guidelines were tightened to assume no prior relationship with the prospect and to use a single signal per message.

**Upstream connections.** The [account intent framework](02-account-intent-framework.md) passes a buyer persona tag when it finds a leadership hire, so the copy does not re-derive it. [Sponsor trial portfolio research](supporting/sponsor-trial-portfolio.md) produces the trial footprint that grounds registry-based angles.

## Impact

| Measure | Result |
|---|---|
| Reply rate | [+30% relative / from X% to Y%] within 60 days |
| Sample | [N] sends across [N] reps, compared against [baseline period or control group] |
| Rep time | [X minutes] per personalized message reduced to [Y minutes] |

## Design decisions

**Three options with rationale.** Reps choose the approach that fits what they know about the contact, which keeps judgment with the rep and teaches the reasoning over time.

**Situation picks the angles.** A fixed set of three would produce the same email structure for every prospect. The repertoire forces a fresh choice each time, and two angles that resolve to the same question count as one.

**Rules a reader can feel.** Each voice rule targets a specific reaction in the reader: defensiveness, the sense of a template, or the sense of being watched.

## Interview angle

**Question it answers:** "How have you used AI to improve sales development without making outreach feel automated?"

AI copy was easy to produce and easy to spot. I built a system that reads the prospect's trial footprint, names the one thing they answer to leadership for, and writes three different approaches the rep can choose from. Every fact traces to verified data, every claim comes from an approved library, and the voice rules strip out the patterns that mark copy as machine-written. Reply rates rose [30%] within 60 days.

## Skills demonstrated

Outbound strategy and messaging, sales development enablement, prompt and workflow design, brand and claims governance, experimentation and measurement.
