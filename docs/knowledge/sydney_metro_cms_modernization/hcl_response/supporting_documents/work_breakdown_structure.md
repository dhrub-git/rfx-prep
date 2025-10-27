# Work Breakdown Structure (WBS)
## Sydney Metro CMS Modernization Project
### HCL Technologies Australia

**Document Version:** 1.0
**Date:** October 2025
**Project Duration:** 18 weeks
**Total Effort:** 970 person-days
**Total Cost Estimate:** $1,940,000 AUD

---

## 1. Executive Summary

This Work Breakdown Structure (WBS) provides a hierarchical decomposition of the Sydney Metro CMS Modernization project into manageable work packages. The WBS is organized into 6 major phases, each broken down into deliverables, work packages, and detailed tasks with effort estimates, cost allocations, and responsibility assignments.

### WBS Overview
- **Level 1:** 6 Phases
- **Level 2:** 24 Major Deliverables
- **Level 3:** 78 Work Packages
- **Level 4:** 312+ Individual Tasks

### Cost Summary by Phase
| Phase | Effort (Person-Days) | Cost (AUD) | % of Total |
|-------|---------------------|------------|------------|
| Phase 1: Discovery | 80 | $160,000 | 8.2% |
| Phase 2: Architecture & Design | 80 | $160,000 | 8.2% |
| Phase 3: Build & Configure | 300 | $600,000 | 30.9% |
| Phase 4: Migration | 200 | $400,000 | 20.6% |
| Phase 5: Testing & Hardening | 150 | $300,000 | 15.5% |
| Phase 6: Cutover & Handover | 60 | $120,000 | 6.2% |
| Hypercare & Buffer | 100 | $200,000 | 10.3% |
| **Total** | **970** | **$1,940,000** | **100%** |

*Note: Cost calculated at $2,000 AUD per person-day (blended rate)*

---

## 2. WBS Hierarchy

```
1.0 Sydney Metro CMS Modernization
├── 1.1 Discovery
│   ├── 1.1.1 Project Initiation
│   ├── 1.1.2 Current State Analysis
│   ├── 1.1.3 Requirements Gathering
│   └── 1.1.4 Risk Assessment
├── 1.2 Architecture & Design
│   ├── 1.2.1 Solution Architecture
│   ├── 1.2.2 Content Modeling
│   ├── 1.2.3 Migration Planning
│   └── 1.2.4 Security Design
├── 1.3 Build & Configure
│   ├── 1.3.1 CMS Configuration
│   ├── 1.3.2 Frontend Development
│   ├── 1.3.3 API Development
│   ├── 1.3.4 CI/CD Setup
│   └── 1.3.5 Infrastructure Setup
├── 1.4 Migration
│   ├── 1.4.1 ETL Development
│   ├── 1.4.2 Content Migration
│   ├── 1.4.3 Redirect Implementation
│   └── 1.4.4 Data Validation
├── 1.5 Testing & Hardening
│   ├── 1.5.1 Performance Testing
│   ├── 1.5.2 Accessibility Testing
│   ├── 1.5.3 Security Testing
│   └── 1.5.4 User Acceptance Testing
├── 1.6 Cutover & Handover
│   ├── 1.6.1 Production Deployment
│   ├── 1.6.2 Training
│   ├── 1.6.3 Documentation
│   └── 1.6.4 Knowledge Transfer
└── 1.7 Project Management
    ├── 1.7.1 Planning & Control
    ├── 1.7.2 Risk Management
    ├── 1.7.3 Quality Assurance
    └── 1.7.4 Stakeholder Management
```

---

## 3. Phase 1: Discovery (1.1)

### 3.1 WBS 1.1.1: Project Initiation

**Duration:** 3 days | **Effort:** 18 person-days | **Cost:** $36,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.1.1.1 | Project Kickoff | Conduct kickoff meeting, introduce team, review charter | 2 | PM | R: PM; A: Sponsor; C: All Leads; I: Team |
| 1.1.1.2 | Communication Plan | Develop and approve communication strategy | 1 | PM | R: PM; A: Sponsor; C: Stakeholders |
| 1.1.1.3 | RACI Matrix | Define roles and responsibilities | 1 | PM | R: PM; A: Sponsor; C: All Leads |
| 1.1.1.4 | Project Repository Setup | Setup SharePoint/Confluence, document structure | 2 | PM, BA | R: PM; A: PM; C: Team |
| 1.1.1.5 | Governance Framework | Establish decision-making process, change control | 2 | PM | R: PM; A: Sponsor; C: Leads |
| 1.1.1.6 | Initial Risk Register | Identify initial project risks and mitigation strategies | 2 | PM, Leads | R: All Leads; A: PM; C: Team |
| 1.1.1.7 | Stakeholder Register | Identify and classify stakeholders, engagement plan | 2 | PM, BA | R: PM; A: Sponsor; C: BA |
| 1.1.1.8 | Schedule Baseline | Finalize project schedule, milestone dates | 2 | PM | R: PM; A: Sponsor; C: Leads |
| 1.1.1.9 | Budget Baseline | Confirm budget allocation by phase | 2 | PM, Finance | R: PM; A: Sponsor; C: Finance |
| 1.1.1.10 | Procurement | Finalize tool licenses (Contentful, Vercel, monitoring) | 2 | PM, Procurement | R: Procurement; A: PM; C: Tech Lead |

**Acceptance Criteria:**
- Project charter signed
- Communication plan approved
- All team members onboarded
- Project repository accessible to all stakeholders
- Initial risk register contains minimum 15 risks

---

### 3.2 WBS 1.1.2: Current State Analysis

**Duration:** 5 days | **Effort:** 25 person-days | **Cost:** $50,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.1.2.1 | System Access | Obtain access to legacy CMS environments (dev/prod) | 1 | Solution Architect | R: Sydney Metro IT; A: PM; C: Tech Lead |
| 1.1.2.2 | System Inventory | Document all CMS components, versions, dependencies | 3 | Solution Architect, Lead Dev | R: Solution Architect; A: PM; C: Sydney Metro |
| 1.1.2.3 | Architecture Documentation | Review existing architecture, integration points | 3 | Solution Architect | R: Solution Architect; A: PM; I: Sydney Metro IT |
| 1.1.2.4 | Content Analysis | Analyze content types, volumes, structure | 5 | Content Migration Lead | R: Content Lead; A: PM; C: Sydney Metro Content |
| 1.1.2.5 | Performance Baseline | Measure current system performance metrics | 2 | SRE | R: SRE; A: Tech Lead; C: Sydney Metro |
| 1.1.2.6 | Security Assessment | Review current security posture, vulnerabilities | 3 | Security Architect | R: Security; A: PM; I: Sydney Metro IT |
| 1.1.2.7 | Integration Mapping | Identify all external systems and APIs | 2 | Integration Specialist | R: Integration Spec; A: Lead Dev; C: Sydney Metro |
| 1.1.2.8 | User Workflow Analysis | Document current editorial workflows | 2 | BA, Content Lead | R: BA; A: PM; C: Content Lead |
| 1.1.2.9 | Analytics Review | Analyze current usage patterns, popular content | 2 | BA | R: BA; A: PM; C: Sydney Metro Marketing |
| 1.1.2.10 | Current State Report | Compile comprehensive current state documentation | 2 | Solution Architect, BA | R: Solution Architect; A: PM; C: Sponsor |

**Acceptance Criteria:**
- Complete system inventory document
- Access credentials provided for all environments
- Performance baseline established
- Current state report reviewed and approved
- All integration points documented

---

### 3.3 WBS 1.1.3: Requirements Gathering

