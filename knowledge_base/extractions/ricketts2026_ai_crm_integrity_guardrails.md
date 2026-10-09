# CRM Integrity Guardrails (AI-Assisted Salesforce Workflows)

## Metadata
- **Author:** **Kyle Ricketts**
- **Year:** 2026
- **Venue:** Internal AI skill, documented in portfolio write-up — Florence Healthcare (source: `knowledge_base/papers/35-ai-crm-integrity-guardrails.md`)
- **User's role:** Sole designer and builder; part of the GTM skill library (ricketts2026_ai_gtm_skill_library.md)
- **Status:** internal, live

## Methods & Tools
- **Operational frameworks:** CRM data governance, stage-gate enforcement, deal-type classification (new business, amendment, renewal)
- **Software/platforms:** Salesforce (via MCP connector), Claude Skills, Google Sheets (bulk-change audit sheets)
- **Key techniques:** Confirming the full toolset (query and search alongside create/update) before declaring a limitation; record IDs selected in every query to build direct links; field labels in conversation with API names kept inside queries; validation-rule fields asked first and unskippable

## Key Results
1. Embedded CRM integrity rules into every AI-assisted Salesforce interaction for GTM users
2. Required fields captured at creation: validation-rule fields asked first; accounts missing them are flagged and backfilled before an opportunity is created
3. Stage criteria checked before advancement (key fields, next-stage criteria, validation rule text); administrators are still asked and told the rule would not block them
4. Downstream fields (primary contact, product suite, record type, owners, stage, close date) walked as separate, skippable prompts with the requester as default owner
5. Deal-type recommendation on opportunities for existing accounts, based on prior agreements
6. Every named record carries a direct production link; bulk changes trigger a color-coded audit sheet of old and new values with record links
7. Not-found lookups offer both create and fuzzy-match search; escalation lookups return a fixed format

## Novelty Claims
- None claimed in source

## Collaboration & Scope
- **Other groups:** All GTM users of AI-assisted Salesforce
- **User's specific contribution:** Translated the org's CRM rules into skill logic
- **Shared vs. sole work:** Entirely sole-ownership

## Provenance Notes
- **Publication status:** N/A — internal skill
- **Safe to claim:** Full-ownership verbs (Embedded, Built, Designed)
- **Needs hedging:** None
- **Do NOT claim:** Validation-failure reduction or number of users covered (source placeholders unconfirmed)

## Resume Bullet Seeds
1. Embedded CRM integrity rules into AI-assisted Salesforce workflows (required-field and stage-gate checks, deal-type recommendations, direct record links, audit sheets for bulk changes), applied to every AI-assisted Salesforce interaction.
