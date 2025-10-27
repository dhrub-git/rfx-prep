# Detailed Project Schedule
## Sydney Metro CMS Modernization Project
### HCL Technologies Australia

**Document Version:** 1.0
**Date:** October 2025
**Project Duration:** 18 weeks (4.5 months)
**Start Date:** 6 January 2025
**End Date:** 20 June 2025

---

## 1. Executive Summary

This document outlines the detailed project schedule for the Sydney Metro CMS Modernization project. The project is structured across 6 phases over an 18-week period, delivering a modern, scalable, and secure content management system based on Contentful headless CMS.

### Key Schedule Highlights
- **Total Duration:** 18 weeks
- **Phases:** 6 distinct phases with clear milestones
- **Working Days:** 90 business days
- **Resource Commitment:** 8-12 FTEs across phases
- **Critical Path Duration:** 15 weeks
- **Buffer Allocation:** 3 weeks distributed across phases

---

## 2. Project Timeline Overview

| Phase | Duration | Start Date | End Date | Key Deliverables |
|-------|----------|------------|----------|------------------|
| Phase 1: Discovery | 2 weeks | 6 Jan 2025 | 17 Jan 2025 | NFRs, Content Audit, Technical Assessment |
| Phase 2: Architecture & Design | 2 weeks | 20 Jan 2025 | 31 Jan 2025 | Architecture Blueprint, Migration Plan |
| Phase 3: Build & Configure | 6 weeks | 3 Feb 2025 | 14 Mar 2025 | Configured CMS, CI/CD Pipeline, Templates |
| Phase 4: Migration | 4 weeks | 17 Mar 2025 | 11 Apr 2025 | Migrated Content, Redirect Maps, QA |
| Phase 5: Testing & Hardening | 3 weeks | 14 Apr 2025 | 2 May 2025 | Test Reports, Performance Validation |
| Phase 6: Cutover & Handover | 1 week | 5 May 2025 | 9 May 2025 | Go-Live, Training, Support Documentation |
| **Buffer Period** | 6 weeks | 12 May 2025 | 20 Jun 2025 | Hypercare, Issue Resolution, Optimization |

---

## 3. Phase 1: Discovery (2 Weeks)

**Objective:** Understand current state, gather requirements, and establish project foundations.

### 3.1 Week 1: Project Initiation & Discovery (6-10 Jan 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 6 Jan | Project kickoff meeting<br>Stakeholder introductions<br>Communication plan finalization | PM, All Leads | None | Kickoff minutes, RACI matrix |
| Tue 7 Jan | Current state CMS analysis<br>Access to legacy systems<br>Environment setup | Solution Architect, Lead Dev | Kickoff complete | Access credentials, System inventory |
| Wed 8 Jan | Stakeholder workshop #1<br>Business requirements gathering<br>User role definition | PM, BA, Content Lead | System access | Requirements document (draft) |
| Thu 9 Jan | Content audit initiation<br>Content types identification<br>Asset inventory | Content Migration Lead | System access | Content inventory (50% complete) |
| Fri 10 Jan | Non-functional requirements workshop<br>Performance targets<br>Security requirements | Solution Architect, SRE, Security | Business requirements | NFR document (draft) |

### 3.2 Week 2: Requirements Finalization & Planning (13-17 Jan 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 13 Jan | Content audit completion<br>Volume analysis<br>Taxonomy review | Content Migration Lead | Week 1 inventory | Complete content audit report |
| Tue 14 Jan | Technical constraints assessment<br>Integration points identification<br>API requirements | Lead Dev, Integration Specialist | System analysis | Technical constraints document |
| Wed 15 Jan | Accessibility requirements<br>WCAG 2.1 AA compliance review<br>Current gaps analysis | Accessibility SME, QA | NFR workshop | Accessibility requirements doc |
| Thu 16 Jan | Risk assessment workshop<br>Dependency mapping<br>Mitigation planning | PM, All Leads | All discovery activities | Risk register, Mitigation plan |
| Fri 17 Jan | **Milestone M1 Review**<br>NFR approval meeting<br>Discovery phase sign-off | PM, Stakeholders | All Week 2 tasks | **M1: Discovery Complete** |

