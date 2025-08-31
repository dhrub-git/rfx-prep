# Decision Log

| id | date | area | decision | options considered | rationale | approvers | links |
|----|------|------|----------|--------------------|----------|-----------|-------|
| D-001 | 2025-08-30 | Models | Use private endpoints only | Public API; Private VPC | Data control and latency | Security, Architect | |
| D-002 | 2025-08-30 | Orchestration | Use Temporal for DAGs | Camunda; Prefect; LangGraph | Strong reliability + retries + signals | Architect, Ops | |
| D-003 | 2025-08-30 | Retrieval | Hybrid BM25 + embeddings + re-ranker | Keyword-only; Dense-only | Best quality + explainability | ML, Architect | |
| D-004 | 2025-08-30 | Security | OIDC + RBAC; Vault for secrets | Basic API keys | Compliance and least-privilege | Security | |
| D-005 | 2025-08-30 | Storage | pgvector in Postgres | External vector DB | Fewer moving parts, simpler ops | Data, Ops | |
