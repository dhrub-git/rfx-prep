# RFP Agentic Workflow: Business & Operating Plan

## Purpose
- Provide a pragmatic, trackable business plan and operating model to deliver, adopt, and scale the agentic RFP workflow.
- Define governance, KPIs, milestones, budgets, risk controls, and ongoing runbooks.

## Business Objectives
- Improve win rate by 5–10 points within 12 months.
- Reduce time-to-first-draft to < 24 hours for standard RFPs.
- Cut SME review time by 30–50% through better coverage and QA.
- Institutionalize reusable knowledge; reduce one-off effort by 40%.

## Success Metrics (KPIs)
- Win-rate delta vs. baseline.
- Cycle time: intake → first draft → final.
- Requirement coverage % and compliance defects per submission.
- SME hours per opportunity and rework rate.
- Cost per opportunity and LLM spend variance.

## Governance & RACI
- Steering Committee (Exec Sponsor, Proposal Lead, IT, Security): strategy, budget, risk acceptance.
- Working Group (PO, Architect, Ops, SMEs): backlog, releases, adoption.
- RACI (examples):
  - Architecture decisions: A/R = Solution Architect; C = Security, Ops; I = Steering.
  - Model policy updates: A = Security; R = ML Eng; C = Legal; I = Steering.
  - Knowledge pack approvals: A = Proposal Lead; R = SMEs; C = Legal; I = Sales.

## Operating Model
- Intake: triage new opportunities, classify scope, assign workspace and roles.
- Plan: confirm win themes, sources, required SMEs, deadlines, and budget caps.
- Build: run orchestrations; SMEs address gaps via assigned tasks.
- Review: red team, compliance checks, brand/style, pricing alignment.
- Release: assemble final package, approvals, archive artifacts and provenance.
- Learn: retro meeting, update playbooks, promote new sources to knowledge packs.

## Cadence
- Weekly WG: delivery status, risks, KPIs, release readiness.
- Bi-weekly Steering: budget, escalations, policy changes.
- Monthly Enablement: training, office hours, refresh playbooks.

## Roadmap & Milestones (Tracked)
- M1: Foundations live (RBAC, observability, dev/stage/prod) — Target: Q1-W3
- M2: Parse + Requirement Matrix + HITL — Target: Q1-W6
- M3: Knowledge Packs + Hybrid Retrieval — Target: Q1-W9
- M4: Drafting + QA + Assembly — Target: Q1-W12
- M5: Graphics + Pricing Hooks + CRM/DMS — Target: Q2-W4
- M6: Evals at PR Gates + Cost Controls — Target: Q2-W8

## Budget & Cost Model
- One-time: orchestration platform, observability, vector/search infra, security hardening, integration work.
- Ongoing: LLM/API usage, storage, compute, observability, support, enablement.
- Controls: per-run spend caps, model allowlists by data class, caching policies, off-peak batch windows.
- Reporting: monthly cost reports; per-opportunity spend included in retros.

## Vendor & Model Strategy
- Primary LLMs: shortlist of approved models by sensitivity tier; private endpoints preferred.
- Evaluation: sandbox test sets, bias/safety checks, cost-latency-quality tradeoff; canary before promotion.
- Contracts: data retention and training restrictions; SLAs and escalation channels.

## Compliance & Legal
- Data classification with handling rules (Public, Internal, Sensitive, Restricted).
- Records management: retention by class; legal holds applied via DMS/ECM.
- Provenance & audit logs retained for proposals and model calls.
- External submissions reviewed by Legal for terms/deviations.

## Change Management & Training
- Champions network within proposal teams.
- Training modules: intake, knowledge packs, drafting review, QA dashboard, assembly.
- Playbooks: win themes, compliance mapping, red-team checklists, model usage do’s/don’ts.
- Feedback channels: office hours, issue templates, request board.

## Risk Register (Initial)
- Data leakage via model/vendor — Mitigation: private endpoints, zero-retention, allowlist.
- Hallucinations and factual drift — Mitigation: strict RAG, citation enforcement, QA gates.
- Low adoption — Mitigation: champions, co-creation, measurable wins, quick assists.
- Cost overruns — Mitigation: budgets, alerts, caching, sampling controls, model selection.
- Timeline slippage — Mitigation: phased scope, critical path tracking, buffer.

## KPI Dashboard (Definitions)
- Coverage: required items covered / total; weighted by scoring rubric.
- Quality: human rubric score per section; defect density (style/compliance/factuality).
- Velocity: lead time per stage; p95 drafting iteration time.
- Cost: model spend per opportunity; unit cost per 1k tokens by model.
- Reliability: orchestration success %, retries per run, MTTR.

## Tracking Templates (Use in Repo/Tools)
- Intake Checklist: opportunity summary, sources, constraints, win themes, deadlines.
- Compliance Matrix: requirement ID, owner, coverage, confidence, evidence, status.
- Decision Log: architecture, model, policy choices; rationale; date; approvers.
- Assumption Log: key assumptions; dependency; validation status.
- Risk Log: risk, owner, impact, mitigation, status.
- Retro Notes: wins, gaps, actions, owners, due dates.

## Roles & Access (RBAC)
- Proposal Lead: full project control; approve packs; final sign-off.
- SMEs: read/write in assigned sections; propose sources.
- Reviewer/QA: comment, approve/reject tasks; run QA tools.
- Architect/Engineer: configure DAGs, models, tools; prod access gated.
- Security/Legal: read all, approve policies; audit access.

## Adoption Plan
- Pilot (3–5 proposals): measure cycle time, coverage, quality; iterate.
- Wave 1 (one business unit): expand knowledge packs; training; add integrations.
- Wave 2 (cross-org): standardize templates, dashboards; formalize SLAs; cost governance.

## SLAs & Runbooks
- Orchestration: 99.5% uptime; queued tasks < 5 minutes start time.
- Support: P1 within 2 hours, P2 same business day, P3 within 2 days.
- Incident Response: on-call rotation; playbooks for model outage, vendor latency, indexing failure.
- Backup & DR: daily snapshots; cross-region for critical metadata.

## Dependencies
- Identity (OIDC), DMS/ECM, CRM, HR/Skills DB, Pricing/Finance APIs, Observability stack, Secrets manager.

## Open Questions
- External portal submission automation scope and risk posture.
- Long-term knowledge graph vs. pragmatic metadata-only approach.
- Model finetuning policy vs. prompt-engineering + retrieval.

## Appendix: Example Backlog (Initial)
- Data contracts for sources; chunking policies; PII filter.
- Requirement miner models and eval set.
- Hybrid retriever with re-ranker; citation resolver.
- Writer agent tools: template fetch, citation insert, section linter.
- QA coverage engine and style/brand lints.
- Assembly pipeline for DOCX/PDF; cross-ref checks.
- Cost telemetry and budgets; approval gates.
- Dashboards: KPIs, cost, reliability.