### Phase 1 Resources
- **Team Size:** 8 FTEs
- **Effort:** 80 person-days
- **Critical Path:** Content audit + NFR definition (10 days)

---

## 4. Phase 2: Architecture & Design (2 Weeks)

**Objective:** Design target architecture, migration strategy, and technical blueprints.

### 4.1 Week 3: Architecture Definition (20-24 Jan 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 20 Jan | Architecture workshop kickoff<br>Technology stack selection<br>Contentful setup plan | Solution Architect, Lead Dev | M1 approved | Architecture approach document |
| Tue 21 Jan | Content modeling<br>Content type definitions<br>Relationship mapping | Content Architect, Content Lead | Content audit | Content model blueprint |
| Wed 22 Jan | API design<br>GraphQL schema definition<br>Integration patterns | Lead Dev, API Specialist | Content model | API specification document |
| Thu 23 Jan | Security architecture<br>Authentication/authorization design<br>Data protection strategy | Security Architect, SRE | NFRs, API design | Security architecture document |
| Fri 24 Jan | Infrastructure design<br>Hosting strategy (Vercel)<br>CDN configuration plan | SRE, DevOps Engineer | Architecture approach | Infrastructure design document |

### 4.2 Week 4: Migration Planning & Design Review (27-31 Jan 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 27 Jan | Migration strategy definition<br>ETL pipeline design<br>Data transformation rules | Content Migration Lead, Lead Dev | Content audit, Content model | Migration strategy document |
| Tue 28 Jan | Migration runbook creation<br>Rollback procedures<br>Validation criteria | Migration Lead, QA Lead | Migration strategy | Migration runbook (draft) |
| Wed 29 Jan | Redirect mapping strategy<br>URL structure analysis<br>SEO preservation plan | SEO Specialist, Lead Dev | Content audit | Redirect strategy document |
| Thu 30 Jan | Design review session<br>Architecture walkthrough<br>Stakeholder Q&A | Solution Architect, All Leads | All design documents | Design review minutes |
| Fri 31 Jan | **Milestone M2 Review**<br>Architecture approval<br>Design sign-off | PM, Stakeholders, Architects | All Week 4 tasks | **M2: Architecture Signed-Off** |

### Phase 2 Resources
- **Team Size:** 8 FTEs
- **Effort:** 80 person-days
- **Critical Path:** Content modeling + API design (8 days)

---

## 5. Phase 3: Build & Configure (6 Weeks)

**Objective:** Configure Contentful CMS, build frontend, establish CI/CD, and develop integrations.

### 5.1 Week 5-6: CMS Setup & Core Configuration (3-14 Feb 2025)

| Week | Tasks | Owner | Duration | Deliverables |
|------|-------|-------|----------|--------------|
| Week 5 | **Contentful Environment Setup**<br>• Space creation (Dev/Staging/Prod)<br>• Content type implementation<br>• Field validations<br>• Localization setup | Lead Dev, CMS Developer | 5 days | Configured Contentful spaces |
| Week 5 | **Initial Content Types**<br>• Page templates<br>• News articles<br>• Service pages<br>• Component library | CMS Developer, Content Architect | 5 days | 15-20 content types implemented |
| Week 6 | **Editorial Workflow**<br>• Review/approval workflows<br>• Publishing rules<br>• User roles & permissions | CMS Developer, Content Lead | 5 days | Workflow configurations |
| Week 6 | **CI/CD Pipeline - Phase 1**<br>• Repository setup<br>• Build automation<br>• Environment provisioning | DevOps Engineer, Lead Dev | 5 days | Basic CI/CD pipeline |

