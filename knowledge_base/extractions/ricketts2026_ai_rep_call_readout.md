# Rep Call Readout (Gong Call Analytics for SADR Coaching)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI system, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/34-ai-rep-call-readout.md`)
- **User's role:** Sole designer and builder; part of the executive reporting system (ricketts2026_ai_exec_reporting_system.md)
- **Status:** internal, live (weekly)

## Methods & Tools
- **Operational frameworks:** Call-level coaching analytics, scope rules (1:1 calls only), call classification (connect, voicemail, no-connect, gatekeeper)
- **Software/platforms:** Gong (web interface), Claude in Chrome browser automation, Claude Skills, Slack
- **Key techniques:** Browser automation across Gong's participant filter, date range, and result pages (the Gong connector had no rep or attendee scope); opening calls with no AI summary before classifying them; cross-call pattern detection; attendee-roster verification

## Key Results
1. Weekly per-SADR coaching readout for frontline managers: bottom-line verdict, metrics table (connect rate, voicemail share, gatekeepers, firm next steps, live talk time, median durations, pipeline touched), what is working, what needs attention, one non-obvious pattern, and up to three actions for the week
2. Caught a Gong call-classification artifact: unresolved phone numbers counted as a separate attendee, making plain dials read as multi-party calls. It affected 12 of one rep's 16 dials and would have understated that rep's activity by 75% in a document sent to their manager
3. Skill now opens a sample of flagged multi-party calls and checks the real roster before excluding any, and states which convention it applied
4. Pattern detection: compressed vs. spread activity, repeat dials with no reply, live opportunities worked like cold leads, objection arcs across calls, rehearsed language, short calls with real outcomes
5. Safeguards: full readout shown and sent to Slack only after explicit approval; pronouns taken from a team roster and never inferred from names; reps selected by title to avoid name collisions; stated limits (browser route scales to about five reps, Gong API with proper secret storage documented as the next step)

## Novelty Claims
- None claimed in source

## Collaboration & Scope
- **Other groups:** Frontline sales managers are the audience
- **User's specific contribution:** Designed the scope rule, classification, pattern library, safeguards, and caught the attendee artifact
- **Shared vs. sole work:** Entirely sole-ownership

## Provenance Notes
- **Publication status:** N/A — internal system
- **Safe to claim:** Full-ownership verbs; "would have understated one rep's call activity by 75%" (12 of 16 dials)
- **Needs hedging:** None
- **Do NOT claim:** That the readout scales across the whole sales org (source states about five reps via browser automation)

## Resume Bullet Seeds
1. Automated a weekly Gong call readout for SADR coaching that classifies every 1:1 call and surfaces cross-call patterns, catching a call-classification error that would have understated one rep's activity by 75%.
2. Built approval and privacy safeguards into AI-generated coaching readouts (manager sign-off before Slack delivery, pronouns from a team roster, stated data limits) for documents that name individual reps.
