## Florence Clay Governance Roadmap

- **Role/context:** Co-led (with GTM Systems/IT) the governance framework for Clay as it scaled from pilot to production, addressing the risk surface of an AI system with CRM write-back access.
- **Timeframe:** Q3–Q1 (multi-quarter roadmap, exploration/planning phase as of this document)
- **What I did:**
  - Defined a three-tier field-level write governance policy (NEVER-WRITE / WRITE-IF-EMPTY / ALWAYS-WRITE) to prevent AI enrichment from silently overwriting verified CRM data
  - Designed a role-based access control framework for the Clay workspace (Admin/Editor/Viewer) tied to job function and data sensitivity, including a 24-hour offboarding SLA
  - Established ongoing data-quality monitoring: email/phone fill-rate targets, AI field accuracy sampling (50-100 records/month human-reviewed), and a conflict-rate metric for Clay-vs-CRM disagreements
  - Scoped a formal privacy/compliance review (GDPR/CCPA/CPRA) covering vendor DPAs across Clay's 150+ data providers, lawful basis documentation, data retention policy, and data-subject deletion-request handling across Clay/SFDC/HubSpot
  - Built a provider evaluation and lifecycle framework (match rate by ICP segment, cost-per-valid-match, compliance posture, retirement criteria) and a credit budget governance model (allocation by use case, 70%/90% alert thresholds, approval gates for high-cost workflows)
  - Set AI-specific governance standards: hallucination risk management, mandatory human review before AI-generated content overwrites verified data or is sent externally, and quarterly prompt/context quality reviews
  - Established data lineage/audit trail requirements (what was written, when, by which workflow, from which source) and a vendor risk/security assessment process for every new system connection
- **Outcome/metrics:**
  - Prioritized roadmap of 12 governance initiatives (4 P1-High, 6 P2-Medium, 3 P3-Low) with named business/technical owners, target quarters, and impacted teams/systems for each
- **Skills/tools demonstrated:** Data governance framework design, privacy/compliance program scoping (GDPR/CCPA/CPRA), vendor risk management, AI governance (hallucination risk, bias, human-in-the-loop controls), cross-functional program management (GTM Systems, IT, Legal, Sales, Marketing), audit trail/data lineage design
- **Resume-ready bullet(s):**
  - Built a comprehensive AI/data governance framework for a production enrichment platform with CRM write-back access, covering field-level write permissions, access control, privacy compliance (GDPR/CCPA/CPRA), and AI hallucination risk management
  - Established data quality and vendor risk processes (monthly accuracy sampling, provider lifecycle management, credit budget governance) that scaled a single-team pilot into an auditable, compliant, cross-functional GTM system