### 5.2 Week 7-8: Frontend Development & Integration (17 Feb-28 Feb 2025)

| Week | Tasks | Owner | Duration | Deliverables |
|------|-------|-------|----------|--------------|
| Week 7 | **Next.js Application Setup**<br>• Project scaffolding<br>• TypeScript configuration<br>• Routing architecture<br>• Static generation setup | Frontend Lead, Developers (2) | 5 days | Next.js application foundation |
| Week 7 | **Component Development**<br>• Design system implementation<br>• Reusable components<br>• Accessibility integration | Frontend Developers (2), Accessibility SME | 5 days | Component library (50% complete) |
| Week 8 | **API Integration**<br>• Contentful GraphQL queries<br>• Data fetching layer<br>• Error handling | Frontend Lead, Backend Dev | 5 days | Integrated API layer |
| Week 8 | **Template Development**<br>• Page templates<br>• Dynamic routing<br>• Preview mode | Frontend Developers (2) | 5 days | 10+ page templates |

### 5.3 Week 9-10: Advanced Features & Pipeline Completion (3-14 Mar 2025)

| Week | Tasks | Owner | Duration | Deliverables |
|------|-------|-------|----------|--------------|
| Week 9 | **Search Implementation**<br>• Search service integration<br>• Indexing configuration<br>• Search UI components | Backend Dev, Frontend Dev | 5 days | Working search functionality |
| Week 9 | **Media Management**<br>• Asset upload/processing<br>• Image optimization<br>• Video embedding | CMS Developer, Frontend Dev | 5 days | Media management system |
| Week 10 | **CI/CD Pipeline - Complete**<br>• Automated testing integration<br>• Deployment automation<br>• Environment promotion | DevOps Engineer, QA Automation | 5 days | Full CI/CD pipeline |
| Week 10 | **Monitoring & Logging**<br>• Application monitoring<br>• Error tracking<br>• Performance monitoring | SRE, DevOps Engineer | 5 days | Monitoring dashboard |
| Fri 14 Mar | **Milestone M3 Review**<br>• CMS demonstration<br>• Technical walkthrough | PM, All Leads | 1 day | **M3: CMS Configured & CI/CD Live** |

### Phase 3 Resources
- **Team Size:** 10-12 FTEs
- **Effort:** 300 person-days
- **Critical Path:** CMS setup → Frontend development → CI/CD (25 days)

---

## 6. Phase 4: Migration (4 Weeks)

**Objective:** Migrate content from legacy CMS to Contentful, validate data integrity, and establish redirects.

### 6.1 Week 11: Migration Pipeline Development (17-21 Mar 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 17 Mar | ETL pipeline development<br>Legacy export scripts<br>Data extraction testing | Migration Lead, Backend Dev | M3 complete | ETL scripts (draft) |
| Tue 18 Mar | Data transformation logic<br>Content mapping rules<br>Field conversions | Migration Lead, Content Architect | ETL scripts | Transformation rules document |
| Wed 19 Mar | Contentful import scripts<br>Batch processing logic<br>Error handling | Backend Dev, Migration Lead | Transformation rules | Import scripts |
| Thu 20 Mar | Migration pipeline testing<br>Small batch test (100 items)<br>Validation checks | QA, Migration Lead | Import scripts | Test results report |
| Fri 21 Mar | Pipeline optimization<br>Performance tuning<br>Error recovery procedures | Migration Lead, Backend Dev | Test results | Optimized pipeline |

