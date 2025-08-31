# Risk Log

| id | risk | impact | likelihood | mitigation | owner | status |
|----|------|--------|------------|-----------|-------|--------|
| R-001 | Model outage near deadline | High | Medium | Offline cache; backup model; earlier freeze | Ops | Open |
| R-002 | OCR/parse errors in scanned RFP | Medium | Medium | Confidence thresholds + HITL spot checks | Engineering | Open |
| R-003 | Data leakage via third-party tools | High | Low | Private endpoints, DLP, contracts | Security | Open |
| R-004 | SME bottlenecks delay approvals | Medium | Medium | Parallelize; set SLAs; backups | PM | Open |
| R-005 | Page-limit non-compliance | Medium | Low | Pre-flight checks; lints; template guardrails | QA | Open |
