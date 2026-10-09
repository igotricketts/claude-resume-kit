# Account Intent Framework

> Developed an account intent framework of 8 public buying-signal criteria (FDA enforcement, clinical tech hiring, leadership changes, funding, cost programs, CRO relationships, trial readouts) with suppression rules and confidence scoring. It drove territory prioritization for strategic sellers and [sourced/influenced] $1M+ in [pipeline/new ARR] within 3 months.

## The problem

Clinical trial software purchases follow events: an FDA inspection finding, a new head of clinical operations, a funding round that pays for the next phase, a migration off a legacy system. Those events are public, but they are scattered across regulatory databases, careers pages, press releases, SEC filings, and trial registries. Sellers either skipped the research or spent hours on it per account, and the results varied by rep. Third-party intent data covered web browsing behavior and missed these operational triggers entirely.

The framework answers one question for any account: is there a reason to reach out right now, and what is the single strongest hook?

## What it does

The framework runs as three connected Claude skills.

| Skill | Role |
|---|---|
| Account intent | Researches one account (scan or deep dive) or ranks a list of accounts (triage) against the regulatory, hiring, leadership, funding, and cost criteria |
| CRO partnership signal | Covers the two CRO relationship criteria, in account-check and discovery-sweep modes |
| Intent workup | Orchestrator. Runs all 8 criteria plus a suppression sweep against one account and writes a four-sheet Excel briefing |

### The 8 criteria

| ID | Signal | What counts |
|---|---|---|
| PIPE-09 | Imminent early-phase readout | A Phase 1 or 2 study reaching primary completion between 30 days ago and 60 days ahead. The only criterion that fires before a purchase decision is made. Sponsors only. |
| REG-01 | FDA regulatory action on clinical operations | Warning letters citing GCP or sponsor oversight, OAI inspection classifications on bioresearch monitoring, published Form 483s with clinical observations, disclosed clinical holds, consent decrees. 180-day lookback. |
| TECH-02 | Clinical technology transformation hiring | Postings that own a migration, implementation, or vendor selection for eTMF, eISF, CTMS, or eRegulatory; a net-new clinical systems function; named TMF remediation; or three or more concurrent clinical operations postings. 60-day lookback. |
| FIN-03 | New clinical operations leadership | An external hire into a clinical operations, quality, site enablement, clinical systems, or medical leadership role, reported with months in seat. 90-day lookback. |
| FIN-04 | Funding, IPO, or R&D increase | Capital that expands clinical development. |
| FIN-06 | Cost or efficiency initiative | A named efficiency program, read through a three-state direction model. |
| CRO-05 | New CRO partnership | A sponsor engaging a CRO, or a CRO winning a named sponsor. |
| CRO-07 | Insourcing or outsourcing shift | Trial operations ownership moving in-house or out to a partner. |

Each criterion maps to at least one of three value drivers: accelerating clinical trials, mitigating risk and inspection readiness, or improving productivity and capacity.

### Suppression

Some findings disqualify an account regardless of positive signals: activist-driven headcount mandates, programs transferred out, and operating expense caps. Suppression is a separate sweep that runs on every workup. An active suppression signal caps the overall recommendation, even when strong positives exist.

When a program transfers out, the receiving organization has just gained trial operations workload. The workup records that counterparty as a related account, and it is often the better lead.

## How it's built

**One file per criterion.** Each criterion lives in its own reference file containing the hit definition, the exclusion list, the search order, and the known coverage limits. The orchestrator reads those files directly and never restates a criterion, so two versions of the same rule can never disagree.

**Exclusions carry the precision.** Most search results for these criteria are near misses. A manufacturing finding looks like a clinical one. A system named in a job's requirements looks like a migration. An internal promotion looks like a new hire. A bridge round looks like expansion capital. Each exclusion exists because the excluded thing is common and resembles a hit.

**Deterministic where possible.** PIPE-09 pulls registrations from ClinicalTrials.gov and passes them to a Python script for the date arithmetic, which buckets studies as just completed, imminent (30 days), or near (60 days). Date math done by a language model across a dozen studies looks right and is quietly wrong, so the model never does it.