### 6.2 Week 12: Dry Run Migration (24-28 Mar 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 24 Mar | Dry run preparation<br>Environment setup<br>Backup creation | SRE, Migration Lead | Optimized pipeline | Staging environment ready |
| Tue 25 Mar | **Migration Dry Run**<br>Full content migration to staging<br>Real-time monitoring | Migration Lead, All Dev Team | Staging environment | Migrated content (staging) |
| Wed 26 Mar | Data validation<br>Content integrity checks<br>Relationship verification | QA, Content Lead | Migration complete | Validation report |
| Thu 27 Mar | Issue identification<br>Data quality assessment<br>Gap analysis | Migration Lead, QA | Validation report | Issue log, Gap analysis |
| Fri 28 Mar | Dry run retrospective<br>Pipeline adjustments<br>Runbook refinement | PM, Migration Lead, All Leads | Issue log | Updated migration runbook |

### 6.3 Week 13: Redirect Mapping & Validation (31 Mar-4 Apr 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 31 Mar | URL mapping generation<br>Old URL → New URL mapping<br>Pattern-based rules | SEO Specialist, Migration Lead | Content migration | URL mapping spreadsheet |
| Tue 1 Apr | Redirect rules implementation<br>301 redirects configuration<br>Edge function setup (Vercel) | Backend Dev, DevOps Engineer | URL mapping | Redirect configuration |
| Wed 2 Apr | Redirect testing<br>Automated link checking<br>SEO validation | QA, SEO Specialist | Redirect configuration | Redirect test report |
| Thu 3 Apr | Link validation<br>Internal link checks<br>Broken link identification | QA, Content Lead | Content migration | Link validation report |
| Fri 4 Apr | SEO meta-data validation<br>Sitemap generation<br>Robots.txt configuration | SEO Specialist | All validation complete | SEO validation report |

### 6.4 Week 14: Production Migration Preparation (7-11 Apr 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 7 Apr | Pipeline fixes from dry run<br>Bug resolution<br>Performance optimization | Migration Lead, Backend Dev | Dry run retrospective | Updated pipeline |
| Tue 8 Apr | Second dry run (if needed)<br>Selective re-migration<br>Final validation | Migration Lead, QA | Pipeline fixes | Final validation report |
| Wed 9 Apr | Production migration rehearsal<br>Timing validation<br>Cutover procedure review | Migration Lead, All Leads | Second dry run | Rehearsal results |
| Thu 10 Apr | Go/No-Go preparation<br>Checklist completion<br>Risk assessment | PM, All Leads | Rehearsal complete | Go/No-Go assessment |
| Fri 11 Apr | **Milestone M4 Review**<br>Migration sign-off<br>Production readiness | PM, Stakeholders | All Week 14 tasks | **M4: Migration Validated** |

### Phase 4 Resources
- **Team Size:** 10 FTEs
- **Effort:** 200 person-days
- **Critical Path:** ETL development → Dry run → Validation (15 days)

---

## 7. Phase 5: Testing & Hardening (3 Weeks)

**Objective:** Comprehensive testing across performance, accessibility, security, and user acceptance.

### 7.1 Week 15: Performance & Load Testing (14-18 Apr 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 14 Apr | Performance test planning<br>Test scenarios definition<br>Load profiles | QA Lead, SRE | M4 approved | Performance test plan |
| Tue 15 Apr | Load testing execution<br>JMeter/k6 scripts<br>Peak traffic simulation | QA, SRE | Test plan | Load test results |
| Wed 16 Apr | Performance analysis<br>Bottleneck identification<br>CDN effectiveness | SRE, Lead Dev | Load test results | Performance analysis report |
| Thu 17 Apr | Performance optimization<br>Caching improvements<br>Query optimization | Lead Dev, Frontend Dev | Analysis report | Optimization changes |
| Fri 18 Apr | Re-testing<br>Performance validation<br>Benchmark comparison | QA, SRE | Optimization complete | Performance test report (final) |

