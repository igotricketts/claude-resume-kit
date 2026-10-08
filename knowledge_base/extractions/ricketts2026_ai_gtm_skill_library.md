# GTM Skill Library (10 Claude Skills for SADR, AE, and Leadership Teams)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI program, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/32-ai-gtm-skill-library.md`)
- **User's role:** Sole creator; deployed to SADR, AE, and leadership teams
- **Status:** internal, deployed

## Methods & Tools
- **Operational frameworks:** AI adoption and change management, knowledge management (team methods encoded once, applied the same way every time), sales enablement
- **Software/platforms:** Claude Skills, Claude Cowork, MCP connectors (Snowflake, Salesforce, Gong, Slack, ClinicalTrials.gov), Python
- **Key techniques:** Uniform packaging standard (skill directory plus reference files, packaging validator, trigger description under the 1,024-character limit); trigger descriptions written for recall using reps' natural phrasings and naming the neighboring skill for adjacent requests; substance in reference files and workflow in the skill file; deterministic steps (date math, workbook construction, data synthesis) in Python; house style built in (American spelling, no em dashes, no antithesis phrasing, Florence number formatting)

## Key Results
1. Created and deployed 10 Claude skills: account intent, CRO partnership signal, intent workup, sponsor trial portfolio, 3-option outbound, Salesforce record links (CRM integrity), client-facing communications, forecast movement readout, MQL disposition readout, rep call readout
2. Reached >85% adoption across SADR and AE teams (user-confirmed 2026-10-08; replaces source "[N] reps")
3. Replaced individual, inconsistent prompting with one research standard, one claims library, and one voice across reps
4. Prospecting skills form an explicit handoff chain (intent research → portfolio research → outbound copy), with each skill declining out-of-scope work and passing context forward
5. Downstream results: account intent framework influenced $1M in ARR pipeline (ricketts2026_ai_account_intent_framework.md); reply-rate result pending confirmation (ricketts2026_ai_outbound_copy_system.md)

## Novelty Claims
- None claimed in source

## Collaboration & Scope
- **Other groups:** SADR, AE, account leadership, Demand Gen, and sales leadership are the users. Reporting skills query Snowflake through the data team's shared analyst skill
- **User's specific contribution:** Created and deployed all 10 skills and set the packaging and house-style standards
- **Shared vs. sole work:** Sole creator; data-access layer is the data team's

## Provenance Notes
- **Publication status:** N/A — internal program
- **Safe to claim:** Full-ownership verbs (Created, Deployed, Built); "10 Claude skills"; ">85% adoption across SADR and AE teams"
- **Needs hedging:** Data layer, per config.md
- **Do NOT claim:**
  - A named quarterly objective (source "[Q3 2026]" unconfirmed)
  - A rep headcount for adoption; use the percentage only
  - Do not double-count the intent framework's $1M pipeline as a separate library result on the same resume

## Resume Bullet Seeds
1. Created and deployed a library of 10 Claude skills for SADR, AE, and leadership teams covering account intent research, trial portfolio analysis, outbound copy, CRM guardrails, executive communications, and weekly readouts, reaching >85% adoption across SADR and AE teams.
2. Standardized AI use across sales teams by encoding research methods, approved claims, and CRM rules once in shared reference files, so output quality no longer depended on who wrote the prompt.
