# How Clay Works (Production System Documentation)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026 (documentation dated June 24, 2026)
- **Venue:** Internal technical documentation — Florence Healthcare
- **User's role:** Sole architect/owner and documenter
- **Status:** internal, live in production

## Methods & Tools
- **Computational methods:** Waterfall data enrichment logic, AI identity-verification gating, prompt-based content generation
- **Software/frameworks:** Salesforce (Account/Contact objects), Clay, ClinicalTrials.gov API
- **Key techniques:** Three-gate human-in-the-loop system design, daily automated multi-stage pipeline, rubric-based AI scoring, SOQL query design, prompt inventory documentation

## Key Results
1. Built a daily automated pipeline (5am account enrichment, 6am contact enrichment, 7am cadence drafting) delivering a fully drafted outbound kit within ~24 hours of opt-in
2. Engineered account enrichment against ClinicalTrials.gov's API with AI synthesis into a 6-section portfolio summary and a rubric-based 0-10 priority score
3. Designed identity-verification AI gates confirming enriched LinkedIn profiles belong to the correct contact before any Salesforce write-back
4. Built a "seven-resource outbound kit" generator: 5 sequenced emails, a LinkedIn invite, a cold-call cheat sheet, and internal QA rationale
5. Live production system governing enrichment across two Salesforce objects and one cadence-drafting table, with zero direct rep tool exposure (Salesforce checkboxes/list views only)

## Novelty Claims
- First AI-driven, human-in-the-loop CRM enrichment/personalization production system at the org, with identity-verification and write-back governance built in from the start

## Collaboration & Scope
- **Other groups:** N/A for architecture/build — documentation notes forward design for a future Slack-approval-gated feature
- **User's specific contribution:** Sole architect, builder, and technical documenter of the production system
- **Shared vs. sole work:** Entirely sole-ownership

## Provenance Notes
- **Publication status:** N/A — internal technical documentation
- **Safe to claim:** Full-ownership verbs (Architected, Designed, Built, Engineered) — this is a system the user personally designed and documented
- **Needs hedging:** None
- **Do NOT claim:** N/A

## Resume Bullet Seeds
1. Architected and documented a production AI enrichment and personalization system integrating Salesforce, ClinicalTrials.gov, and multiple data-waterfall providers, running fully automated daily on a three-stage pipeline with human approval gates at every stage.
2. Designed identity-verification and write-back governance logic (never overwrite verified data, confirm identity before writing) to make an AI-driven data pipeline safe to run against production CRM.
3. Built an AI-generated "seven-resource outbound kit" system (sequenced emails, LinkedIn invite, call cheat sheet, QA rationale) with explicit voice rules to maximize reply rates while keeping every send human-reviewed.
