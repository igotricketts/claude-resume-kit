# Account Intent Framework (8 Public Buying-Signal Criteria)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI system, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/29-ai-account-intent-framework.md`)
- **User's role:** Sole designer and builder
- **Status:** internal, live

## Methods & Tools
- **Operational frameworks:** Signal-based prospecting, territory prioritization, suppression rules, three value drivers (accelerating clinical trials, mitigating risk and inspection readiness, improving productivity and capacity)
- **Software/platforms:** Claude Skills (three connected skills: account intent, CRO partnership signal, intent workup orchestrator), ClinicalTrials.gov, Python (date arithmetic; openpyxl for Excel output), Clay (routing for client-side-rendered careers pages), public sources (FDA databases, job boards, press, SEC filings)
- **Key techniques:** One reference file per criterion (hit definition, exclusions, search order, coverage limits); classifying each candidate criterion by extraction method (deterministic API pull, prompt-engineered search, no viable source) before building; evidence standard per claim (source URL, event date, verbatim quote under 25 words); five result states (FOUND, NOT FOUND, UNKNOWN, NOT APPLICABLE, NOT ENOUGH DATA); split retrieval vs. conclusion confidence, never averaged

## Key Results
1. Defined 8 public buying-signal criteria for clinical trial software: imminent early-phase trial readout, FDA regulatory action on clinical operations, clinical technology transformation hiring, new clinical operations leadership, funding/IPO/R&D increase, cost or efficiency initiative, new CRO partnership, insourcing or outsourcing shift
2. Influenced $1M in ARR pipeline within three months from accounts run through the framework (user-confirmed 2026-10-08)
3. Drove territory prioritization for strategic sellers
4. Suppression sweep runs on every workup (activist headcount mandates, programs transferred out, opex caps) and caps the recommendation even when positives are strong; transferred-out programs record the receiving organization as a related, often better, lead
5. Intent workup orchestrator runs all 8 criteria plus suppression on one account and writes a four-sheet Excel briefing (Summary, Signals, Related Accounts, Suppression)
6. Validated each criterion against live accounts before codifying; permanently shelved two (published RFPs, public ICH E6(R3) readiness statements) for lack of a reliable public source
7. Inverted the CRO partnership search (sweeping CRO newsrooms for named sponsor wins) after direct sponsor lookups produced little
8. A validation workup showed a Phase 2 primary completion date was public months before the R&D guidance announcing Phase 3 funding, which moved the trial-readout criterion to the front of every sponsor workup
9. Handoffs: leadership hires pass a buyer persona tag to the outbound copy system; portfolio-relevant accounts route to sponsor trial portfolio research

## Novelty Claims
- None claimed in source. Distinctive element: separates "nothing found" from "could not check," and weights negative results by how well each source is indexed

## Collaboration & Scope
- **Other groups:** Strategic sellers are the users
- **User's specific contribution:** Designed the criteria, exclusions, evidence standard, result states, suppression logic, and orchestration
- **Shared vs. sole work:** Entirely sole-ownership

## Provenance Notes
- **Publication status:** N/A — internal system
- **Safe to claim:** Full-ownership verbs (Developed, Designed, Built); "8 public buying-signal criteria"; "influenced $1M in ARR pipeline within three months"
- **Needs hedging:** The $1M is influenced pipeline, not sourced pipeline and not closed ARR
- **Do NOT claim:**
  - "$1M+", "sourced," or "generated $1M in ARR"
  - Number of accounts researched or research-time reduction (source placeholders unconfirmed)
  - The 2–6 month new-leader vendor re-evaluation window as a validated finding (source labels it a working heuristic)

## Resume Bullet Seeds
1. Developed an account intent framework of 8 public buying-signal criteria (FDA enforcement, clinical tech hiring, leadership changes, funding, CRO relationships, trial readouts) with suppression rules and confidence scoring, influencing $1M in ARR pipeline within three months.
2. Validated each intent criterion against live accounts before codifying it, shelving two with no reliable public source, and set an evidence standard (source URL, event date, verbatim quote) for every signal reps act on.
3. Built a one-account intent workup that runs all 8 criteria plus a suppression sweep and writes a four-sheet Excel briefing used for territory prioritization by strategic sellers.