### 7.2 Week 16: Accessibility & Security Testing (21-25 Apr 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 21 Apr | Accessibility audit<br>WCAG 2.1 AA automated testing<br>Screen reader testing | Accessibility SME, QA | Performance testing complete | Accessibility audit report |
| Tue 22 Apr | Manual accessibility testing<br>Keyboard navigation<br>Color contrast validation | Accessibility SME | Automated testing | Manual test results |
| Wed 23 Apr | Security testing initiation<br>OWASP Top 10 checks<br>Vulnerability scanning | Security Architect, QA | Accessibility testing | Security scan results |
| Thu 24 Apr | Penetration testing<br>API security validation<br>Authentication testing | Security Specialist | Security scanning | Penetration test report |
| Fri 25 Apr | Issue remediation planning<br>Priority classification<br>Fix assignment | PM, Leads | All test reports | Issue remediation plan |

### 7.3 Week 17: UAT & Issue Resolution (28 Apr-2 May 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 28 Apr | UAT preparation<br>Test case distribution<br>User training | QA Lead, Content Lead | All testing complete | UAT test cases |
| Tue 29 Apr | **UAT Day 1**<br>Content editors testing<br>Publishing workflows<br>Feedback collection | Content Team, QA | UAT preparation | UAT feedback (Day 1) |
| Wed 30 Apr | **UAT Day 2**<br>Frontend functionality<br>Search and navigation<br>Accessibility validation | Stakeholders, QA | UAT Day 1 | UAT feedback (Day 2) |
| Thu 1 May | Bug fixing<br>High/critical issues<br>Accessibility fixes | Dev Team, All | UAT feedback | Bug fixes deployed |
| Fri 2 May | **Milestone M5 Review**<br>Test results presentation<br>Hardening sign-off | PM, QA Lead, Stakeholders | All testing complete | **M5: Testing Complete** |

### Phase 5 Resources
- **Team Size:** 10 FTEs
- **Effort:** 150 person-days
- **Critical Path:** Performance testing → UAT (12 days)

---

## 8. Phase 6: Cutover & Handover (1 Week)

**Objective:** Production deployment, go-live, knowledge transfer, and transition to support.

### 8.1 Production Cutover (5-9 May 2025)

| Day | Tasks | Owner | Dependencies | Deliverables |
|-----|-------|-------|--------------|--------------|
| Mon 5 May | **Go/No-Go Meeting**<br>Final readiness review<br>Deployment approval | PM, Stakeholders, All Leads | M5 approved | Go-live approval |
| Mon 5 May PM | Production migration<br>Content cutover<br>DNS switchover preparation | Migration Lead, SRE, DevOps | Go-live approval | Migration execution log |
| Tue 6 May | **Go-Live**<br>DNS cutover<br>Traffic monitoring<br>Issue triage | All Team | Migration complete | Live production system |
| Wed 7 May | Post-launch monitoring<br>Performance tracking<br>Error resolution | SRE, Dev Team | Go-live | Monitoring reports |
| Thu 8 May | Training delivery<br>Content editor training<br>Admin training | Content Lead, Training Specialist | Go-live stable | Training sessions delivered |
| Thu 8 May | Documentation handover<br>Support runbooks<br>Operational procedures | PM, Tech Writer, All Leads | Training complete | Support documentation |
| Fri 9 May | **Milestone M6**<br>Project closure meeting<br>Lessons learned<br>Handover complete | PM, All Stakeholders | All tasks complete | **M6: Go-Live & Handover** |

### Phase 6 Resources
- **Team Size:** 12 FTEs (full team)
- **Effort:** 60 person-days
- **Critical Path:** Go/No-Go → Migration → Go-live (3 days)

---

## 9. Hypercare & Buffer Period (6 Weeks)

**Period:** 12 May 2025 - 20 June 2025

### 9.1 Hypercare Support (Weeks 18-20)

| Week | Focus Areas | Team | Activities |
|------|-------------|------|------------|
| Week 18 | Immediate post-launch support | Full team (8 FTEs) | 24/7 monitoring, rapid issue response, user support |
| Week 19 | Stabilization | Core team (6 FTEs) | Bug fixes, minor enhancements, performance tuning |
| Week 20 | Optimization | Core team (4 FTEs) | Content optimization, workflow refinements, documentation updates |