**Duration:** 5 days | **Effort:** 30 person-days | **Cost:** $60,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.1.3.1 | Stakeholder Workshops | Conduct 3 workshops (business, technical, editorial) | 6 | PM, BA | R: BA; A: PM; C: All Stakeholders |
| 1.1.3.2 | Functional Requirements | Document functional requirements (50+ requirements) | 4 | BA | R: BA; A: PM; C: Stakeholders |
| 1.1.3.3 | Non-Functional Requirements | Define NFRs (performance, security, scalability) | 4 | Solution Architect, SRE | R: Solution Architect; A: PM; C: Sydney Metro |
| 1.1.3.4 | Accessibility Requirements | Document WCAG 2.1 AA requirements and gaps | 3 | Accessibility SME | R: Accessibility SME; A: QA Lead; C: PM |
| 1.1.3.5 | Content Requirements | Define content types, fields, taxonomies (draft) | 4 | Content Lead, BA | R: Content Lead; A: PM; C: Sydney Metro Content |
| 1.1.3.6 | Integration Requirements | Specify API requirements, authentication, data sync | 3 | Integration Specialist | R: Integration Spec; A: Lead Dev; C: Sydney Metro IT |
| 1.1.3.7 | User Stories | Create user stories for key personas (30+ stories) | 3 | BA | R: BA; A: PM; C: Stakeholders |
| 1.1.3.8 | Requirements Prioritization | MoSCoW prioritization with stakeholders | 1 | PM, BA | R: PM; A: Sponsor; C: BA, Stakeholders |
| 1.1.3.9 | Requirements Traceability | Setup traceability matrix, tool configuration | 1 | BA, QA Lead | R: BA; A: PM; C: QA Lead |
| 1.1.3.10 | Requirements Approval | Formal requirements review and sign-off | 1 | PM, BA | R: PM; A: Sponsor; C: All Leads |

**Acceptance Criteria:**
- Minimum 50 functional requirements documented
- NFRs approved covering 8 quality attributes
- WCAG 2.1 AA compliance requirements defined
- Requirements traceability matrix established
- Formal sign-off obtained from sponsor

---

### 3.4 WBS 1.1.4: Risk Assessment

**Duration:** 2 days | **Effort:** 7 person-days | **Cost:** $14,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.1.4.1 | Risk Identification Workshop | Brainstorm risks with team and stakeholders | 2 | PM, All Leads | R: All Leads; A: PM; C: Team |
| 1.1.4.2 | Risk Analysis | Assess probability and impact for each risk | 1 | PM | R: PM; A: PM; C: Leads |
| 1.1.4.3 | Risk Prioritization | Prioritize risks using risk matrix | 1 | PM | R: PM; A: PM; C: Sponsor |
| 1.1.4.4 | Mitigation Planning | Develop mitigation strategies for high/critical risks | 2 | PM, Leads | R: Risk Owners; A: PM; C: Team |
| 1.1.4.5 | Risk Register | Document risks in risk register tool | 1 | PM | R: PM; A: PM; I: Team |

**Acceptance Criteria:**
- Minimum 20 risks identified
- All high/critical risks have mitigation plans
- Risk register approved by sponsor
- Risk owners assigned

**Phase 1 Total:** 80 person-days | $160,000

---

## 4. Phase 2: Architecture & Design (1.2)

### 4.1 WBS 1.2.1: Solution Architecture

**Duration:** 5 days | **Effort:** 30 person-days | **Cost:** $60,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.2.1.1 | Architecture Workshop | Conduct 2-day architecture design workshop | 8 | Solution Architect, Leads | R: Solution Architect; A: PM; C: All Leads |
| 1.2.1.2 | Technology Stack Selection | Select and justify technology choices | 2 | Solution Architect, Lead Dev | R: Solution Architect; A: PM; C: Sponsor |
| 1.2.1.3 | High-Level Architecture | Design system architecture (C4 model Level 1-2) | 4 | Solution Architect | R: Solution Architect; A: PM; C: Tech Lead |
| 1.2.1.4 | Component Architecture | Detail component interactions (C4 Level 3) | 4 | Solution Architect, Lead Dev | R: Solution Architect; A: PM; C: Dev Team |
| 1.2.1.5 | Deployment Architecture | Design hosting, CDN, edge functions architecture | 3 | SRE, DevOps Engineer | R: SRE; A: Solution Architect; C: Lead Dev |
| 1.2.1.6 | Integration Architecture | Design API gateway, authentication, data sync | 3 | Integration Specialist, Lead Dev | R: Integration Spec; A: Solution Architect; C: Security |
| 1.2.1.7 | Scalability Design | Define auto-scaling, caching, performance strategy | 2 | SRE, Solution Architect | R: SRE; A: Solution Architect; C: PM |
| 1.2.1.8 | Disaster Recovery Plan | Design backup, failover, and recovery procedures | 2 | SRE | R: SRE; A: Solution Architect; C: PM |
| 1.2.1.9 | Architecture Documentation | Create comprehensive architecture document | 2 | Solution Architect | R: Solution Architect; A: PM; I: Team |

**Acceptance Criteria:**
- Architecture diagrams (C4 model) approved
- Technology stack documented and justified
- Scalability targets defined (e.g., 100k concurrent users)
- DR plan with RTO/RPO defined
- Architecture review completed with no critical issues

---

### 4.2 WBS 1.2.2: Content Modeling

**Duration:** 4 days | **Effort:** 18 person-days | **Cost:** $36,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.2.2.1 | Content Type Analysis | Analyze and categorize content from audit | 3 | Content Architect, Content Lead | R: Content Architect; A: PM; C: Sydney Metro |
| 1.2.2.2 | Content Model Design | Design 15-20 content types with fields | 5 | Content Architect | R: Content Architect; A: PM; C: Content Lead |
| 1.2.2.3 | Relationship Mapping | Define relationships between content types | 2 | Content Architect | R: Content Architect; A: PM; C: Lead Dev |
| 1.2.2.4 | Taxonomy Design | Design categories, tags, navigation taxonomy | 2 | Content Architect, SEO Specialist | R: Content Architect; A: PM; C: Sydney Metro |
| 1.2.2.5 | Localization Strategy | Define multi-language support (if required) | 1 | Content Architect | R: Content Architect; A: PM; C: Sydney Metro |
| 1.2.2.6 | Field Validation Rules | Define validation rules for content fields | 2 | Content Architect, Lead Dev | R: Content Architect; A: Lead Dev; C: Content Lead |
| 1.2.2.7 | Content Model Documentation | Document content model with examples | 2 | Content Architect | R: Content Architect; A: PM; I: Team |
| 1.2.2.8 | Content Model Review | Review with stakeholders and approve | 1 | Content Architect, PM | R: Content Architect; A: PM; C: Sponsor |

**Acceptance Criteria:**
- 15-20 content types designed
- All relationships documented
- Taxonomy approved by Sydney Metro content team
- Field validations defined for all fields
- Content model reviewed and approved

---

### 4.3 WBS 1.2.3: Migration Planning

**Duration:** 3 days | **Effort:** 15 person-days | **Cost:** $30,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.2.3.1 | Migration Strategy | Define migration approach (big bang vs phased) | 2 | Migration Lead, PM | R: Migration Lead; A: PM; C: Sponsor |
| 1.2.3.2 | ETL Design | Design extraction, transformation, load processes | 4 | Migration Lead, Backend Dev | R: Migration Lead; A: Lead Dev; C: Content Lead |
| 1.2.3.3 | Data Mapping | Map legacy fields to new content model | 3 | Migration Lead, Content Architect | R: Migration Lead; A: Content Architect; C: Sydney Metro |
| 1.2.3.4 | Migration Runbook | Create step-by-step migration procedures | 2 | Migration Lead | R: Migration Lead; A: PM; C: SRE |
| 1.2.3.5 | Validation Strategy | Define data validation and QA approach | 2 | QA Lead, Migration Lead | R: QA Lead; A: Migration Lead; C: Content Lead |
| 1.2.3.6 | Rollback Plan | Define rollback procedures and criteria | 1 | Migration Lead, SRE | R: Migration Lead; A: PM; C: SRE |
| 1.2.3.7 | Downtime Plan | Plan content freeze and cutover window | 1 | Migration Lead, PM | R: PM; A: Sponsor; C: Migration Lead |

