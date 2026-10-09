# Sponsor Trial Portfolio Research

> Built a sponsor research workflow that profiles any company's active trial portfolio, pipeline news, and site footprint from ClinicalTrials.gov.

Part of the [GTM skill library](../05-gtm-skill-library.md).

## What it answers

Given a company name (and optionally its website), the workflow answers: what trials is this sponsor running, in which therapeutic areas and phases, across how many sites and countries, and what has changed in its pipeline in the last 90 days. For a company selling trial operations software, site footprint is the closest public proxy for account size and workload.

## The six-step workflow

**1. Resolve the sponsor name.** ClinicalTrials.gov searches are name-sensitive, and the registered lead sponsor often differs from the brand (legal suffixes, subsidiaries, former names). The workflow finds a trial page listing the organization as lead sponsor and extracts the exact registered string, using the form on the most recent trial when variants exist. If no match is found, it stops and says so.

**2. Recent pipeline news.** Three to five operationally relevant items from the last 90 days: phase transitions, IND and NDA filings, approvals and complete response letters, trial starts and expansions, regulatory actions, CRO partnerships, and clinical leadership changes. Each item must carry a verified on-page date, duplicates keep only the most authoritative source, and every URL must be publicly accessible.

**3. Ongoing trials.** All recruiting, not-yet-recruiting, active, and enrolling-by-invitation trials for the sponsor, paginated up to 100.

**4. Site locations.** Location records for each ongoing trial, prioritizing the 25 largest by enrollment when a sponsor has more.

**5. Recently completed or terminated trials.** Trials whose primary completion fell in the last 90 days.

**6. Synthesis.** A structured JSON object with two outputs: a full registry report and a six-section portfolio summary.

## Data rules

**The location asymmetry.** Location data exists only for ongoing trials. Completed trials never receive a site count and never enter a site total, share, or density figure. They appear as recent context only.

**Strict sponsor filter.** A trial is kept only if its normalized lead sponsor name contains the normalized searched name. Rejections are counted and reported, so the reader knows how much was filtered.

**Per-study fields.** Phase, study type, design (including adaptive, platform, basket, and umbrella designs detected from the title or model), arm count, enrollment, key dates, conditions, interventions, collaborators, and, for ongoing trials, site count, sites per enrollee, country spread, and sites not yet recruiting.

**Portfolio metrics.** Total site locations, recruiting-site total, each study's share of the portfolio's sites, and a site-density rank among recruiting studies.

**No outside knowledge in the summary.** The six sections (snapshot, therapeutic areas, modality, study type and phase, scale and geography, representative studies) draw only on the retrieved data, and their counts must match the report header exactly.

**Size guard.** The full report is capped in length. When it runs over, the smallest ongoing studies drop first, then the oldest completed ones, and the report is marked as truncated.

## Where it fits

The trial footprint this workflow produces is the raw material for the [outbound copy system](../04-outbound-copy-system.md), whose strongest angles reference a prospect's programs, phases, countries, and site counts. The [account intent framework](../02-account-intent-framework.md) routes any account whose portfolio matters to this workflow.

## Impact

| Measure | Result |
|---|---|
| Research time per sponsor | [X hours] reduced to [Y minutes] |
| Usage | [N] sponsors profiled |

## Interview angle

"Site footprint is the best public measure of how much trial operations work a sponsor carries, and it was buried in registry records. I built a workflow that resolves the sponsor's exact registered name, pulls every active trial and its sites, and produces a portfolio profile a rep can scan before a call. A key rule keeps completed trials out of every site total, since locations are pulled only for active studies and mixing the two would overstate the footprint."
