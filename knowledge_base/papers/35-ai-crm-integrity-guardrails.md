# CRM Integrity Guardrails

> Embedded CRM integrity rules into AI-assisted Salesforce workflows: required-field and stage-gate checks, deal-type recommendations, and direct record links.

Part of the [GTM skill library](../05-gtm-skill-library.md).

## The problem

Once GTM users started querying and updating Salesforce through Claude, a new class of data quality problems appeared. Records were created with required fields blank, and the validation failure arrived later as an error email. Stages advanced without their entry criteria. Answers named records with no way to click through to them. Field names came back as API names that only administrators recognize. And in at least one case the assistant reported that it could only create and update records, because the query tools had not loaded yet, when a working query tool was available the whole time.

## What the skill enforces

**Check the full toolset first.** Before telling a user Salesforce cannot do something, the skill confirms whether query and search tools exist alongside the create and update tools, and loads any that are deferred. Manual workarounds such as asking for a CSV export are a last resort.

**Link every record.** Every record named in a response carries a direct link to the production org, including every row in a list, every fuzzy-match candidate, and every item in a grouped summary. Queries always select the record ID so the link can be built. The production base URL is a fixed constant; the skill never asks the user for it. Sandbox links apply only when a system administrator explicitly asks for one.

**Speak in field labels.** Users are assumed to be non-administrators, so fields are described by their labels in conversation. API names stay inside the queries.

**Walk downstream fields before saving.** When creating or updating opportunities, contacts, or accounts, the skill identifies the requesting user as the default owner and walks through fields with downstream impact (primary contact, product suite, record type, owners, stage, close date) as separate, skippable prompts.

**Respect stage gates.** Before advancing a stage, the skill checks the stage's key fields, next-stage criteria, and validation rule text, and asks only for what is actually required. Administrators, who bypass these rules, are still asked and told the rule would not block them.

**Recommend the deal type.** When an opportunity is created on an existing account, the skill checks for a prior agreement and recommends new business, amendment, or renewal.

**Required fields up front.** A field enforced by a validation rule is asked first when creating an account, and cannot be skipped. When creating an opportunity on an account that lacks it, the skill flags the gap and backfills the account first.

**Record not found.** When a lookup returns nothing, the skill offers both paths at once: create the record, or search for fuzzy matches under a different spelling or abbreviation.

**Bulk changes get an audit sheet.** Any request that updates, reassigns, or creates many records triggers an offer of a Google Sheet listing each record, the old and new values, and a link back to the record, with changed cells color-coded and a legend for each change type.

**Escalation lookups in a fixed format.** Questions about open account escalations return a one-line answer, then each escalation's key fields (status, type, date reported, ARR at risk), then a single line on closed escalations for context.

## Impact

| Measure | Result |
|---|---|
| Validation failures on AI-assisted record creation | [baseline] to [current] |
| Users covered | [N] GTM users |
| Data quality | Required fields captured at creation, stage criteria checked before advancement, bulk changes auditable |

## Interview angle

"CRM integrity is part of my role, and AI-assisted data entry was creating a new way to break it. I wrote the org's rules into a skill that applies to every Salesforce interaction: required fields asked first, stage criteria checked before advancement, every record linked, and bulk changes logged to an audit sheet. The rules now apply on every interaction, regardless of who is asking."