**Acceptance Criteria:**
- Migration strategy approved
- ETL design documented
- Field mapping 100% complete
- Migration runbook reviewed by SRE
- Rollback plan approved

---

### 4.4 WBS 1.2.4: Security Design

**Duration:** 3 days | **Effort:** 17 person-days | **Cost:** $34,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.2.4.1 | Security Architecture | Design security layers (network, app, data) | 4 | Security Architect | R: Security Architect; A: PM; C: Solution Architect |
| 1.2.4.2 | Authentication Design | Design SSO integration, user auth flows | 3 | Security Architect, Lead Dev | R: Security Architect; A: Lead Dev; C: Sydney Metro IT |
| 1.2.4.3 | Authorization Model | Define role-based access control (RBAC) | 2 | Security Architect | R: Security Architect; A: PM; C: Content Lead |
| 1.2.4.4 | Data Protection | Design encryption at rest and in transit | 2 | Security Architect, SRE | R: Security Architect; A: PM; C: SRE |
| 1.2.4.5 | API Security | Design API authentication, rate limiting, CORS | 2 | Security Architect, Lead Dev | R: Security Architect; A: Lead Dev; C: Integration Spec |
| 1.2.4.6 | Security Monitoring | Design security logging and alerting | 2 | Security Architect, SRE | R: SRE; A: Security Architect; C: PM |
| 1.2.4.7 | Compliance Review | Review against ISO 27001, Australian Privacy Act | 1 | Security Architect | R: Security Architect; A: PM; I: Legal |
| 1.2.4.8 | Security Sign-Off | Security architecture review and approval | 1 | Security Architect, PM | R: Security Architect; A: Sponsor; C: PM |

**Acceptance Criteria:**
- Security architecture approved
- Authentication flows documented
- RBAC model defined with 5+ roles
- Compliance requirements addressed
- Security sign-off obtained

**Phase 2 Total:** 80 person-days | $160,000

---

## 5. Phase 3: Build & Configure (1.3)

### 5.1 WBS 1.3.1: CMS Configuration

**Duration:** 10 days | **Effort:** 80 person-days | **Cost:** $160,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.3.1.1 | Contentful Space Setup | Create dev, staging, production spaces | 2 | Lead Dev, CMS Developer | R: CMS Developer; A: Lead Dev; C: PM |
| 1.3.1.2 | Content Type Implementation | Implement 15-20 content types in Contentful | 15 | CMS Developer, Content Architect | R: CMS Developer; A: Lead Dev; C: Content Architect |
| 1.3.1.3 | Field Validations | Configure field-level validations and constraints | 5 | CMS Developer | R: CMS Developer; A: Lead Dev; C: QA |
| 1.3.1.4 | References & Relationships | Configure content relationships and references | 5 | CMS Developer | R: CMS Developer; A: Content Architect; C: Lead Dev |
| 1.3.1.5 | Localization Setup | Configure locales and translation workflows | 3 | CMS Developer | R: CMS Developer; A: Content Architect; C: Content Lead |
| 1.3.1.6 | Media Library Setup | Configure asset management, image settings | 4 | CMS Developer | R: CMS Developer; A: Lead Dev; C: Content Lead |
| 1.3.1.7 | Workflow Configuration | Setup editorial workflows (draft/review/publish) | 5 | CMS Developer, Content Lead | R: CMS Developer; A: Content Lead; C: PM |
| 1.3.1.8 | User Roles & Permissions | Configure 5+ roles with appropriate permissions | 4 | CMS Developer, Security | R: CMS Developer; A: Security Architect; C: Content Lead |
| 1.3.1.9 | Webhooks Configuration | Setup webhooks for build triggers, notifications | 3 | CMS Developer, Backend Dev | R: CMS Developer; A: Lead Dev; C: DevOps |
| 1.3.1.10 | Extensions & Plugins | Configure Contentful UI extensions as needed | 4 | CMS Developer | R: CMS Developer; A: Lead Dev; C: Content Lead |
| 1.3.1.11 | Preview Environment | Setup preview mode for content editors | 3 | CMS Developer, Frontend Dev | R: CMS Developer; A: Lead Dev; C: Content Lead |
| 1.3.1.12 | CMS Testing | Test all configurations, workflows, permissions | 5 | QA, CMS Developer | R: QA; A: QA Lead; C: CMS Developer |
| 1.3.1.13 | Content Editor Training Prep | Prepare training materials for editors | 3 | Content Lead, Training Specialist | R: Training Specialist; A: Content Lead; C: PM |
| 1.3.1.14 | CMS Documentation | Document CMS configuration and guidelines | 4 | Tech Writer, CMS Developer | R: Tech Writer; A: PM; C: CMS Developer |
| 1.3.1.15 | Editor Onboarding | Initial training session for Sydney Metro editors | 3 | Training Specialist, Content Lead | R: Training Specialist; A: PM; C: Content Lead |
| 1.3.1.16 | CMS Configuration Review | Review and sign-off on CMS setup | 2 | PM, Lead Dev, Content Lead | R: Lead Dev; A: PM; C: Sponsor |

**Acceptance Criteria:**
- All content types deployed to production
- Workflows operational with 3+ states
- 5+ user roles configured
- Preview mode functional
- Content editors trained (minimum 5 users)

---

### 5.2 WBS 1.3.2: Frontend Development

**Duration:** 15 days | **Effort:** 120 person-days | **Cost:** $240,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.3.2.1 | Next.js Project Setup | Initialize Next.js 14+ with TypeScript | 3 | Frontend Lead | R: Frontend Lead; A: Lead Dev; C: Team |
| 1.3.2.2 | Design System Integration | Integrate Sydney Metro design system/tokens | 8 | Frontend Dev 1, Designer | R: Frontend Dev 1; A: Frontend Lead; C: Designer |
| 1.3.2.3 | Component Library | Build reusable React components (20-30 components) | 20 | Frontend Dev 1, Frontend Dev 2 | R: Frontend Devs; A: Frontend Lead; C: Accessibility SME |
| 1.3.2.4 | Accessibility Implementation | WCAG 2.1 AA compliance in all components | 10 | Frontend Dev 1, Accessibility SME | R: Accessibility SME; A: Frontend Lead; C: QA |
| 1.3.2.5 | Responsive Design | Mobile-first responsive implementation | 8 | Frontend Dev 2 | R: Frontend Dev 2; A: Frontend Lead; C: Designer |
| 1.3.2.6 | Page Templates | Build 10-15 page templates (home, article, service) | 15 | Frontend Dev 1, Frontend Dev 2 | R: Frontend Devs; A: Frontend Lead; C: Content Architect |
| 1.3.2.7 | Dynamic Routing | Implement Next.js dynamic routes and slug handling | 5 | Frontend Lead | R: Frontend Lead; A: Lead Dev; C: Frontend Devs |
| 1.3.2.8 | Static Generation | Configure ISR (Incremental Static Regeneration) | 4 | Frontend Lead | R: Frontend Lead; A: Lead Dev; C: DevOps |
| 1.3.2.9 | Error Handling | Implement error boundaries, 404/500 pages | 3 | Frontend Dev 2 | R: Frontend Dev 2; A: Frontend Lead; C: QA |
| 1.3.2.10 | Performance Optimization | Implement lazy loading, code splitting, optimization | 6 | Frontend Lead, Frontend Dev 1 | R: Frontend Lead; A: Lead Dev; C: SRE |
| 1.3.2.11 | SEO Implementation | Meta tags, Open Graph, JSON-LD structured data | 5 | Frontend Dev 2, SEO Specialist | R: SEO Specialist; A: Frontend Lead; C: Marketing |
| 1.3.2.12 | Analytics Integration | Google Analytics 4, Tag Manager integration | 3 | Frontend Dev 2 | R: Frontend Dev 2; A: Frontend Lead; C: Marketing |
| 1.3.2.13 | Forms & Interactions | Build contact forms, search, interactive elements | 8 | Frontend Dev 1, Frontend Dev 2 | R: Frontend Devs; A: Frontend Lead; C: BA |
| 1.3.2.14 | Loading States | Implement skeletons, spinners, loading indicators | 3 | Frontend Dev 2 | R: Frontend Dev 2; A: Frontend Lead; C: Designer |
| 1.3.2.15 | Browser Testing | Cross-browser testing (Chrome, Firefox, Safari, Edge) | 5 | QA, Frontend Devs | R: QA; A: QA Lead; C: Frontend Lead |
| 1.3.2.16 | Unit & Integration Tests | Jest/React Testing Library tests (70%+ coverage) | 10 | Frontend Dev 1, QA Automation | R: Frontend Devs; A: QA Lead; C: Frontend Lead |
| 1.3.2.17 | Frontend Documentation | Component documentation, Storybook setup | 4 | Frontend Dev 1, Tech Writer | R: Frontend Dev 1; A: Frontend Lead; C: Tech Writer |