### 9.2 Risk Buffer Allocation (Weeks 21-23)

| Week | Purpose | Team | Contingency |
|------|---------|------|-------------|
| Week 21 | Migration issues buffer | 4 FTEs | Additional migration cycles, data corrections |
| Week 22 | Testing extension buffer | 4 FTEs | Additional UAT, security testing, accessibility remediation |
| Week 23 | Go-live delay buffer | 4 FTEs | Delayed cutover, additional hardening, stakeholder requests |

---

## 10. Critical Path Analysis

### 10.1 Critical Path Activities (15 Weeks)

1. **Discovery → NFR Approval** (2 weeks)
2. **Content Modeling → API Design** (1 week)
3. **CMS Configuration** (2 weeks)
4. **Frontend Development** (2 weeks)
5. **ETL Development → Dry Run** (2 weeks)
6. **Migration Validation** (1 week)
7. **Performance Testing → UAT** (2 weeks)
8. **Go-Live Preparation → Cutover** (1 week)
9. **Hypercare** (2 weeks)

### 10.2 Critical Dependencies

| Dependent Activity | Prerequisite | Lead Time | Risk |
|-------------------|--------------|-----------|------|
| Architecture Design | NFR Approval | 0 days | High - Delays cascade |
| Frontend Development | Content Model Complete | 0 days | High - Blocks integration |
| Migration Dry Run | ETL Pipeline Ready | 0 days | Critical - No workaround |
| UAT | All Testing Complete | 0 days | Medium - Can be compressed |
| Go-Live | UAT Sign-Off | 0 days | Critical - Cannot bypass |

---

## 11. Resource Allocation by Phase

| Phase | PM | Arch | Dev | Content | SRE | QA | Security | Total FTE |
|-------|----|----|-----|---------|-----|----|---------:|-----------|
| Phase 1 | 1 | 1 | 1 | 2 | 1 | 1 | 1 | 8 |
| Phase 2 | 1 | 2 | 2 | 1 | 1 | 1 | 1 | 9 |
| Phase 3 | 1 | 1 | 5 | 1 | 2 | 1 | 1 | 12 |
| Phase 4 | 1 | 0.5 | 3 | 2 | 1 | 2 | 0.5 | 10 |
| Phase 5 | 1 | 0.5 | 2 | 1 | 2 | 3 | 1 | 10.5 |
| Phase 6 | 1 | 1 | 4 | 2 | 2 | 1 | 1 | 12 |
| Hypercare | 0.5 | 0.5 | 3 | 1 | 2 | 1 | 0 | 8 |

**Peak Capacity:** 12 FTEs (Phase 3 & 6)
**Average Capacity:** 9.9 FTEs
**Total Effort:** 970 person-days

---

## 12. Key Milestones & Success Criteria

| Milestone | Date | Success Criteria | Approval Required |
|-----------|------|------------------|-------------------|
| M1: Discovery Complete | 17 Jan 2025 | ✓ NFRs approved<br>✓ Content audit complete<br>✓ Risk register finalized | Sponsor, PM |
| M2: Architecture Signed-Off | 31 Jan 2025 | ✓ Architecture approved<br>✓ Migration plan accepted<br>✓ Security review passed | Architect, Sponsor |
| M3: CMS Configured | 14 Mar 2025 | ✓ 15+ content types live<br>✓ CI/CD operational<br>✓ Templates deployed | Tech Lead, PM |
| M4: Migration Validated | 11 Apr 2025 | ✓ Dry run successful<br>✓ Data integrity confirmed<br>✓ Redirects tested | Migration Lead, QA |
| M5: Testing Complete | 2 May 2025 | ✓ Performance benchmarks met<br>✓ WCAG 2.1 AA compliant<br>✓ UAT approved | QA Lead, Sponsor |
| M6: Go-Live | 9 May 2025 | ✓ Production cutover successful<br>✓ Training delivered<br>✓ Support runbooks ready | All Stakeholders |

