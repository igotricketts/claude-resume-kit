# Worked Narrative: AI-Driven GTM Systems (Reporting Loop and Prospecting Loop)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Portfolio overview of AI work at Florence Healthcare (source: `knowledge_base/papers/27-ai-gtm-systems-overview.md`)
- **User's role:** Sole author; synthesizes ricketts2026_ai_exec_reporting_system.md, ricketts2026_ai_account_intent_framework.md, ricketts2026_ai_mql_disposition_readout.md, ricketts2026_ai_outbound_copy_system.md, ricketts2026_ai_gtm_skill_library.md, and the five supporting-skill extractions
- **Status:** internal narrative synthesis — not a new project, use for interview/narrative framing only

## Methods & Tools
- **Operational frameworks:** Two connected loops. The reporting loop turns warehouse data into weekly leadership decisions; the prospecting loop turns public buying signals into prioritized accounts and then outreach, with each skill handing its output to the next
- **Software/platforms:** Claude Skills (packaged skill files with reference documents and Python scripts), Claude Cowork, scheduled tasks, hosted artifacts, Claude in Chrome; MCP connectors for Snowflake, Salesforce, Gong, Slack, and ClinicalTrials.gov; SQL on dbt-modeled Snowflake marts; Python (openpyxl, Playwright); Clay for enrichment routing
- **Key techniques:** Five recurring design principles: validate before codifying, keep one source of truth, reconcile before publishing, state what the data cannot say, write for the decision

## Key Results
See the source extractions for granular metrics. This file's contribution is the connective narrative and the shared design principles:
1. Validate before codifying: every criterion and query was tested against live accounts and real data before it became a skill; two intent criteria were shelved for lack of a reliable public source
2. One source of truth: criteria, exclusion lists, and house style each live in one reference file that orchestrators read directly
3. Reconcile before publishing: reports carry hard reconciliation gates that stop a run on any variance
4. State what the data cannot say: outputs separate "not found" from "could not check," carry explicit confidence levels, and label small samples
5. Write for the decision: every readout leads with a verdict, ties findings to an owner, and ends with actions

## Novelty Claims
- N/A — narrative framing device, not a project

## Collaboration & Scope
- **Other groups:** Florence's data team maintains the shared Snowflake analyst skill (connection handling, schema map, documented query traps) that the reporting skills query through. Source states: "That layer ... is their work. The systems in this repo are built on top of it."
- **User's specific contribution:** Designed and built the reporting and prospecting systems on top of that data layer
- **Shared vs. sole work:** Systems are sole-built; the data-access layer is the data team's

## Provenance Notes
- **Publication status:** N/A — internal work, documented in a portfolio write-up the user has cleared for public sharing (2026-10-08)
- **Safe to claim:** Use for interview answers and cover-letter framing about building trustworthy AI systems in GTM
- **Needs hedging:** Any reference to the Snowflake data layer: "built on" the warehouse, never "built the warehouse layer"
- **Do NOT claim:**
  - The source README gives the title "VP of Revenue Operations & Outbound Sales." This is incorrect per the user. The title is **Sr. Director, Revenue Operations** (config.md KB Corrections Log)
  - Do not treat this file as a separate resume line item, and do not double-count metrics alongside its source extractions

## Resume Bullet Seeds
1. Built a connected set of AI GTM systems on Claude, Snowflake, and Salesforce: a reporting loop that turns warehouse data into weekly leadership decisions and a prospecting loop that turns public buying signals into prioritized accounts and outreach.

_Note: This is a narrative/interview-prep synthesis of already-extracted projects, not an independent achievement. Use for STAR-format interview answers and CL "AI adoption" framing rather than as a standalone resume bullet source._