**Acceptance Criteria:**
- 20+ reusable components built
- 10+ page templates functional
- WCAG 2.1 AA compliance verified
- 70%+ code coverage
- Performance budget met (Core Web Vitals)

---

### 5.3 WBS 1.3.3: API Development

**Duration:** 10 days | **Effort:** 50 person-days | **Cost:** $100,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.3.3.1 | GraphQL Schema Design | Design GraphQL schema for Contentful queries | 3 | Backend Dev, Lead Dev | R: Backend Dev; A: Lead Dev; C: Content Architect |
| 1.3.3.2 | Data Fetching Layer | Build data fetching utilities and hooks | 5 | Backend Dev, Frontend Lead | R: Backend Dev; A: Lead Dev; C: Frontend Lead |
| 1.3.3.3 | API Rate Limiting | Implement rate limiting and caching | 3 | Backend Dev | R: Backend Dev; A: Lead Dev; C: SRE |
| 1.3.3.4 | API Error Handling | Implement robust error handling and retries | 3 | Backend Dev | R: Backend Dev; A: Lead Dev; C: QA |
| 1.3.3.5 | Search API | Integrate search service (Algolia or similar) | 5 | Backend Dev, Search Specialist | R: Backend Dev; A: Lead Dev; C: Frontend Lead |
| 1.3.3.6 | External API Integration | Integrate Sydney Metro APIs (auth, data services) | 8 | Integration Specialist, Backend Dev | R: Integration Spec; A: Lead Dev; C: Security |
| 1.3.3.7 | API Security | Implement authentication, authorization, API keys | 5 | Backend Dev, Security Architect | R: Backend Dev; A: Security Architect; C: Lead Dev |
| 1.3.3.8 | API Monitoring | Setup API monitoring and logging | 3 | Backend Dev, SRE | R: SRE; A: Backend Dev; C: PM |
| 1.3.3.9 | API Documentation | Create API documentation (OpenAPI/Swagger) | 3 | Backend Dev, Tech Writer | R: Backend Dev; A: Lead Dev; C: Tech Writer |
| 1.3.3.10 | API Testing | Unit tests, integration tests for APIs | 5 | Backend Dev, QA Automation | R: Backend Dev; A: QA Lead; C: Lead Dev |
| 1.3.3.11 | API Performance Testing | Load testing APIs, optimize performance | 4 | Backend Dev, SRE | R: SRE; A: Backend Dev; C: QA Lead |
| 1.3.3.12 | API Review | Code review and security review | 3 | Lead Dev, Security Architect | R: Lead Dev; A: Security Architect; C: PM |

**Acceptance Criteria:**
- GraphQL queries operational for all content types
- Search functionality working
- API response time <200ms (p95)
- API documentation complete
- Security review passed

---

### 5.4 WBS 1.3.4: CI/CD Setup

**Duration:** 8 days | **Effort:** 30 person-days | **Cost:** $60,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.3.4.1 | Repository Setup | Setup Git repository, branching strategy | 2 | DevOps Engineer | R: DevOps Engineer; A: Lead Dev; C: Team |
| 1.3.4.2 | Build Pipeline | Configure build automation (GitHub Actions/Azure) | 4 | DevOps Engineer | R: DevOps Engineer; A: Lead Dev; C: PM |
| 1.3.4.3 | Testing Automation | Integrate automated tests in pipeline | 3 | QA Automation, DevOps Engineer | R: QA Automation; A: QA Lead; C: DevOps |
| 1.3.4.4 | Code Quality Gates | Setup linting, code scanning, quality gates | 2 | DevOps Engineer, Lead Dev | R: DevOps Engineer; A: Lead Dev; C: QA Lead |
| 1.3.4.5 | Deployment Automation | Configure automated deployment to Vercel | 3 | DevOps Engineer | R: DevOps Engineer; A: Lead Dev; C: SRE |
| 1.3.4.6 | Environment Management | Setup dev/staging/prod environments | 3 | DevOps Engineer, SRE | R: DevOps Engineer; A: SRE; C: Lead Dev |
| 1.3.4.7 | Preview Deployments | Configure preview URLs for pull requests | 2 | DevOps Engineer | R: DevOps Engineer; A: Lead Dev; C: Frontend Lead |
| 1.3.4.8 | Secrets Management | Configure secure secrets management | 2 | DevOps Engineer, Security | R: DevOps Engineer; A: Security Architect; C: Lead Dev |
| 1.3.4.9 | Rollback Procedures | Implement automated rollback capabilities | 2 | DevOps Engineer, SRE | R: DevOps Engineer; A: SRE; C: PM |
| 1.3.4.10 | Pipeline Monitoring | Setup pipeline monitoring and alerting | 2 | DevOps Engineer, SRE | R: SRE; A: DevOps Engineer; C: PM |
| 1.3.4.11 | CI/CD Documentation | Document pipeline processes and runbooks | 3 | DevOps Engineer, Tech Writer | R: DevOps Engineer; A: PM; C: Tech Writer |
| 1.3.4.12 | Pipeline Testing | Test all pipeline stages, verify automation | 2 | DevOps Engineer, QA | R: DevOps Engineer; A: Lead Dev; C: QA Lead |

**Acceptance Criteria:**
- CI/CD pipeline operational for all environments
- Automated deployments working
- Build time <10 minutes
- Rollback tested and operational
- Pipeline documentation complete

---

### 5.5 WBS 1.3.5: Infrastructure Setup

**Duration:** 7 days | **Effort:** 20 person-days | **Cost:** $40,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.3.5.1 | Vercel Configuration | Setup Vercel project, configure settings | 2 | SRE, DevOps Engineer | R: SRE; A: Lead Dev; C: PM |
| 1.3.5.2 | CDN Configuration | Configure CDN caching rules, edge functions | 3 | SRE | R: SRE; A: Lead Dev; C: DevOps |
| 1.3.5.3 | Domain & DNS Setup | Configure domain, DNS, SSL certificates | 2 | SRE, Sydney Metro IT | R: Sydney Metro IT; A: SRE; C: PM |
| 1.3.5.4 | Monitoring Setup | Setup DataDog/New Relic, configure dashboards | 3 | SRE | R: SRE; A: PM; C: DevOps |
| 1.3.5.5 | Logging Infrastructure | Configure centralized logging (CloudWatch/Splunk) | 2 | SRE | R: SRE; A: PM; C: DevOps |
| 1.3.5.6 | Error Tracking | Setup Sentry or similar error tracking | 2 | SRE, Frontend Lead | R: SRE; A: Frontend Lead; C: PM |
| 1.3.5.7 | Alerting Configuration | Configure alerts for critical issues | 2 | SRE | R: SRE; A: PM; C: Lead Dev |
| 1.3.5.8 | Backup & DR | Configure backup strategy and DR procedures | 2 | SRE | R: SRE; A: PM; C: Security |
| 1.3.5.9 | Infrastructure Documentation | Document infrastructure architecture and runbooks | 2 | SRE, Tech Writer | R: SRE; A: PM; C: Tech Writer |

