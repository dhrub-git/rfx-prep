# Technical Approach — Sydney Metro CMS Modernization

## Target Architecture
- Headless CMS with API-first content delivery
- CDN + WAF in AU regions; edge caching of public content
- API Gateway mediating content APIs; JWT/OIDC for auth
- Static site generation or SPA for front ends where appropriate
- Asset storage in AU; versioned; lifecycle policies

## Security & Privacy
- OIDC SSO with NSW Identity (or agency IdP); RBAC; audit logs
- Data residency: AU-only data stores and backups
- Secrets via Vault/Key Management; TLS everywhere
- CI/CD SAST+DAST; dependency scanning; container image signing

## Accessibility
- WCAG 2.1 AA as baseline; semantic HTML; ARIA where needed
- Automated checks in CI; manual testing in UAT with screen readers

## Performance & Resilience
- p95 < 500ms under 500 RPS via CDN caching, SSR/ISR, and DB tuning
- HA: multi-AZ deployment; health checks; autoscaling
- DR: RTO<=4h, RPO<=1h; tested quarterly; runbooks documented

## Migration Strategy
- Inventory legacy content; define mapping rules; plan redirects
- ETL pipeline to transform and import content; idempotent runs
- Parallel publishing period with sync to reduce cutover risk

## APIs & Integrations
- OpenAPI contracts; versioned; backward-compatible changes
- Webhooks for downstream systems; retry with backoff
- Editorial workflow integration (review, approve, publish)

## Observability
- OpenTelemetry traces; structured logs; dashboards for SLIs
- Error budgets for availability/latency; page-weight budgets

## Deliverables
- Architecture decision records; runbooks; security plan
- OpenAPI specs; migration plan; test strategy; training materials