---

## 13. Risk Buffer Allocations

| Risk Category | Buffer Time | Trigger | Mitigation |
|---------------|-------------|---------|------------|
| Discovery delays | 3 days | Stakeholder unavailability | Fast-track workshops, parallel activities |
| Architecture changes | 5 days | Design revisions post-review | Modular design, early validation |
| Development issues | 10 days | Technical blockers, API changes | Experienced team, daily standups |
| Migration failures | 7 days | Data quality issues | Multiple dry runs, rollback procedures |
| Testing extensions | 5 days | Failed UAT, accessibility gaps | Early testing, parallel tracks |
| Go-live delays | 3 days | Last-minute issues | Strong cutover runbook, rehearsals |

**Total Buffer:** 33 days (6.6 weeks) across 18-week schedule = 37% buffer

---

## 14. Assumptions & Constraints

### 14.1 Assumptions
1. Sydney Metro stakeholders available for workshops and approvals within 2 business days
2. Access to legacy CMS systems granted by Day 2 of project
3. Contentful enterprise license available from project start
4. Vercel hosting infrastructure provisioned within Week 1
5. Content freeze period of 24 hours accepted for final migration
6. 8-12 FTE resources available throughout project duration
7. No major scope changes after Phase 2 architecture approval

### 14.2 Constraints
1. **Fixed Deadline:** Must complete by 20 June 2025 (18 weeks)
2. **Budget:** Fixed-price contract, no overruns permitted
3. **Regulatory:** Must maintain WCAG 2.1 AA compliance throughout
4. **Operational:** Maximum 4-hour downtime window for cutover
5. **Technical:** Must integrate with existing Sydney Metro authentication system
6. **Resource:** Maximum 12 concurrent FTEs available

### 14.3 Dependencies
1. **External:** Sydney Metro IT team for system access, DNS changes, firewall rules
2. **Internal:** HCL's Contentful and Vercel partnerships for licensing and support
3. **Vendor:** Contentful support for enterprise features, migration assistance
4. **Third-party:** SEO tools, accessibility testing tools, performance monitoring tools

---

## 15. Gantt Chart (Text Representation)

```
Phase                    | Jan 2025      | Feb 2025      | Mar 2025      | Apr 2025      | May 2025      | Jun 2025      |
                         | W1 W2 W3 W4  | W5 W6 W7 W8  | W9 W10W11W12 | W13W14W15W16 | W17W18W19W20 | W21W22W23    |
-------------------------|--------------|--------------|--------------|--------------|--------------|--------------|
Phase 1: Discovery       | ██ ██        |              |              |              |              |              |
Phase 2: Architecture    |       ██ ██  |              |              |              |              |              |
Phase 3: Build           |              | ██ ██ ██ ██  | ██ ██        |              |              |              |
Phase 4: Migration       |              |              |       ██ ██  | ██ ██        |              |              |
Phase 5: Testing         |              |              |              |       ██ ██  | ██           |              |
Phase 6: Cutover         |              |              |              |              |    ██        |              |
Hypercare                |              |              |              |              |       ██ ██  | ██           |
Buffer Period            |              |              |              |              |              |    ██ ██ ██  |
-------------------------|--------------|--------------|--------------|--------------|--------------|--------------|
M1 ↓                     |    ✓         |              |              |              |              |              |
M2 ↓                     |          ✓   |              |              |              |              |              |
M3 ↓                     |              |          ✓   |              |              |              |              |
M4 ↓                     |              |              |          ✓   |              |              |              |
M5 ↓                     |              |              |              |              | ✓            |              |
M6 ↓                     |              |              |              |              |    ✓         |              |
```

---

## 16. Deployment Schedule