**Acceptance Criteria:**
- Vercel infrastructure operational
- CDN cache hit ratio >80%
- Monitoring dashboards functional
- Alerting tested and operational
- Infrastructure documented

**Phase 3 Total:** 300 person-days | $600,000

---

## 6. Phase 4: Migration (1.4)

### 6.1 WBS 1.4.1: ETL Development

**Duration:** 5 days | **Effort:** 40 person-days | **Cost:** $80,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.4.1.1 | Legacy Export Scripts | Develop scripts to export data from legacy CMS | 8 | Migration Lead, Backend Dev | R: Migration Lead; A: Lead Dev; C: Sydney Metro IT |
| 1.4.1.2 | Data Transformation | Build transformation logic, field mapping | 10 | Migration Lead, Backend Dev | R: Migration Lead; A: Lead Dev; C: Content Architect |
| 1.4.1.3 | Contentful Import Scripts | Develop import scripts for Contentful API | 8 | Backend Dev, Migration Lead | R: Backend Dev; A: Migration Lead; C: Lead Dev |
| 1.4.1.4 | Asset Migration | Develop asset (images/docs) migration scripts | 5 | Migration Lead, Backend Dev | R: Migration Lead; A: Lead Dev; C: Content Lead |
| 1.4.1.5 | Batch Processing | Implement batch processing, error handling | 4 | Backend Dev | R: Backend Dev; A: Migration Lead; C: SRE |
| 1.4.1.6 | ETL Testing | Unit test ETL scripts, small-batch testing | 3 | QA, Migration Lead | R: QA; A: QA Lead; C: Migration Lead |
| 1.4.1.7 | ETL Documentation | Document ETL process, troubleshooting guide | 2 | Migration Lead, Tech Writer | R: Migration Lead; A: PM; C: Tech Writer |

**Acceptance Criteria:**
- ETL pipeline successfully tested with 100 items
- Error handling operational
- Asset migration tested
- ETL documentation complete

---

### 6.2 WBS 1.4.2: Content Migration

**Duration:** 10 days | **Effort:** 100 person-days | **Cost:** $200,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.4.2.1 | Migration Environment Prep | Prepare staging environment for migration | 3 | SRE, Migration Lead | R: SRE; A: Migration Lead; C: DevOps |
| 1.4.2.2 | Dry Run #1 | Execute full migration dry run to staging | 10 | Migration Lead, Backend Dev | R: Migration Lead; A: PM; C: All Leads |
| 1.4.2.3 | Data Validation | Validate migrated content, check integrity | 8 | QA, Content Lead | R: QA; A: QA Lead; C: Content Lead |
| 1.4.2.4 | Issue Analysis | Analyze migration issues, create fix list | 5 | Migration Lead, QA | R: Migration Lead; A: PM; C: QA Lead |
| 1.4.2.5 | ETL Fixes | Fix identified ETL issues | 8 | Migration Lead, Backend Dev | R: Migration Lead; A: Lead Dev; C: QA |
| 1.4.2.6 | Content Reconciliation | Reconcile content counts, missing items | 5 | Content Lead, Migration Lead | R: Content Lead; A: Migration Lead; C: Sydney Metro |
| 1.4.2.7 | Asset Validation | Validate all assets migrated correctly | 5 | QA, Content Lead | R: QA; A: Content Lead; C: Migration Lead |
| 1.4.2.8 | Relationship Validation | Verify all content relationships intact | 5 | QA, Content Architect | R: QA; A: Content Architect; C: Migration Lead |
| 1.4.2.9 | Dry Run #2 | Execute second dry run with fixes | 8 | Migration Lead, Backend Dev | R: Migration Lead; A: PM; C: All Leads |
| 1.4.2.10 | Final Validation | Final data integrity checks | 5 | QA, Migration Lead | R: QA; A: QA Lead; C: Migration Lead |
| 1.4.2.11 | Migration Report | Create comprehensive migration report | 3 | Migration Lead | R: Migration Lead; A: PM; C: Sponsor |
| 1.4.2.12 | Production Readiness | Prepare for production migration | 3 | Migration Lead, SRE | R: Migration Lead; A: PM; C: SRE |
| 1.4.2.13 | Content Freeze | Coordinate content freeze with Sydney Metro | 2 | PM, Content Lead | R: PM; A: Sponsor; C: Sydney Metro |
| 1.4.2.14 | Production Migration | Execute production migration | 10 | Migration Lead, All Team | R: Migration Lead; A: PM; C: All Leads |
| 1.4.2.15 | Post-Migration Validation | Validate production content | 5 | QA, Content Lead | R: QA; A: QA Lead; C: Migration Lead |
| 1.4.2.16 | Migration Closure | Migration sign-off, lessons learned | 2 | PM, Migration Lead | R: PM; A: Sponsor; C: All Leads |

**Acceptance Criteria:**
- 100% of content migrated successfully
- Data integrity >99.5%
- All assets migrated and validated
- Content relationships intact
- Migration report approved

---

### 6.3 WBS 1.4.3: Redirect Implementation

**Duration:** 5 days | **Effort:** 35 person-days | **Cost:** $70,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.4.3.1 | URL Analysis | Analyze legacy URL structure and patterns | 3 | SEO Specialist, Migration Lead | R: SEO Specialist; A: Lead Dev; C: Sydney Metro |
| 1.4.3.2 | Redirect Mapping | Create old URL → new URL mapping (1000s of URLs) | 8 | SEO Specialist, Migration Lead | R: SEO Specialist; A: Migration Lead; C: Content Lead |
| 1.4.3.3 | Redirect Rules | Develop redirect rules (pattern-based + specific) | 5 | Backend Dev, SEO Specialist | R: Backend Dev; A: Lead Dev; C: SEO Specialist |
| 1.4.3.4 | Edge Function Development | Implement redirects as Vercel edge functions | 4 | Backend Dev | R: Backend Dev; A: Lead Dev; C: DevOps |
| 1.4.3.5 | Redirect Testing | Test redirect rules (automated + manual) | 5 | QA, SEO Specialist | R: QA; A: QA Lead; C: SEO Specialist |
| 1.4.3.6 | 404 Page | Implement custom 404 page with search | 2 | Frontend Dev, SEO Specialist | R: Frontend Dev; A: Frontend Lead; C: SEO Specialist |
| 1.4.3.7 | Redirect Monitoring | Setup redirect monitoring and analytics | 2 | SRE, SEO Specialist | R: SRE; A: SEO Specialist; C: PM |
| 1.4.3.8 | Redirect Documentation | Document redirect strategy and maintenance | 2 | SEO Specialist, Tech Writer | R: SEO Specialist; A: PM; C: Tech Writer |
| 1.4.3.9 | SEO Validation | Validate SEO meta-data, sitemaps, robots.txt | 3 | SEO Specialist | R: SEO Specialist; A: Frontend Lead; C: Marketing |
| 1.4.3.10 | Redirect Sign-Off | Redirect strategy approved | 1 | SEO Specialist, PM | R: PM; A: Sponsor; C: SEO Specialist |

**Acceptance Criteria:**
- 100% of key URLs have redirects
- Redirect testing 95%+ success rate
- 404 page implemented
- SEO validation passed
- Redirect strategy approved

---

### 6.4 WBS 1.4.4: Data Validation

