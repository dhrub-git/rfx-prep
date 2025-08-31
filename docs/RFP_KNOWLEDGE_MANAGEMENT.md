# RFP Knowledge Management (Architecture & Governance)

## Purpose
- Define how we ingest, govern, retrieve, and evolve institutional knowledge for RFPs using versioned Knowledge Packs.

## Sources
- Internal: prior proposals, case studies, resumes, solution/architecture docs, certifications, product sheets, SLAs.
- External (approved): standards, regulatory docs, public references; optional analyst/vendor content per policy.

## Ingestion & Processing
- Contracts: source owner, refresh cadence, classification, retention, allowed models.
- Chunking: hybrid semantic/layout; tables treated as row/region chunks with headers; 300–1200 tokens.
- Metadata: source_id, uri, hash, title, authors, date, doc_type, section_path, toc_heading, labels, version, security_class, embargo_until.
- Sanitization: PII/secret detection and redaction with audit trail.
- Dedupe: near-duplicate hashing; keep canonical; merge metadata.

## Storage
- Object Store: originals and normalized artifacts.
- Relational DB: corpus registry, contracts, pack manifests, run lineage.
- Search Index: BM25/keyword and filters.
- Vector Index: embeddings with namespaces per opportunity/pack.
- Optional KG: entities (orgs, people, products), relations, claims.

## Knowledge Packs
- Definition: curated, versioned subset of sources for a specific opportunity or domain.
- Manifest: list of sources (by hash), embedded index refs, labels, owners, approvals, effective dates.
- Lifecycle: propose → curate → approve → use → retire; immutable after approval (new version increments).

## Governance
- Roles: Source Owner, Curator, Approver, Consumer.
- Policies: classification handling, residency, retention, external use rules, allowed models by class.
- Approvals: two-person rule for Restricted content; logs retained.
- Audits: quarterly spot checks for stale/out-of-policy content.

## Retrieval Strategy
- Hybrid retrieval: keyword + dense + re-ranking; freshness/time-decay scoring; section-aware query recipes.
- Citation resolution: include uri/hash/section_path; render as inline references.
- Query routing: per-section query templates (e.g., management approach vs. technical spec).

## Promotion & Deprecation
- Promotion: post-project retro identifies high-value content; curate into domain/base packs.
- Deprecation: mark superseded sources; maintain redirect to newer versions; soft-delete after retention.

## Quality & Evals
- Coverage to requirements, citation precision, factual consistency sampling.
- Human rubrics for clarity, persuasiveness, brand/style.
- Evals run pre-promotion; thresholds required for pack approval.

## Security & Privacy
- Tenant/project namespaces; pack-level ACLs; field-level redactions where needed.
- Model usage: allowlist per class; private endpoints preferred; zero-retention vendor config.
- Provenance: mandatory for all retrieved content.

## Operational Cadence
- Weekly: new source proposals, pack updates, stale content review.
- Monthly: eval scorecards, policy updates, training refresh.

