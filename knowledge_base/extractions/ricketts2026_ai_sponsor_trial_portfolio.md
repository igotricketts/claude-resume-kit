# Sponsor Trial Portfolio Research (ClinicalTrials.gov Workflow)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI skill, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/36-ai-sponsor-trial-portfolio.md`)
- **User's role:** Sole designer and builder; part of the GTM skill library (ricketts2026_ai_gtm_skill_library.md)
- **Status:** internal, live

## Methods & Tools
- **Operational frameworks:** Account sizing via public proxy (site footprint as the closest public measure of a sponsor's trial operations workload)
- **Software/platforms:** ClinicalTrials.gov (MCP connector), Claude Skills; structured JSON output
- **Key techniques:** Exact registered lead-sponsor name resolution; strict normalized sponsor filter with rejection counts reported; trial design detection (adaptive, platform, basket, umbrella); site-density ranking; length guard that drops the smallest ongoing and oldest completed studies first and marks truncation

## Key Results
1. Six-step workflow: resolve sponsor name, 3–5 operationally relevant pipeline news items from the last 90 days (each with a verified on-page date), all ongoing trials (paginated to 100), site locations (25 largest by enrollment when more), trials completed or terminated in the last 90 days, synthesis
2. Produces a full registry report and a six-section portfolio summary (snapshot, therapeutic areas, modality, study type and phase, scale and geography, representative studies) drawn only from retrieved data, with counts that must match the report header
3. Location asymmetry rule: completed trials never enter any site total, share, or density figure, since locations are pulled only for ongoing studies
4. Supplies the trial footprint that grounds the outbound copy system's registry-based angles; receives routed accounts from the account intent framework

## Novelty Claims
- None claimed in source

## Collaboration & Scope
- **Other groups:** SADRs and AEs are the users
- **User's specific contribution:** Designed the workflow and data rules
- **Shared vs. sole work:** Entirely sole-ownership
- **Overlap note:** The Clay production system (FL-08) also enriches accounts from ClinicalTrials.gov on a daily schedule. This is a separate on-demand Claude workflow; do not present them as one system

## Provenance Notes
- **Publication status:** N/A — internal skill
- **Safe to claim:** Full-ownership verbs (Built, Designed)
- **Needs hedging:** None
- **Do NOT claim:** Research-time reduction or number of sponsors profiled (source placeholders unconfirmed)

## Resume Bullet Seeds
1. Built a sponsor research workflow that profiles a company's active trials, pipeline news, and site footprint from ClinicalTrials.gov, with strict sponsor-name matching and site totals limited to ongoing studies.