**Duration:** 4 days | **Effort:** 25 person-days | **Cost:** $50,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.4.4.1 | Validation Test Plan | Create comprehensive validation test plan | 2 | QA Lead | R: QA Lead; A: PM; C: Migration Lead |
| 1.4.4.2 | Automated Validation | Run automated validation scripts | 3 | QA, Migration Lead | R: QA; A: QA Lead; C: Migration Lead |
| 1.4.4.3 | Content Sampling | Manual validation of content sample (5%) | 5 | QA, Content Lead | R: QA; A: QA Lead; C: Content Lead |
| 1.4.4.4 | Link Checking | Automated link checking (internal/external) | 3 | QA, SEO Specialist | R: QA; A: QA Lead; C: SEO Specialist |
| 1.4.4.5 | Image Validation | Validate all images load correctly | 3 | QA | R: QA; A: QA Lead; C: Content Lead |
| 1.4.4.6 | Metadata Validation | Validate SEO metadata, Open Graph tags | 2 | QA, SEO Specialist | R: SEO Specialist; A: QA Lead; C: Frontend Lead |
| 1.4.4.7 | Search Testing | Test search functionality with migrated content | 2 | QA | R: QA; A: QA Lead; C: Backend Dev |
| 1.4.4.8 | Defect Management | Log and triage validation defects | 3 | QA Lead | R: QA Lead; A: PM; C: Migration Lead |
| 1.4.4.9 | Validation Report | Create validation report with findings | 2 | QA Lead | R: QA Lead; A: PM; C: Sponsor |

**Acceptance Criteria:**
- Validation test plan approved
- <1% critical defects
- All images validated
- Link checking 98%+ success
- Validation report approved

**Phase 4 Total:** 200 person-days | $400,000

---

## 7. Phase 5: Testing & Hardening (1.5)

### 7.1 WBS 1.5.1: Performance Testing

**Duration:** 5 days | **Effort:** 40 person-days | **Cost:** $80,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.5.1.1 | Performance Test Plan | Create performance test plan with scenarios | 2 | QA Lead, SRE | R: QA Lead; A: PM; C: SRE |
| 1.5.1.2 | Load Test Scripts | Develop JMeter/k6 load test scripts | 5 | QA, SRE | R: QA; A: QA Lead; C: SRE |
| 1.5.1.3 | Baseline Metrics | Capture baseline performance metrics | 2 | SRE | R: SRE; A: QA Lead; C: PM |
| 1.5.1.4 | Load Testing | Execute load tests (10k, 50k, 100k users) | 5 | SRE, QA | R: SRE; A: QA Lead; C: PM |
| 1.5.1.5 | Stress Testing | Execute stress tests to find breaking point | 3 | SRE, QA | R: SRE; A: QA Lead; C: Lead Dev |
| 1.5.1.6 | Endurance Testing | Execute 24-hour endurance test | 3 | SRE, QA | R: SRE; A: QA Lead; C: PM |
| 1.5.1.7 | Performance Analysis | Analyze results, identify bottlenecks | 4 | SRE, Lead Dev | R: SRE; A: Lead Dev; C: QA Lead |
| 1.5.1.8 | CDN Performance | Validate CDN performance, cache hit ratio | 2 | SRE | R: SRE; A: Lead Dev; C: PM |
| 1.5.1.9 | Core Web Vitals | Validate Lighthouse scores, Core Web Vitals | 3 | Frontend Lead, SRE | R: Frontend Lead; A: SRE; C: QA |
| 1.5.1.10 | Performance Optimization | Optimize based on test findings | 5 | Lead Dev, Frontend Lead, SRE | R: Dev Leads; A: PM; C: QA Lead |
| 1.5.1.11 | Re-testing | Re-run tests to validate optimizations | 3 | SRE, QA | R: SRE; A: QA Lead; C: PM |
| 1.5.1.12 | Performance Report | Create performance test report | 3 | QA Lead, SRE | R: QA Lead; A: PM; C: Sponsor |

**Acceptance Criteria:**
- Page load time <2 seconds (p95)
- 100k concurrent users supported
- Core Web Vitals: LCP <2.5s, FID <100ms, CLS <0.1
- CDN cache hit ratio >80%
- Performance report approved

---

### 7.2 WBS 1.5.2: Accessibility Testing

**Duration:** 5 days | **Effort:** 35 person-days | **Cost:** $70,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.5.2.1 | Accessibility Test Plan | Create WCAG 2.1 AA test plan | 2 | Accessibility SME, QA Lead | R: Accessibility SME; A: QA Lead; C: PM |
| 1.5.2.2 | Automated Testing | Run axe, WAVE, Lighthouse accessibility tests | 3 | QA, Accessibility SME | R: QA; A: Accessibility SME; C: Frontend Lead |
| 1.5.2.3 | Screen Reader Testing | Test with JAWS, NVDA, VoiceOver | 5 | Accessibility SME | R: Accessibility SME; A: QA Lead; C: Frontend Lead |
| 1.5.2.4 | Keyboard Navigation | Test keyboard-only navigation | 3 | Accessibility SME, QA | R: Accessibility SME; A: QA Lead; C: Frontend Lead |
| 1.5.2.5 | Color Contrast | Validate color contrast ratios (4.5:1 minimum) | 2 | Accessibility SME | R: Accessibility SME; A: Frontend Lead; C: Designer |
| 1.5.2.6 | Focus Management | Test focus indicators, focus traps | 2 | Accessibility SME, QA | R: Accessibility SME; A: QA Lead; C: Frontend Lead |
| 1.5.2.7 | ARIA Implementation | Validate ARIA labels, roles, states | 3 | Accessibility SME | R: Accessibility SME; A: Frontend Lead; C: QA |
| 1.5.2.8 | Form Accessibility | Test form labels, error messages, validation | 2 | Accessibility SME, QA | R: Accessibility SME; A: QA Lead; C: Frontend Lead |
| 1.5.2.9 | Media Accessibility | Validate captions, transcripts, alt text | 2 | Accessibility SME, Content Lead | R: Accessibility SME; A: Content Lead; C: QA |
| 1.5.2.10 | Accessibility Fixes | Fix identified accessibility issues | 6 | Frontend Devs, Accessibility SME | R: Frontend Devs; A: Frontend Lead; C: Accessibility SME |
| 1.5.2.11 | Re-testing | Re-test after fixes | 3 | Accessibility SME, QA | R: Accessibility SME; A: QA Lead; C: Frontend Lead |
| 1.5.2.12 | Accessibility Report | Create WCAG 2.1 AA compliance report | 2 | Accessibility SME | R: Accessibility SME; A: PM; C: Sponsor |

**Acceptance Criteria:**
- WCAG 2.1 AA compliant (100% Level A, 95%+ Level AA)
- Automated testing: 0 critical issues
- Screen reader testing passed
- Accessibility report approved

---

### 7.3 WBS 1.5.3: Security Testing

**Duration:** 5 days | **Effort:** 35 person-days | **Cost:** $70,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.5.3.1 | Security Test Plan | Create security test plan (OWASP Top 10) | 2 | Security Architect, QA Lead | R: Security Architect; A: PM; C: QA Lead |
| 1.5.3.2 | Vulnerability Scanning | Run automated vulnerability scans | 3 | Security Architect, QA | R: Security Architect; A: PM; C: Lead Dev |
| 1.5.3.3 | Penetration Testing | Execute penetration tests | 8 | Security Specialist | R: Security Specialist; A: Security Architect; C: PM |
| 1.5.3.4 | API Security Testing | Test API authentication, authorization, rate limiting | 4 | Security Architect, QA | R: Security Architect; A: Lead Dev; C: QA Lead |
| 1.5.3.5 | XSS Testing | Cross-site scripting vulnerability testing | 2 | Security Architect, QA | R: Security Architect; A: Lead Dev; C: QA |
| 1.5.3.6 | CSRF Testing | Cross-site request forgery testing | 2 | Security Architect, QA | R: Security Architect; A: Lead Dev; C: QA |
| 1.5.3.7 | SQL Injection Testing | Test for SQL injection vulnerabilities | 2 | Security Architect, QA | R: Security Architect; A: Backend Dev; C: QA |
| 1.5.3.8 | Authentication Testing | Test SSO, session management, password policies | 3 | Security Architect | R: Security Architect; A: Lead Dev; C: QA |
| 1.5.3.9 | Security Fixes | Fix identified security vulnerabilities | 5 | Dev Team, Security Architect | R: Dev Team; A: Security Architect; C: PM |
| 1.5.3.10 | Re-testing | Re-test after security fixes | 2 | Security Architect, QA | R: Security Architect; A: PM; C: QA Lead |
| 1.5.3.11 | Security Report | Create penetration test report | 2 | Security Architect | R: Security Architect; A: PM; C: Sponsor |

