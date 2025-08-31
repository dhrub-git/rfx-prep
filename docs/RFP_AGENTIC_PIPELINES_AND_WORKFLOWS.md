# RFP Agentic Pipelines & Workflows (High-Level, Technical)

## Purpose

- Define orchestrated pipelines (DAGs), agent roles, inputs/outputs, artifacts, and human-in-the-loop (HITL) gates for the RFP program.
- Serve as the runbook for workflow configuration in the chosen orchestrator (e.g., Temporal, Camunda, Prefect, LangGraph).

## Master Workflow (DAG)

```
Intake → Parse → Requirement Mining → Compliance Matrix → Knowledge Pack → Research → Drafting Loop → QA/Compliance → Assembly → Red Team → Final Sign-off → Export/Archive
```

## Stage Specifications

### 1) Intake

- Triggers: manual upload, mailbox ingestion, SFTP drop, or portal fetch.
- Inputs: RFP package (PDF/DOCX/XLSX/PPTX/ZIP), opportunity metadata.
- Outputs: opportunity workspace, originals in object store, immutable manifest.
- Agents/Tools: Intake service, checksum hasher, DLP pre-scan.
- HITL: confirm scope, eligibility, deadlines, win themes; go/no-go.
- Metrics: time to triage, completeness, DLP flags.

### 2) Parse

- Inputs: originals from Intake.
- Outputs: structured document model (sections, headings, tables, figures), normalized text.
- Agents/Tools: OCR, layout parser (e.g., Unstructured/Detectron), table extractor.
- HITL: optional spot-check on low-confidence OCR/layout.
- Metrics: parse latency, extraction coverage, OCR confidence.

### 3) Requirement Mining

- Inputs: structured document model.
- Outputs: requirement inventory with IDs, priority (must/shall/should), scoring, due dates, submission instructions.
- Agents/Tools: NER + pattern miner; rules for must/shall; scorer mapping.
- HITL: review auto-mined requirements; resolve ambiguities.
- Metrics: precision/recall vs. sample labels; reviewer changes.

### 4) Compliance Matrix

- Inputs: requirement inventory.
- Outputs: compliance matrix with owner, coverage status, evidence links, confidence.
- Agents/Tools: compliance engine; matrix initializer.
- HITL: assign owners; accept baseline matrix.
- Metrics: % assigned, initial coverage gap.

### 5) Knowledge Pack (Curation)

- Inputs: prior proposals, case studies, resumes, solution docs, certifications, product collateral.
- Outputs: versioned knowledge pack; search index; vector index; provenance map.
- Agents/Tools: ETL chunkers, PII filter, dedupe, embeddings, indexers.
- HITL: approve pack scope; flag restricted content.
- Metrics: ingestion success, dedupe %, PII redactions, coverage to requirements.

### 6) Research

- Inputs: knowledge pack; web/DB connectors as permitted.
- Outputs: curated intel notes with citations and risk/competitor insights.
- Agents/Tools: research agent, browsing connectors, citation resolver.
- HITL: approve external sources per policy; redact as needed.
- Metrics: source credibility scores, freshness, utilization in drafts.

### 7) Drafting Loop (Iterative)

- Inputs: outlines, compliance matrix, retrieved snippets, research notes.
- Outputs: section drafts with inline citations and graphics stubs.
- Agents/Tools: writer agent (RAG, tool-use), template fetcher, section linter, graphics suggester.
- HITL: SME review tasks per section; accept/return changes.
- Metrics: iterations to acceptance, p95 draft latency, citation density.

### 8) QA/Compliance

- Inputs: accepted drafts, compliance matrix, style/brand rules.
- Outputs: QA report; auto-fixes where safe; updated coverage.
- Agents/Tools: coverage engine, style/brand lints, cross-ref checker, factuality sampler.
- HITL: sign-off on non-trivial fixes; resolve blockers.
- Metrics: coverage %, defect types, residual risks.

### 9) Assembly

- Inputs: accepted sections, figures, tables, front/back matter.
- Outputs: assembled DOCX/PDF with ToC, numbering, cross-refs, page-limit validation.
- Agents/Tools: docxtpl/LaTeX pipeline; figure/appendix manager.
- HITL: visual review on formatting edge cases.
- Metrics: broken cross-refs, page-limit violations.

### 10) Red Team Review

- Inputs: assembled draft and QA report.
- Outputs: red team findings and prioritized fix list.
- Agents/Tools: critique agent with evaluator rubrics; diff highlighters.
- HITL: red team session and adjudication.
- Metrics: issues by severity; fixes accepted rate.

### 11) Final Sign-off & Export

- Inputs: addressed red team actions; legal/pricing approvals.
- Outputs: final deliverables; provenance bundle; audit logs; archive record.
- Agents/Tools: export service; records manager.
- HITL: approvals (Proposal Lead, Legal, Exec as required).
- Metrics: cycle time; residual defect rate; submission readiness.

## Failure Modes & Recovery

- Idempotent tasks; retries with backoff; compensating steps for partials.
- Quotas and budgets enforced per run; early-stop on cost ceilings.
- Circuit breakers for external connectors; fallback to cached retrieval.
- Resume-from-checkpoint on orchestrator restarts.

## Policy Gates (HITL)

- Go/No-go after Intake.
- Requirement inventory approval.
- Knowledge pack approval.
- Section-level SME approvals.
- QA exception approvals.
- Final sign-off (Legal/Pricing/Lead).

## Observability & SLIs

- Traces across stages (OpenTelemetry), per-stage latency and error rate.
- Coverage %, citation match rate, style defects per 10k words.
- Cost telemetry by stage; budget compliance.

## Mapping to Orchestrator

- Represent each stage as an activity with typed inputs/outputs.
- Use signals for HITL gates; timers for SLAs; retries for transient errors.
- Capture artifacts to object store keyed by run/opportunity.