**Evidence standard.** Every factual claim needs a source URL, the date the event occurred (trade press revisits old actions constantly, so publication dates mislead), and a verbatim quote under 25 words. A claim that cannot carry all three is dropped. An unsourced signal is treated as worse than no signal, because a rep will act on it and burn a real relationship.

**Five result states.** FOUND, NOT FOUND, UNKNOWN (a required source was unreachable), NOT APPLICABLE (the question does not fit this account type, such as trial readouts for a CRO), and NOT ENOUGH DATA. A rep reading "no transformation hiring" stops researching. A rep reading "could not read their careers page" keeps going. The distinction changes behavior.

**Split confidence.** Each result carries two scores: retrieval confidence (how completely the sources were reached) and conclusion confidence (how sure the finding is). They are reported separately and never averaged, because their divergence is informative.

**Negative results weighted by source.** An empty FDA search is trustworthy, since warning letters are well indexed. An empty job search is close to meaningless, since job boards block automated access. An empty leadership search is weak for private companies, which often hire without announcements. Each criterion documents how much its negatives mean.

**Workbook output.** The orchestrator assembles results into JSON and a Python script (openpyxl) writes a four-sheet workbook: Summary, Signals, Related Accounts, and Suppression. One account, one run, one file, named for the account and date.

**Handoffs.** A leadership hire returns a buyer persona tag that carries into the [outbound copy system](04-outbound-copy-system.md). Accounts whose trial portfolio matters route to [sponsor trial portfolio research](supporting/sponsor-trial-portfolio.md). Structured output carries a source flag so ad hoc results stay distinguishable from scheduled extraction, which protects scoring calibration downstream.

## Impact

| Measure | Result |
|---|---|
| Pipeline | $1M+ in [pipeline/new ARR] [sourced/influenced] within 3 months, from accounts run through the framework |
| Territory planning | Account prioritization for strategic sellers |
| Coverage | [N] accounts researched |
| Research time | [X hours] per account reduced to [Y minutes] |

## Design decisions and lessons

**Classify by extraction method first.** Before writing any prompt, each candidate criterion was sorted into a deterministic API pull, a prompt-engineered search, or no viable source. That triage decided the build order.

**Shelve what cannot be sourced.** Published RFPs and public statements on ICH E6(R3) readiness were permanently shelved. Both looked valuable on paper, and neither had a reliable public data source.

**Invert when direct lookup fails.** Checking whether one sponsor had signed a CRO produced little, because most selections are never announced. Sweeping CRO newsrooms for named sponsor wins worked far better, so CRO-05 runs in that direction.

**Route around rendering limits.** Workday careers pages render client-side and cannot be fetched from a chat session. Those pages route to Clay. Aggregator fallbacks proved stale (one was years out of date), so an industry job board is used to confirm role details.

**Name the top false positive.** Internal promotions were the most frequent false positive on leadership hires, so the internal-versus-external test stays strict.

**Flag unvalidated assumptions.** The 2-to-6 month window in which a new leader re-evaluates vendors is labeled as a working heuristic in the skill itself, pending validation against closed-won data.

**Fit the tool to actual use.** The orchestrator began as a multi-run log with diffing across runs. Actual usage was one account at a time, so it became a single-account briefing and two sheets and a diffing criterion were removed.

**Find the earlier tell.** In one validation workup, a Phase 2 study's primary completion date was public months before the R&D guidance that announced Phase 3 funding, and site selection was already final by the time the guidance came out. That finding moved PIPE-09 to the front of every sponsor workup.

## Interview angle

**Question it answers:** "How do you help sellers prioritize when every account looks the same in the CRM?"

Our buying triggers were public but scattered across a dozen sources. I defined eight criteria, validated each against live accounts before building it, and shelved the ones with no reliable source. The framework separates "nothing happened" from "we could not check," and it can veto an account with a suppression signal even when other signals look strong. Strategic sellers used it to prioritize territories, and accounts run through it [sourced/influenced] $1M+ in [pipeline/new ARR] within three months.

## Skills demonstrated

Signal-based prospecting design, territory prioritization, regulatory and clinical operations domain knowledge, research methodology and evidence standards, AI orchestration, Python automation.
