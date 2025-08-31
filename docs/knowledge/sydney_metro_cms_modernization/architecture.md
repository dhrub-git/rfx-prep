# Architecture (Text + Diagram)

```
Users ──► CDN/WAF (AU) ──► Frontend (SSR/SPA)
                               │
                               ▼
                        API Gateway (JWT/OIDC)
                         │            │
            Content APIs ◄┘            └► Webhooks
                         │
                         ▼
                    Headless CMS (AU)
                         │
                         ├─ Asset Store (AU S3/Blob)
                         ├─ Search Index
                         └─ RDBMS (pgvector optional)

Observability: OpenTelemetry ▸ Logs ▸ Metrics ▸ Traces
Security: OIDC, RBAC, KMS/Vault, AU-only data
DR: Cross-AZ backups, tested runbooks (RTO<=4h, RPO<=1h)
```