| Deployment | Environment | Date | Scope | Rollback Time |
|------------|-------------|------|-------|---------------|
| Initial Deploy | Development | 3 Feb 2025 | CMS configuration, basic templates | 15 minutes |
| Integration Deploy | Development | 10 Feb 2025 | API integration, components | 30 minutes |
| Feature Complete | Development | 14 Mar 2025 | Full feature set, CI/CD live | 1 hour |
| Migration Dry Run | Staging | 25 Mar 2025 | Complete content migration | 2 hours |
| UAT Deploy | Staging | 28 Apr 2025 | Production-ready build | 1 hour |
| **Production Go-Live** | **Production** | **6 May 2025** | **Full cutover** | **4 hours** |

---

## 17. Change Control Process

### 17.1 Change Request Procedure
1. Change request submitted to PM with impact analysis
2. PM reviews with technical leads (1 business day)
3. Impact assessment on schedule, budget, and scope (2 business days)
4. Change Control Board review (weekly meetings)
5. Sponsor approval required for >3 day schedule impact or >5% budget impact
6. Approved changes integrated into project plan within 2 business days

### 17.2 Emergency Changes
- Critical security or production issues: Immediate approval by PM and Tech Lead
- Stakeholder notification within 4 hours
- Retrospective review at next Change Control Board meeting

---

## 18. Communication & Reporting

### 18.1 Status Reporting Schedule

| Report Type | Frequency | Audience | Content |
|-------------|-----------|----------|---------|
| Daily Standup | Daily, 9:00 AM | Delivery Team | Progress, blockers, plan for day |
| Weekly Status Report | Friday 4:00 PM | Sponsor, Stakeholders | Phase progress, risks, upcoming milestones |
| Milestone Reviews | End of each phase | Sponsor, Executive Stakeholders | Deliverables review, approval gate |
| Risk Review | Bi-weekly | PM, Leads, Sponsor | Risk register updates, mitigation progress |
| Executive Dashboard | Weekly | C-level Executives | High-level metrics, budget, schedule variance |

### 18.2 Escalation Path
1. **Level 1:** Team Lead (4-hour response)
2. **Level 2:** Project Manager (8-hour response)
3. **Level 3:** Program Director (24-hour response)
4. **Level 4:** Sponsor/Executive (48-hour response)

---

## 19. Quality Gates

| Phase End | Quality Gate | Criteria | Approval |
|-----------|--------------|----------|----------|
| Phase 1 | Discovery Review | NFRs documented, content audit complete, risks identified | PM, Sponsor |
| Phase 2 | Architecture Review | Design approved, security signed-off, migration plan reviewed | Solution Architect, Security Lead |
| Phase 3 | Technical Review | CI/CD operational, code review passed, 15+ content types live | Tech Lead, QA Lead |
| Phase 4 | Migration Review | Data integrity >99.5%, redirects tested, validation complete | Migration Lead, QA Lead |
| Phase 5 | Quality Assurance | Performance benchmarks met, WCAG AA compliant, UAT passed | QA Lead, Accessibility SME |
| Phase 6 | Go-Live Approval | Production stable, training complete, support ready | All Stakeholders |

---

## 20. Project Closeout

### 20.1 Closeout Activities (Week 18)
- Lessons learned workshop
- Project documentation archival
- Final financial reconciliation
- Contract closure
- Celebration event

### 20.2 Post-Project Review (Week 20)
- Benefits realization assessment
- Performance against KPIs
- Customer satisfaction survey
- Continuous improvement recommendations

---

**Document Approval:**

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Manager | [Name] | _____________ | _______ |
| Solution Architect | [Name] | _____________ | _______ |
| Project Sponsor (Sydney Metro) | [Name] | _____________ | _______ |

**Document Control:**
- **Version:** 1.0
- **Last Updated:** October 2025
- **Next Review:** Start of Phase 2
- **Owner:** HCL Technologies Project Manager

---

*End of Detailed Project Schedule*
