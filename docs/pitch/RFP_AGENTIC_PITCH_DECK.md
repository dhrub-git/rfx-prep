# RFP Agentic Platform — Pitch Deck

## 1. Title

- RFP Agentic Platform for ICT Procurement (NSW + Federal)
- Automating compliant, high‑quality proposals with multi‑agent workflows
- Pricing: $10,000 per RFP + 2% success fee of contract value

## 2. Problem

- ICT RFP responses are labor‑intensive, error‑prone, and slow, risking non‑compliance and missed deadlines.
- Institutional knowledge is scattered across drives and emails; teams rewrite instead of reusing.
- Quality varies by SME availability; cross‑references, page limits, and formatting cause last‑minute churn.
- Traditional tools (DMS/Word) don’t enforce coverage, traceability, or measurable quality.

## 3. Opportunity (Why Now)

- Generative AI + retrieval unlocks high‑quality drafting with citations and controls.
- Governments tighten compliance and security while accelerating digital procurement.
- NSW and Australian Federal agencies standardize processes (Buy.NSW, AusTender), enabling repeatable automation.

## 4. Solution Overview

- An agentic RFP platform purpose‑built for ICT proposals, orchestrating:
  - RFP parsing + requirement mining → compliance matrix
  - Governed Knowledge Packs (versioned, curated, auditable)
  - Writer + Research + Graphics + QA/Compliance agents
  - Assembly to DOCX/PDF with page limits and cross‑refs validated
  - Human‑in‑the‑loop gates and full provenance
- Outcome: faster first draft, higher compliance coverage, consistent quality, lower SME hours.

## 5. How It Works (Architecture Summary)

- Orchestrator executes a deterministic DAG with HITL gates.
- Hybrid retrieval (BM25 + embeddings + re‑ranking) to ground content with citations.
- Knowledge Packs with approvals, classification, and retention policies.
- QA: coverage checks vs. mined requirements, style/brand lint, factuality sampling.
- Security: OIDC/RBAC, private model endpoints, DLP, audit logs, source hashes.

References: see `docs/RFP_AGENTIC_SOLUTION_ARCHITECTURE.md`, `docs/RFP_AGENTIC_PIPELINES_AND_WORKFLOWS.md`, `docs/RFP_KNOWLEDGE_MANAGEMENT.md`.

## 6. Differentiation

- Built for government ICT proposals: compliance matrices, strict formatting, and provenance by design.
- Knowledge governance (packs, approvals, classification) standard in the workflow.
- Cost controls with per‑run budgets and model allowlists.
- Transparent QA metrics (coverage %, defect density) and traceable citations.

## 7. Market Size (TAM/SAM/SOM Framework)

- TAM (AU Government ICT procurement as proxy):
  - Commonwealth total contracts (FY2017–18): ~AU$71.1B; ICT categories (UNSPSC 43, 81) ~AU$8.34B across ~15.5k contracts.
  - Source: Historical Australian Government Contract Notice Data (data.gov.au) — FY2017–18 CSV; UNSPSC filters 43 and 81.
  - Link: https://data.gov.au/data/dataset/5c7fa69b-b0e9-4553-b8df-2a022dd2e982/resource/bc2097b7-8116-4e9d-9953-98813635892a/download/17-18-fy-dataset.csv
- SAM (Australia focus; NSW + Commonwealth first):
  - Commonwealth ICT (anchor): ~AU$8.34B (FY2017–18, see above).
  - NSW: multi‑billion Digital Restart Fund supporting ICT initiatives (indicative of sustained ICT investment).
  - Link: https://www.digital.nsw.gov.au/funding/digital-restart-fund
- SOM (Year 1–3 beachhead):
  - Prime contractors/SIs active in NSW/Commonwealth ICT; focus categories: SaaS, digital, cloud, cyber, managed services.
  - Penetration example: 1% of ICT opportunities serviced within target accounts in Year 2–3.
- Notes: We can refine with current‑year AusTender exports and NSW procurement data (filtering UNSPSC 43/81) to update values.

## 8. Target Customers (ICP)

- Primary: Prime contractors and systems integrators bidding on ICT (e.g., digital services, infrastructure, security).
- Secondary: Mid‑size ICT vendors/consultancies pursuing panels and standing offers.
- Tertiary: Agency internal bid teams seeking automation (subject to procurement policy).
- Buyer personas: Proposal Director, Capture Manager, Delivery/Practice Leads, Compliance/Legal.