**Acceptance Criteria:**
- 0 high/critical security vulnerabilities
- OWASP Top 10 validated
- Penetration test report approved
- Security sign-off obtained

---

### 7.4 WBS 1.5.4: User Acceptance Testing

**Duration:** 5 days | **Effort:** 40 person-days | **Cost:** $80,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.5.4.1 | UAT Test Plan | Create UAT test plan and test cases | 3 | QA Lead, BA | R: QA Lead; A: PM; C: BA |
| 1.5.4.2 | UAT Environment Prep | Prepare UAT environment with production data | 2 | SRE, QA | R: SRE; A: QA Lead; C: PM |
| 1.5.4.3 | Tester Training | Train Sydney Metro UAT testers | 2 | QA Lead, Training Specialist | R: Training Specialist; A: QA Lead; C: PM |
| 1.5.4.4 | UAT Execution - Day 1 | Content editors test CMS workflows | 5 | Sydney Metro Testers, QA | R: Sydney Metro; A: QA Lead; C: Content Lead |
| 1.5.4.5 | UAT Execution - Day 2 | Stakeholders test frontend functionality | 5 | Sydney Metro Testers, QA | R: Sydney Metro; A: QA Lead; C: PM |
| 1.5.4.6 | UAT Execution - Day 3 | End-to-end workflow testing | 5 | Sydney Metro Testers, QA | R: Sydney Metro; A: QA Lead; C: PM |
| 1.5.4.7 | Defect Triage | Daily defect triage meetings | 3 | QA Lead, PM | R: QA Lead; A: PM; C: Leads |
| 1.5.4.8 | Bug Fixing | Fix high/critical UAT defects | 8 | Dev Team | R: Dev Team; A: Lead Dev; C: QA Lead |
| 1.5.4.9 | Regression Testing | Regression testing after bug fixes | 3 | QA | R: QA; A: QA Lead; C: PM |
| 1.5.4.10 | UAT Sign-Off | UAT completion and sign-off | 2 | PM, QA Lead | R: PM; A: Sponsor; C: All Leads |
| 1.5.4.11 | UAT Report | Create UAT summary report | 2 | QA Lead | R: QA Lead; A: PM; C: Sponsor |

**Acceptance Criteria:**
- 95%+ test cases passed
- 0 high/critical defects open
- UAT sign-off obtained from Sydney Metro
- UAT report approved

**Phase 5 Total:** 150 person-days | $300,000

---

## 8. Phase 6: Cutover & Handover (1.6)

### 8.1 WBS 1.6.1: Production Deployment

**Duration:** 3 days | **Effort:** 30 person-days | **Cost:** $60,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.6.1.1 | Go/No-Go Checklist | Complete go-live readiness checklist | 2 | PM, All Leads | R: PM; A: Sponsor; C: All Leads |
| 1.6.1.2 | Go/No-Go Meeting | Conduct go/no-go decision meeting | 1 | PM, Stakeholders | R: PM; A: Sponsor; C: All Leads |
| 1.6.1.3 | Content Freeze | Initiate content freeze in legacy system | 1 | PM, Content Lead | R: Content Lead; A: PM; C: Sydney Metro |
| 1.6.1.4 | Final Backup | Create final backup of legacy system | 2 | SRE | R: SRE; A: PM; C: Sydney Metro IT |
| 1.6.1.5 | Production Migration | Execute production content migration | 6 | Migration Lead, All Team | R: Migration Lead; A: PM; C: All Leads |
| 1.6.1.6 | DNS Cutover | Switch DNS to new system | 2 | SRE, Sydney Metro IT | R: Sydney Metro IT; A: SRE; C: PM |
| 1.6.1.7 | Go-Live Monitoring | Monitor system for first 4 hours | 4 | SRE, All Team | R: SRE; A: PM; C: All Leads |
| 1.6.1.8 | Smoke Testing | Execute smoke tests post-deployment | 2 | QA, All Leads | R: QA; A: QA Lead; C: PM |
| 1.6.1.9 | Issue Triage | Triage and resolve go-live issues | 4 | PM, Dev Team | R: Dev Team; A: PM; C: Leads |
| 1.6.1.10 | Go-Live Communication | Communicate go-live status to stakeholders | 1 | PM | R: PM; A: Sponsor; I: Stakeholders |
| 1.6.1.11 | Rollback Decision | Make rollback decision if critical issues | 1 | PM, Sponsor | R: PM; A: Sponsor; C: All Leads |
| 1.6.1.12 | Go-Live Report | Create go-live status report | 2 | PM | R: PM; A: Sponsor; C: All Leads |
| 1.6.1.13 | Post-Go-Live Review | Conduct post-go-live review meeting | 2 | PM, All Leads | R: PM; A: Sponsor; C: Team |

**Acceptance Criteria:**
- Production system live and stable
- <2% error rate in first 24 hours
- DNS propagation complete
- Smoke tests passed
- Go-live report approved

---

### 8.2 WBS 1.6.2: Training

**Duration:** 2 days | **Effort:** 10 person-days | **Cost:** $20,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.6.2.1 | Training Materials | Finalize training materials and guides | 2 | Training Specialist, Content Lead | R: Training Specialist; A: PM; C: Content Lead |
| 1.6.2.2 | Content Editor Training | Conduct 4-hour content editor training | 2 | Training Specialist, Content Lead | R: Training Specialist; A: PM; C: Sydney Metro |
| 1.6.2.3 | Admin Training | Conduct 2-hour admin training | 1 | Training Specialist, Lead Dev | R: Training Specialist; A: PM; C: Sydney Metro IT |
| 1.6.2.4 | Developer Training | Conduct 2-hour developer handover training | 1 | Lead Dev, Solution Architect | R: Lead Dev; A: PM; C: Sydney Metro IT |
| 1.6.2.5 | Training Videos | Create screen recording training videos | 2 | Training Specialist | R: Training Specialist; A: PM; C: Content Lead |
| 1.6.2.6 | Quick Reference Guides | Create quick reference cards | 1 | Training Specialist, Tech Writer | R: Training Specialist; A: PM; C: Content Lead |
| 1.6.2.7 | Training Assessment | Assess training effectiveness, feedback | 1 | Training Specialist | R: Training Specialist; A: PM; C: Content Lead |

**Acceptance Criteria:**
- 3 training sessions delivered
- Training materials approved
- 90%+ attendee satisfaction
- Training videos published

---

### 8.3 WBS 1.6.3: Documentation

**Duration:** 5 days | **Effort:** 15 person-days | **Cost:** $30,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.6.3.1 | Support Runbooks | Create support runbooks for common issues | 3 | SRE, Tech Writer | R: SRE; A: PM; C: Lead Dev |
| 1.6.3.2 | Operational Procedures | Document operational procedures (backup, monitoring) | 2 | SRE, Tech Writer | R: SRE; A: PM; C: PM |
| 1.6.3.3 | Architecture Documentation | Finalize architecture documentation | 2 | Solution Architect, Tech Writer | R: Solution Architect; A: PM; C: Tech Writer |
| 1.6.3.4 | Content Guidelines | Create content authoring guidelines | 2 | Content Lead, Tech Writer | R: Content Lead; A: PM; C: Sydney Metro |
| 1.6.3.5 | API Documentation | Finalize API documentation | 2 | Backend Dev, Tech Writer | R: Backend Dev; A: Lead Dev; C: Tech Writer |
| 1.6.3.6 | Troubleshooting Guide | Create troubleshooting guide | 2 | SRE, Tech Writer | R: SRE; A: PM; C: Support Team |
| 1.6.3.7 | Documentation Portal | Setup documentation portal/wiki | 1 | Tech Writer, PM | R: Tech Writer; A: PM; C: Sydney Metro |
| 1.6.3.8 | Documentation Review | Review all documentation for accuracy | 1 | PM, All Leads | R: All Leads; A: PM; C: Tech Writer |

