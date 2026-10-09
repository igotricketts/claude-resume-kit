# GTM Skill Library

> Created and deployed a library of 10 Claude skills for SADR, AE, and leadership teams, covering account intent research, ClinicalTrials.gov portfolio analysis, outbound copy, CRM data entry guardrails, branded executive communications, and weekly executive readouts. Adopted by [N] reps.

## The problem

Reps were using AI tools individually, each with their own prompts, and output quality varied with the person writing the prompt. The same research was done differently by different reps. Copy cited different numbers for the same proof point. CRM records created with AI help skipped required fields and failed validation after the fact. The goal was consistent AI usage across SADR and AE teams, part of a [Q3 2026] objective, with team knowledge encoded once and applied the same way every time.

## The library

| Skill | What it does | Primary users | Detail |
|---|---|---|---|
| Account intent | Researches one account or triages a list for public buying signals | SADRs, AEs | [02](02-account-intent-framework.md) |
| CRO partnership signal | Detects new CRO relationships and insourcing or outsourcing shifts | SADRs, AEs | [02](02-account-intent-framework.md) |
| Intent workup | Runs all 8 intent criteria on one account and writes an Excel briefing | AEs | [02](02-account-intent-framework.md) |
| Sponsor trial portfolio | Profiles a sponsor's trial portfolio and site footprint from ClinicalTrials.gov | SADRs, AEs | [supporting](supporting/sponsor-trial-portfolio.md) |
| 3-option outbound | Writes three distinct cold emails or LinkedIn invites per prospect | SADRs | [04](04-outbound-copy-system.md) |
| Salesforce record links | Enforces CRM integrity rules and record links in every Salesforce interaction | All GTM users | [supporting](supporting/crm-integrity-guardrails.md) |
| Client-facing communications | Produces branded executive documents, decks, and emails using strategic copywriting frameworks | AEs, account leaders | [supporting](supporting/executive-communications.md) |
| Forecast movement readout | Weekly executive forecast readout | Leadership | [supporting](supporting/forecast-movement-readout.md) |
| MQL disposition readout | Weekly MQL cohort readout | Demand Gen and SADR leadership | [03](03-mql-disposition-readout.md) |
| Rep call readout | Weekly Gong readout of 1:1 prospecting calls | Sales managers | [supporting](supporting/rep-call-readout.md) |

## How the skills work together

The prospecting skills form a chain. Intent research identifies which accounts have a reason to buy now. Portfolio research sizes the account's trial operations. The outbound system writes the first touch, grounded in both. Each skill knows its boundaries and hands off explicitly: the intent skill declines to write outreach and offers the outbound skill instead, and it passes along the buyer persona tag it found so the next skill does not repeat the work.

The utility skills apply everywhere. The Salesforce skill governs any CRM interaction, and the communications skill governs any client-facing document.

## How they're built

**Packaging standard.** Every skill follows the same build process: a directory with a `SKILL.md` and supporting reference files, validated with a packaging validator, with the trigger description kept under the 1,024-character limit so the skill activates on the right requests, then packaged for distribution.

**Trigger descriptions written for recall.** Each description lists the phrasings a rep would actually use ("is there a reason to reach out," "give me 3 options," "what trials are they running") and names the neighboring skill to use instead for adjacent requests. This keeps the right skill firing without the rep having to remember skill names.

**Reference files hold the substance.** Criteria, exclusion lists, copywriting rules, verified facts, and frameworks live in reference files. Workflow lives in the `SKILL.md`. Updating a rule means editing one file.

**Scripts for anything deterministic.** Date arithmetic, workbook construction, and data synthesis run in Python, because those are the steps where a language model is most likely to be confidently wrong.

**House style built in.** American spelling, no em dashes, no antithesis phrasing, and Florence's number formatting apply across skills, so output looks the same regardless of who ran it.

## Impact

| Measure | Result |
|---|---|
| Adoption | [N] reps across SADR and AE teams |
| Consistency | One research standard, one claims library, and one voice across all reps |
| Downstream results | See [intent framework](02-account-intent-framework.md) pipeline and [outbound](04-outbound-copy-system.md) reply rates |

## Interview angle

**Question it answers:** "How do you scale AI adoption across a sales team without losing quality control?"

Reps were each prompting AI their own way, so output quality depended on who asked. I turned our best research methods, messaging rules, and CRM requirements into a library of ten skills that trigger on the way reps naturally ask for help. The skills hand off to each other, enforce the same evidence and claims standards, and run deterministic steps in code. [N] reps adopted them, and the work feeds directly into measurable pipeline and reply-rate gains.

## Skills demonstrated

Sales enablement, AI adoption and change management, knowledge management, process design, GTM tooling.