## 9. Initial Beachhead

- Geography: New South Wales and Australian Federal government RFPs.
- Categories: SaaS, digital transformation, cloud, cybersecurity, managed services.
- Channels: direct to primes/SIs; partnerships with capture/proposal firms.
- Compliance posture: alignment with NSW policies and Commonwealth requirements (records, privacy, auditability).

## 10. Business Model & Pricing

- Per‑opportunity fee: $10,000 for end‑to‑end RFP preparation (intake to assembly and sign‑off).
- Success fee: 2% of awarded contract value (collected post‑award; terms adjustable by ceiling).
- Optional add‑ons: graphics packages, resumes rewrites, custom templates, API integrations, enablement/training.
- Delivery model: hybrid product + managed service, metered model usage under the hood with budget caps.
- Billing: invoiced at kickoff (fixed fee) + post‑award success fee; both handled within the platform workflow.

## 11. GTM Plan (Year 1)

- Focus: 10–20 prime contractors/SIs active in NSW/Commonwealth ICT.
- Motions: reference pilots on 3–5 proposals; land via measurable cycle‑time and coverage gains.
- Offers: fixed‑fee pilot with success‑fee alignment; case studies and red‑team assistance.
- Partnerships: boutique proposal consultancies; design/desktop publishing partners.

## 12. Targets & KPIs (Year 1)

- Operational: first draft in < 24 hours on standard RFPs; coverage ≥ 95%; defect density ↓ 50%.
- Commercial: 100 RFPs prepared in Year 1; attach rate for success fee (%); customer retention (%).
- Financial: revenue per proposal, gross margin after model/infra costs, cost per opportunity trend.

## 13. Traction & Proof (Planned)

- Pilot outcomes: cycle time reduction, SME hours saved, QA coverage improvement with citations.
- Case studies: NSW category example; Commonwealth example with strict formatting/page limits.

## 14. Product Roadmap (Phased)

- Phase 1: Intake → Parse → Requirements → Compliance Matrix (HITL)
- Phase 2: Knowledge Packs + Hybrid Retrieval + Section Outlines
- Phase 3: Draft Generation + QA Gates + Assembly Pipeline
- Phase 4: Graphics + Pricing Hooks + CRM/DMS Integrations
- Phase 5: Evals at PR gates + Cost Controls + Multi‑tenant packaging

## 15. Risks & Mitigations

- Data leakage via models/vendors → private endpoints, zero‑retention, allowlists.
- Hallucination/factual drift → strict RAG with citation enforcement; QA gates.
- Adoption resistance → champions, training, measurable wins; managed service overlay.
- Cost overruns → per‑run budgets, caching, sampling controls.
- Procurement sensitivities → auditable provenance, records management, legal reviews.

## 16. Competitive Landscape

- Traditional proposal & DTP services: manual, slower, less traceable.
- Generic AI writing tools: lack compliance coverage and provenance.
- Our edge: agentic orchestration + compliance‑first knowledge governance.

## 17. Financial Model (Illustrative)

- Inputs:
  - Proposals serviced per month (p)
  - Average contract value (ACV)
  - Win rate (w)
  - Fixed fee: $10,000 per proposal
  - Success fee: 2% × (ACV) × (wins)
  - Direct costs: model/infra per proposal (c)
- Formulas:
  - Fixed‑fee revenue = p × $10,000
  - Success‑fee revenue = p × w × (ACV × 0.02)
  - Gross revenue = Fixed + Success
  - Gross margin = (Gross revenue − p × c) / Gross revenue
- Note: replace with real assumptions from pipeline and target accounts.

## 18. Team & Roles

- Solution Architect, Orchestration Engineer, Data/ML Engineer, Prompt/Tooling Engineer, Security/Compliance Lead, Proposal SMEs.
- Governance and cadence per `docs/RFP_AGENTIC_BUSINESS_AND_OPERATING_PLAN.md`.

## 19. Ask

- Pilot customers in NSW/Commonwealth ICT (3–5 logos).
- Partnerships with proposal/DTP firms.
- Budget for year‑1 delivery and case studies.

## 20. Close

- Mission: increase win rate, cut cycle time, and institutionalize knowledge for ICT RFPs.
- Differentiator: compliance‑first agentic platform with governed knowledge and provable citations.