**Acceptance Criteria:**
- 5+ runbooks created
- Architecture documentation complete
- Documentation portal live
- Documentation review passed

---

### 8.4 WBS 1.6.4: Knowledge Transfer

**Duration:** 3 days | **Effort:** 5 person-days | **Cost:** $10,000

#### Work Packages & Tasks

| WBS Code | Task | Description | Effort (PD) | Owner | RACI |
|----------|------|-------------|-------------|-------|------|
| 1.6.4.1 | Handover Sessions | Conduct handover sessions with Sydney Metro IT | 2 | All Leads | R: All Leads; A: PM; C: Sydney Metro IT |
| 1.6.4.2 | Support Transition | Transition to BAU support team | 1 | PM, SRE | R: PM; A: Sponsor; C: Support Team |
| 1.6.4.3 | Lessons Learned | Conduct lessons learned workshop | 1 | PM, All Leads | R: PM; A: Sponsor; C: Team |
| 1.6.4.4 | Project Closure | Complete project closure activities | 1 | PM | R: PM; A: Sponsor; C: Finance |

**Acceptance Criteria:**
- Handover sessions completed
- Support team transitioned
- Lessons learned documented
- Project closure approved

**Phase 6 Total:** 60 person-days | $120,000

---

## 9. Project Management (1.7) - Throughout Project

### 9.1 WBS 1.7.1: Planning & Control

**Effort:** 30 person-days | **Cost:** $60,000

| WBS Code | Task | Description | Effort (PD) | Owner |
|----------|------|-------------|-------------|-------|
| 1.7.1.1 | Project Planning | Maintain project plan, schedule updates | 10 | PM |
| 1.7.1.2 | Status Reporting | Weekly status reports | 10 | PM |
| 1.7.1.3 | Budget Management | Track budget, cost forecasting | 5 | PM, Finance |
| 1.7.1.4 | Change Management | Process change requests | 5 | PM |

---

### 9.2 WBS 1.7.2: Risk Management

**Effort:** 15 person-days | **Cost:** $30,000

| WBS Code | Task | Description | Effort (PD) | Owner |
|----------|------|-------------|-------------|-------|
| 1.7.2.1 | Risk Monitoring | Ongoing risk monitoring and updates | 10 | PM |
| 1.7.2.2 | Risk Reviews | Bi-weekly risk review meetings | 5 | PM, Leads |

---

### 9.3 WBS 1.7.3: Quality Assurance

**Effort:** 30 person-days | **Cost:** $60,000

| WBS Code | Task | Description | Effort (PD) | Owner |
|----------|------|-------------|-------------|-------|
| 1.7.3.1 | Quality Planning | Quality management plan, standards | 5 | QA Lead |
| 1.7.3.2 | Quality Reviews | Phase gate quality reviews | 10 | QA Lead |
| 1.7.3.3 | Quality Audits | Periodic quality audits | 10 | QA Lead |
| 1.7.3.4 | Quality Reporting | Quality metrics and reports | 5 | QA Lead |

---

### 9.4 WBS 1.7.4: Stakeholder Management

**Effort:** 25 person-days | **Cost:** $50,000

| WBS Code | Task | Description | Effort (PD) | Owner |
|----------|------|-------------|-------------|-------|
| 1.7.4.1 | Stakeholder Engagement | Regular stakeholder meetings | 15 | PM |
| 1.7.4.2 | Stakeholder Communications | Communication as per plan | 5 | PM |
| 1.7.4.3 | Stakeholder Satisfaction | Satisfaction surveys, feedback | 5 | PM |

---

## 10. RACI Matrix Summary

| Activity | PM | Arch | Lead Dev | Content | SRE | QA | Security | Sponsor |
|----------|----|----|----------|---------|-----|----|---------:|---------|
| Discovery | R | C | C | C | C | C | C | A |
| Architecture | A | R | C | C | C | C | C | I |
| CMS Config | A | C | R | C | C | C | C | I |
| Frontend Dev | A | C | R | C | C | C | C | I |
| Migration | R | C | C | R | C | C | C | A |
| Testing | A | C | C | C | C | R | C | I |
| Go-Live | R | C | C | C | R | C | C | A |

**Legend:**
- R = Responsible (does the work)
- A = Accountable (final authority)
- C = Consulted (provides input)
- I = Informed (kept updated)

---

## 11. Cost Breakdown by Resource Type

| Resource Type | Rate (per day) | Total Days | Total Cost | % of Total |
|---------------|----------------|------------|------------|------------|
| Project Manager | $2,500 | 90 | $225,000 | 11.6% |
| Solution Architect | $3,000 | 60 | $180,000 | 9.3% |
| Lead Developer | $2,500 | 80 | $200,000 | 10.3% |
| Developers (3) | $2,000 | 360 | $720,000 | 37.1% |
| Content Lead | $2,000 | 60 | $120,000 | 6.2% |
| SRE/DevOps (2) | $2,200 | 110 | $242,000 | 12.5% |
| QA Team (2) | $1,800 | 100 | $180,000 | 9.3% |
| Security Architect | $2,500 | 30 | $75,000 | 3.9% |
| Specialists (SEO, Accessibility, etc.) | $2,000 | 40 | $80,000 | 4.1% |
| **Total** | | **970** | **$2,022,000** | **100%** |

*Note: Small variance from $1,940,000 blended rate due to differential rates*

---

## 12. Assumptions for Effort Estimates

1. **Team Experience:**
   - Senior team members with Contentful and Next.js experience
   - Average 5+ years experience per team member
   - Minimal learning curve for technology stack

2. **Availability:**
   - 8-12 FTEs available throughout project
   - <10% unplanned absence rate
   - Stakeholders available within 2 business days

3. **Scope:**
   - 15-20 content types as defined
   - <10,000 total content items to migrate
   - No major scope changes post-architecture phase

4. **Technical:**
   - API access to legacy system granted by Day 2
   - No major technical blockers in legacy export
   - Contentful and Vercel services operational with <99.9% uptime

5. **Dependencies:**
   - Sydney Metro IT team responsive for integrations
   - DNS and infrastructure changes completed within agreed timelines
   - Third-party services (Algolia, monitoring) available

---

## 13. Key Metrics & KPIs

| Metric | Target | Measurement |
|--------|--------|-------------|
| Schedule Variance | ±5 days | Weekly tracking |
| Budget Variance | ±5% | Bi-weekly tracking |
| Defect Density | <0.5 defects per work package | Per phase |
| Test Coverage | >70% code coverage | Continuous |
| Migration Accuracy | >99.5% data integrity | Post-migration validation |
| Accessibility Compliance | WCAG 2.1 AA (95%+) | Phase 5 testing |
| Performance | Page load <2s (p95) | Phase 5 testing |
| Availability | >99.9% uptime | Post go-live |

---

## 14. Change Control Thresholds

| Impact | Schedule Impact | Budget Impact | Approval Required |
|--------|----------------|---------------|-------------------|
| Minor | <2 days | <2% | PM |
| Moderate | 2-5 days | 2-5% | PM + Sponsor |
| Major | >5 days | >5% | Change Control Board |
| Critical | >10 days | >10% | Executive Steering Committee |

---

## 15. Glossary

- **WBS:** Work Breakdown Structure
- **PM:** Project Manager
- **Arch:** Solution Architect
- **Dev:** Developer
- **SRE:** Site Reliability Engineer
- **QA:** Quality Assurance
- **SME:** Subject Matter Expert
- **UAT:** User Acceptance Testing
- **ETL:** Extract, Transform, Load
- **NFR:** Non-Functional Requirements
- **RACI:** Responsible, Accountable, Consulted, Informed
- **PD:** Person-Day

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

*End of Work Breakdown Structure Document*
