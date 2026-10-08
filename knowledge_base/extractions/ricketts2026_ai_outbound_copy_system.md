# Outbound Copy System (Three-Option AI Outreach)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI system, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/31-ai-outbound-copy-system.md`)
- **User's role:** Sole designer and builder
- **Status:** internal, live

## Methods & Tools
- **Operational frameworks:** Outbound messaging strategy, buyer-tier and seat-based value mapping (large pharma, mid-cap, emerging biotech, CRO), goal tuning (reply, open, click, event attendance), claims governance
- **Software/platforms:** Claude Skills (skill workflow plus two reference files: copywriting guidelines and a verified facts library), enriched Salesforce contact descriptions, ClinicalTrials.gov footprint data, contact CSVs
- **Key techniques:** "Nerve" and "seat read" stated before writing; angle selection from a repertoire of nine email and six LinkedIn angles by situation; banned problem words and AI-pattern bans (dashes, antithesis, rule-of-three cadence, stock phrases, hype, emoji, false urgency); LinkedIn invites at or under 300 characters with count reported; rule-by-rule self-check before returning

## Key Results
1. Returns three ready-to-send options per prospect (cold email or LinkedIn invite), each a different strategy with a differently shaped question and a one-line rationale for the rep
2. Verified facts library: at most one proof point per email, no invented numbers, never names the customer behind a proof
3. Grounding rules: every prospect fact traces to supplied intel; thin intel produces shorter, plainer copy; inconsistent figures get the conservative framing or are dropped; never references whether trial results were posted
4. Tightened guidelines after testing on live trial portfolio data (assume no prior relationship, one signal per message)
5. Receives buyer persona tags from the account intent framework and trial footprints from sponsor trial portfolio research
6. Reply rate: user reports "30% reply rates" (source: within 60 days). **PENDING:** unconfirmed whether this is an absolute reply rate or a relative lift (see config.md)

## Novelty Claims
- None claimed in source

## Collaboration & Scope
- **Other groups:** SADRs are the primary users
- **User's specific contribution:** Designed the workflow, angle repertoire, voice rules, facts library, grounding rules, and self-check
- **Shared vs. sole work:** Entirely sole-ownership
- **Overlap note:** Distinct from the Clay "seven-resource outbound kit" (ricketts2026_clay_production_system.md, FL-08), which is a daily table-driven drafting pipeline. This is an on-demand Claude skill. Avoid presenting both as the same system, and avoid two outbound-copy bullets on one resume unless the JD weights outbound heavily

## Provenance Notes
- **Publication status:** N/A — internal system
- **Safe to claim:** Full-ownership verbs (Built, Designed)
- **Needs hedging:** None
- **Do NOT claim:**
  - Any reply-rate figure until the user confirms absolute rate vs. relative lift
  - Sample size, baseline, or rep time savings (source placeholders unconfirmed)

## Resume Bullet Seeds
1. Built an outbound copy system that writes three distinct cold email or LinkedIn strategies per prospect from enriched CRM and ClinicalTrials.gov data, governed by a verified claims library and voice rules.
2. Wrote voice and grounding rules for AI-generated outreach (no invented numbers, one approved proof point per email, every prospect fact traced to supplied data) so SADR copy stays accurate and reads as written by a peer.

_Metric to append once confirmed:_ "...lifting reply rates 30% within 60 days" (if relative lift) or "...reaching 30% reply rates within 60 days" (if absolute rate).
