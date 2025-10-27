# Transition and Handover Plan
## Sydney Metro CMS Modernization Project

**Document Version:** 1.0
**Date:** October 2025
**Prepared by:** HCL Technologies
**Classification:** Commercial in Confidence

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | October 2025 | HCL Transition Team | Initial version |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Transition Approach and Phases](#2-transition-approach-and-phases)
3. [Knowledge Transfer Strategy](#3-knowledge-transfer-strategy)
4. [Training Program](#4-training-program)
5. [Documentation Deliverables](#5-documentation-deliverables)
6. [Hypercare Support](#6-hypercare-support)
7. [Warranty Period](#7-warranty-period)
8. [BAU Handover Process](#8-bau-handover-process)

---

## 1. Executive Summary

This Transition and Handover Plan outlines the comprehensive approach for transitioning the Sydney Metro CMS from Sitecore to Strapi, and successfully handing over the system to Sydney Metro's Business-as-Usual (BAU) operations team. The plan ensures a smooth, low-risk transition with minimal disruption to business operations and complete knowledge transfer to all stakeholders.

### 1.1 Transition Objectives

1. **Seamless Migration:** Migrate 5000+ pages from Sitecore to Strapi with zero data loss
2. **User Readiness:** Ensure all users are trained and confident using the new system
3. **Operational Continuity:** Maintain business operations throughout the transition
4. **Knowledge Transfer:** Transfer comprehensive system knowledge to Sydney Metro teams
5. **Support Continuity:** Provide graduated support from intensive hypercare to BAU warranty
6. **Documentation:** Deliver complete, accurate, and usable documentation

### 1.2 Transition Principles

- **Risk Mitigation:** Proactive identification and mitigation of transition risks
- **User-Centric:** Focus on user adoption and satisfaction
- **Phased Approach:** Gradual transition with validation at each stage
- **Two-Way Communication:** Continuous feedback loops with Sydney Metro
- **Operational Resilience:** Maintain service availability throughout transition
- **Lessons Learned:** Capture and apply insights throughout the process

### 1.3 Transition Timeline Overview

```
┌──────────────────────────────────────────────────────────────────────┐
│                    Transition Timeline (Weeks 10-16)                 │
├──────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Week 10-11: Pre-Production Transition                              │
│  ├─ UAT and final testing                                          │
│  ├─ Training delivery (all user groups)                            │
│  ├─ Documentation finalization                                      │
│  └─ Go-live readiness review                                        │
│                                                                      │
│  Week 12: Production Cutover                                        │
│  ├─ Final data migration                                            │
│  ├─ Production deployment                                           │
│  ├─ Smoke testing                                                   │
│  └─ Go-live announcement                                            │
│                                                                      │
│  Week 13-16: Hypercare Period (4 weeks)                            │
│  ├─ Intensive support (24/7 coverage)                              │
│  ├─ Issue resolution and optimization                               │
│  ├─ User support and coaching                                       │
│  └─ Performance monitoring                                          │
│                                                                      │
│  Month 5-16: Warranty Period (12 months)                           │
│  ├─ Defect resolution (per SLA)                                    │
│  ├─ Monthly health checks                                           │
│  ├─ Quarterly system reviews                                        │
│  └─ Knowledge base updates                                          │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

### 1.4 Key Stakeholders

| Stakeholder Group | Role in Transition | Primary Contact |
|-------------------|-------------------|-----------------|
| **Sydney Metro Content Editors** | System end users, UAT participants, training attendees | Content Manager |
| **Sydney Metro IT Operations** | Infrastructure support, BAU handover recipients | IT Operations Manager |
| **Sydney Metro Application Support** | Application support, incident management | Application Support Lead |
| **Sydney Metro IT Security** | Security validation, compliance oversight | CISO |
| **HCL Transition Team** | Execute transition plan, knowledge transfer | HCL Transition Manager |
| **HCL Technical Team** | Technical support, issue resolution | HCL Technical Lead |
| **HCL Training Team** | Training delivery, user enablement | HCL Training Lead |

---

## 2. Transition Approach and Phases

### 2.1 Transition Methodology

**Phased Transition Approach:**

The transition follows a structured, phased approach to minimize risk and ensure business continuity:

```
Phase 1: Preparation     →   Phase 2: Migration     →   Phase 3: Stabilization
(Weeks 10-11)                (Week 12)                  (Weeks 13-16)

- UAT completion            - Data migration          - Hypercare support
- Training delivery         - System cutover          - Issue resolution
- Documentation             - Smoke testing           - Performance tuning
- Readiness review          - Go-live                 - User support
```

### 2.2 Phase 1: Preparation (Weeks 10-11)

**Objectives:**
- Complete User Acceptance Testing with business users
- Deliver comprehensive training to all user groups
- Finalize all documentation
- Conduct go-live readiness review
- Prepare production environment

**Activities:**

| Activity | Duration | Owner | Deliverables |
|----------|----------|-------|--------------|
| **UAT Execution** | Week 10-11 | QA Team | UAT sign-off, defect resolution |
| **Training Delivery** | Week 10-11 | Training Team | Trained users, training records |
| **Documentation Review** | Week 10-11 | Tech Writers | Approved documentation |
| **Production Environment Setup** | Week 10 | DevOps Team | Production environment ready |
| **Data Migration Rehearsal** | Week 11 | Development Team | Migration validated, timing confirmed |
| **Go-Live Readiness Review** | End Week 11 | Project Manager | Go/No-Go decision |
| **Communication Plan Execution** | Week 11 | Communications | Stakeholders informed |

**Go-Live Readiness Checklist:**

- [ ] UAT completed and signed off by business users
- [ ] All P0 and P1 defects resolved
- [ ] All users trained (100% attendance)
- [ ] Documentation finalized and approved
- [ ] Production environment provisioned and tested
- [ ] Data migration rehearsal successful
- [ ] Performance tests passed
- [ ] Security tests passed (penetration testing, vulnerability scan)
- [ ] Disaster recovery tested successfully
- [ ] Support team trained and ready
- [ ] Communication plan executed (stakeholder notifications sent)
- [ ] Rollback plan documented and tested
- [ ] Monitoring and alerting configured
- [ ] Go-live checklist completed
- [ ] Executive sign-off obtained

**Go/No-Go Decision:**
- **Meeting:** Go-Live Readiness Review (Friday, end of Week 11)
- **Attendees:** Sydney Metro Steering Committee, HCL Project Manager, HCL Technical Lead
- **Decision Criteria:** All checklist items completed, no critical blockers
- **Outcome:** Formal approval to proceed with production cutover

### 2.3 Phase 2: Migration and Cutover (Week 12)

**Cutover Window:**
- **Timing:** Friday evening, 6:00 PM - Sunday, 6:00 PM (48-hour window)
- **Rationale:** Weekend cutover minimizes business impact
- **Rollback Decision Point:** Saturday, 12:00 PM (if critical issues arise)

**Cutover Plan:**

```
Friday 6:00 PM - Cutover Begins
├─ 6:00 PM: Content freeze on Sitecore (read-only mode)
├─ 6:30 PM: Final data export from Sitecore
├─ 7:00 PM: Data transformation and validation
├─ 9:00 PM: Data import to Strapi production
├─ 11:00 PM: Data validation and integrity checks
└─ 12:00 AM: Data migration complete

Saturday 12:00 AM - Production Deployment
├─ 12:00 AM: Deploy Strapi application to production
├─ 1:00 AM: Configure DNS and routing
├─ 2:00 AM: Smoke testing (critical user journeys)
├─ 4:00 AM: Extended testing (all functionality)
├─ 8:00 AM: User acceptance testing with pilot users
├─ 12:00 PM: Go/No-Go decision (rollback point)
└─ 2:00 PM: Final validation complete

Saturday 2:00 PM - Go-Live
├─ 2:00 PM: Switch DNS to point to Strapi production
├─ 2:30 PM: Monitor traffic and performance
├─ 3:00 PM: Pilot user group testing (10 users)
├─ 5:00 PM: Expand to broader user base (50 users)
└─ Sunday 8:00 AM: Full user base access

Sunday 8:00 AM - Stabilization
├─ 8:00 AM: All users can access new system
├─ Continuous monitoring throughout Sunday
├─ Hypercare team on standby
└─ 6:00 PM: Cutover window closes, post-cutover review
```

**Cutover Roles and Responsibilities:**

| Role | Responsibilities | Contact |
|------|------------------|---------|
| **Cutover Manager** | Overall cutover coordination, decision-making | HCL Project Manager |
| **Technical Lead** | Technical execution, troubleshooting | HCL Technical Lead |
| **Database Lead** | Data migration execution and validation | HCL Database Engineer |
| **DevOps Lead** | Infrastructure deployment, DNS changes | HCL DevOps Engineer |
| **QA Lead** | Smoke testing, validation | HCL QA Lead |
| **Sydney Metro Sponsor** | Business approval, escalation point | Sydney Metro IT Director |
| **Support Team** | User support, issue logging | HCL Support Team |

**Cutover Communication:**

| Milestone | Communication | Audience |
|-----------|---------------|----------|
| **Cutover Start** | "Cutover has begun. Sitecore is now read-only." | All stakeholders |
| **Data Migration Complete** | "Data migration complete. Validation in progress." | Cutover team |
| **Deployment Complete** | "Production deployment complete. Testing begins." | Cutover team |
| **Go/No-Go Decision** | "Decision to proceed / rollback" | All stakeholders |
| **Go-Live** | "New CMS is now live for pilot users." | Pilot users |
| **Full Go-Live** | "New CMS is now available to all users." | All users |
| **Cutover Complete** | "Cutover successfully completed." | All stakeholders |

**Rollback Plan:**

If critical issues arise, the following rollback procedure will be executed:

1. **Rollback Decision Criteria:**
   - Data integrity issues (data loss, corruption)
   - Critical functionality not working
   - Performance below acceptable thresholds
   - Security vulnerabilities discovered

2. **Rollback Procedure:**
   - **Step 1:** Switch DNS back to Sitecore (15 minutes)
   - **Step 2:** Re-enable Sitecore for read-write (5 minutes)
   - **Step 3:** Notify all users of rollback (immediate)
   - **Step 4:** Investigate and resolve issues (as needed)
   - **Step 5:** Schedule new cutover date (TBD)

3. **Rollback Testing:**
   - Rollback procedure tested during migration rehearsal
   - Documented step-by-step instructions
   - Tested by DevOps team in pre-production environment

### 2.4 Phase 3: Stabilization and Hypercare (Weeks 13-16)

**Hypercare Objectives:**
- Provide intensive support to users during initial weeks
- Quickly resolve any issues that arise
- Monitor system performance and stability
- Build user confidence in the new system
- Gather feedback for continuous improvement

**Hypercare Support Model:**

**Week 13-14 (Intensive Hypercare):**
- **Coverage:** 24/7 support
- **Response Time:** 1 hour for all issues
- **On-site Presence:** HCL team on-site at Sydney Metro (3-5 people)
- **Daily Touchpoints:** Morning standup (9:00 AM), end-of-day review (5:00 PM)

**Week 15-16 (Graduated Hypercare):**
- **Coverage:** Business hours support (7:00 AM - 7:00 PM AEST, Mon-Fri)
- **Response Time:** 2 hours for high priority, 4 hours for medium priority
- **On-site Presence:** Reduced to 2 people
- **Daily Touchpoints:** Morning standup only

**Hypercare Activities:**

| Activity | Frequency | Purpose |
|----------|-----------|---------|
| **User Support** | Continuous | Help users with questions, issues, guidance |
| **Issue Triage** | Real-time | Categorize and prioritize reported issues |
| **Defect Resolution** | As needed | Fix bugs and defects quickly |
| **Performance Monitoring** | Continuous | Monitor system performance, identify bottlenecks |
| **User Feedback Collection** | Daily | Gather user feedback for improvements |
| **Daily Standup** | Daily (9:00 AM) | Review previous day, plan for current day |
| **End-of-Day Review** | Daily (5:00 PM) | Summarize day's activities, escalate issues |
| **Weekly Status Report** | Weekly | Report to Sydney Metro leadership |

**Hypercare Support Channels:**

| Channel | Purpose | Availability |
|---------|---------|--------------|
| **Dedicated Email** | cms-support@hcl.com | 24/7 (monitored) |
| **Dedicated Phone** | 1800-HCL-SUPPORT | 24/7 (Weeks 13-14), Business hours (Weeks 15-16) |
| **On-site Support Desk** | In-person assistance at Sydney Metro office | Business hours |
| **Microsoft Teams Chat** | Real-time chat support | Business hours |
| **ServiceNow Portal** | Ticket submission and tracking | 24/7 (self-service) |

**Hypercare Issue Management:**

**Issue Severity Levels:**

| Severity | Definition | Response Time | Resolution Time |
|----------|------------|---------------|-----------------|
| **P0 - Critical** | System down, no workaround | 15 minutes | 2 hours |
| **P1 - High** | Major functionality impaired, workaround available | 1 hour | 4 hours |
| **P2 - Medium** | Functionality degraded, acceptable workaround | 2 hours | 8 hours |
| **P3 - Low** | Minor issue, cosmetic | 4 hours | 24 hours |
| **P4 - Enhancement** | Feature request, improvement | Logged for future | Backlog |

**Issue Escalation:**
- If issue not resolved within response time → Escalate to HCL Technical Lead
- If issue not resolved within resolution time → Escalate to HCL Delivery Manager
- If critical business impact → Escalate to Sydney Metro Sponsor

**Hypercare Metrics:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| **First Response Time** | 100% within SLA | ServiceNow tracking |
| **Issue Resolution Time** | 95% within SLA | ServiceNow tracking |
| **User Satisfaction** | ≥ 4.0 / 5.0 | Daily feedback surveys |
| **System Availability** | ≥ 99.9% | CloudWatch monitoring |
| **Performance (Page Load)** | < 2 seconds | Synthetic monitoring |
| **Open Issues** | Trending down | Daily issue count |

**Hypercare Success Criteria:**
- All P0 and P1 issues resolved
- User satisfaction ≥ 4.0 / 5.0
- System availability ≥ 99.9%
- Performance targets met consistently
- Declining trend in support requests
- Positive feedback from business users

**Hypercare Exit:**
- **Review Meeting:** End of Week 16
- **Attendees:** Sydney Metro Sponsor, HCL Project Manager, HCL Hypercare Lead
- **Decision:** Transition from Hypercare to Warranty support (or extend Hypercare if needed)

---

## 3. Knowledge Transfer Strategy

### 3.1 Knowledge Transfer Objectives

1. **Technical Knowledge:** Transfer technical knowledge to Sydney Metro IT Operations and Application Support teams
2. **Operational Knowledge:** Transfer day-to-day operational procedures
3. **Support Knowledge:** Enable Sydney Metro teams to provide ongoing support
4. **Maintenance Knowledge:** Enable Sydney Metro teams to maintain and enhance the system
5. **Troubleshooting Knowledge:** Build capability to diagnose and resolve issues

### 3.2 Knowledge Transfer Framework

**Knowledge Transfer Approach:**

```
┌────────────────────────────────────────────────────────────┐
│               Knowledge Transfer Framework                 │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  Knowledge Source        Method           Recipient        │
│  ─────────────────      ─────────       ─────────────     │
│                                                            │
│  HCL Technical Team  →  Training     →  IT Operations     │
│                     →  Documentation →  App Support       │
│                     →  Shadowing     →  Administrators    │
│                     →  Reverse      →  Developers         │
│                          Shadowing                         │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

**Knowledge Transfer Methods:**

| Method | Description | When Used | Effectiveness |
|--------|-------------|-----------|---------------|
| **Formal Training** | Structured classroom/virtual training sessions | For all user groups | High for foundational knowledge |
| **Documentation** | Written guides, runbooks, architecture docs | Ongoing reference | High for procedural knowledge |
| **Shadowing** | Sydney Metro team observes HCL team | During hypercare | High for operational knowledge |
| **Reverse Shadowing** | HCL team observes Sydney Metro team | End of hypercare | High for validation |
| **Hands-on Labs** | Practical exercises in safe environment | During training | High for skill-building |
| **Q&A Sessions** | Dedicated sessions for questions | Weekly during transition | Medium for clarification |
| **Knowledge Base** | Searchable repository of articles | Ongoing | High for self-service |
| **Video Tutorials** | Recorded walkthroughs | Ongoing reference | Medium for visual learners |

### 3.3 Knowledge Transfer Schedule

**Week 10-11: Intensive Knowledge Transfer**

| Session | Audience | Duration | Content |
|---------|----------|----------|---------|
| **System Architecture Overview** | IT Operations, App Support | 4 hours | Architecture, components, data flows |
| **Infrastructure Management** | IT Operations | 4 hours | AWS infrastructure, deployment, scaling |
| **Application Configuration** | App Support | 4 hours | Strapi configuration, plugins, customizations |
| **Database Administration** | IT Operations | 3 hours | PostgreSQL administration, backup/restore |
| **Security Administration** | IT Security, IT Operations | 3 hours | Security controls, access management |
| **Monitoring and Alerting** | IT Operations, App Support | 3 hours | CloudWatch, Grafana, alerting rules |
| **Troubleshooting and Support** | App Support | 4 hours | Common issues, diagnostic procedures |
| **Content Management** | App Support, Content Managers | 2 hours | Content workflows, approval processes |

**Week 12: Cutover Knowledge Sharing**
- HCL team executes cutover with Sydney Metro team observing
- Step-by-step walkthrough of cutover procedures
- Real-time knowledge transfer during deployment

**Week 13-16: Hypercare Knowledge Transfer**
- **Shadowing:** Sydney Metro team shadows HCL team during issue resolution
- **Reverse Shadowing:** HCL team observes Sydney Metro team handling issues (Week 15-16)
- **Daily Huddles:** Review lessons learned from previous day

**Month 5-6: Advanced Knowledge Transfer**
- **Advanced Configuration:** Deep dive into customizations
- **Performance Tuning:** Optimization techniques
- **Troubleshooting Complex Issues:** Advanced diagnostic techniques

### 3.4 Knowledge Transfer Materials

**Documentation Provided:**
- System Architecture Document
- Infrastructure as Code (Terraform) with annotations
- Deployment Runbooks
- Operations Runbooks (backup, restore, scaling, monitoring)
- Troubleshooting Guide
- Security Administration Guide
- User Administration Guide
- API Documentation
- Integration Guide
- Disaster Recovery Procedures

**Training Materials Provided:**
- PowerPoint presentations for all training sessions
- Hands-on lab guides
- Quick reference guides (cheat sheets)
- Video tutorials (screen recordings)
- FAQs document

**Knowledge Base:**
- Confluence space with all documentation
- Searchable knowledge articles
- Troubleshooting decision trees
- Configuration examples
- Common issue resolutions

### 3.5 Knowledge Validation

**Knowledge Assessment:**
- Quiz at end of each training session (80% pass rate required)
- Hands-on practical assessment (successfully complete tasks)
- Reverse shadowing observation (HCL team validates competency)

**Knowledge Transfer Success Criteria:**
- 100% of planned knowledge transfer sessions completed
- Sydney Metro teams can perform day-to-day operations independently
- Sydney Metro teams can resolve 80% of support issues without HCL assistance
- Positive feedback from Sydney Metro teams on knowledge transfer effectiveness

---

## 4. Training Program

### 4.1 Training Objectives

1. **User Adoption:** Ensure all users are comfortable and proficient with the new CMS
2. **Productivity:** Minimize productivity loss during transition
3. **Self-Sufficiency:** Reduce dependency on support team
4. **Best Practices:** Instill best practices for content management
5. **Confidence:** Build user confidence in the new system

### 4.2 Training Audience Segmentation

**User Roles and Training Needs:**

| User Role | Count | Training Needs | Training Duration |
|-----------|-------|----------------|-------------------|
| **Content Editors** | 20-30 | Content creation, editing, publishing, media management | 4 hours |
| **Content Approvers** | 5-8 | Approval workflows, content review | 2 hours |
| **Content Managers** | 5-8 | Full content management, workflow configuration, reporting | 6 hours |
| **System Administrators** | 2-3 | User management, system configuration, security, troubleshooting | 8 hours |
| **IT Operations** | 3-5 | Infrastructure, deployment, monitoring, backup/restore | 8 hours |
| **Application Support** | 3-5 | Support procedures, issue resolution, configuration | 6 hours |
| **Developers** | 2-3 | API integration, customizations, plugin development | 8 hours |

### 4.3 Training Curriculum

**Training Track 1: Content Editor Training (4 hours)**

**Module 1: Introduction to Strapi CMS (30 minutes)**
- Overview of Strapi vs. Sitecore
- Interface navigation
- User roles and permissions
- Logging in with Azure AD

**Module 2: Content Management Basics (60 minutes)**
- Creating new content
- Editing existing content
- Using the rich text editor
- Adding images and media
- Saving drafts
- Hands-on Lab: Create a news article

**Module 3: Multi-language Content (45 minutes)**
- Adding English content
- Adding Simplified Chinese translations
- Language switcher
- Best practices for translations
- Hands-on Lab: Create multi-language content

**Module 4: Content Publishing Workflow (45 minutes)**
- Submitting content for approval
- Tracking approval status
- Publishing approved content
- Scheduling future publication
- Archiving old content
- Hands-on Lab: Complete approval workflow

**Module 5: Media Management (30 minutes)**
- Uploading media files
- Organizing media library
- Tagging and categorizing media
- Using CDN-optimized images
- Hands-on Lab: Upload and organize media

**Module 6: Tips, Tricks, and Best Practices (30 minutes)**
- Content best practices
- Accessibility considerations
- Common mistakes to avoid
- Keyboard shortcuts
- Q&A session

**Training Track 2: Content Approver Training (2 hours)**

**Module 1: Approval Workflow (60 minutes)**
- Receiving approval requests
- Reviewing content for accuracy and compliance
- Approving or rejecting content with comments
- Tracking approval history
- Hands-on Lab: Approve and reject content

**Module 2: Content Quality Assurance (45 minutes)**
- Content review checklist
- Accessibility checks
- Brand consistency
- Legal and compliance considerations
- Hands-on Lab: Review content using checklist

**Module 3: Reporting and Analytics (15 minutes)**
- Content approval reports
- Workflow performance metrics
- Q&A session

**Training Track 3: Content Manager Training (6 hours)**

**Includes:** All Content Editor training (4 hours) +

**Module 7: Advanced Content Management (60 minutes)**
- Content types and structures
- Metadata and taxonomies
- Content relationships
- Bulk operations
- Content versioning
- Hands-on Lab: Advanced content scenarios

**Module 8: Workflow Configuration (45 minutes)**
- Configuring approval workflows
- Setting up content lifecycle
- Defining roles and permissions per content type
- Hands-on Lab: Configure custom workflow

**Module 9: Reporting and Analytics (45 minutes)**
- Content inventory reports
- User activity reports
- Performance analytics
- Export reports
- Hands-on Lab: Generate reports

**Training Track 4: System Administrator Training (8 hours)**

**Module 1: System Architecture (60 minutes)**
- Strapi architecture overview
- AWS infrastructure
- Database structure
- Security model

**Module 2: User Management (60 minutes)**
- Creating and managing users
- Assigning roles and permissions
- Azure AD integration
- Access reviews
- Hands-on Lab: User administration

**Module 3: System Configuration (90 minutes)**
- Strapi admin settings
- Plugin configuration
- Email notifications
- System performance settings
- Hands-on Lab: Configure system settings

**Module 4: Security Administration (90 minutes)**
- Access control configuration
- Security monitoring
- Audit logging
- Security best practices
- Hands-on Lab: Security configuration

**Module 5: Backup and Restore (60 minutes)**
- Backup procedures
- Restore procedures
- Testing backups
- Hands-on Lab: Perform backup and restore

**Module 6: Monitoring and Troubleshooting (90 minutes)**
- CloudWatch dashboards
- Alerting configuration
- Log analysis
- Common issues and resolutions
- Hands-on Lab: Troubleshooting scenarios

**Module 7: API Management (60 minutes)**
- API endpoint management
- API authentication and security
- Rate limiting configuration
- API documentation

**Training Track 5: IT Operations Training (8 hours)**

**Module 1: Infrastructure Overview (60 minutes)**
- AWS architecture
- ECS Fargate containers
- RDS PostgreSQL
- S3 and CloudFront
- VPC and networking

**Module 2: Deployment Procedures (90 minutes)**
- CI/CD pipeline
- Deployment process
- Rollback procedures
- Hands-on Lab: Deploy application

**Module 3: Monitoring and Alerting (90 minutes)**
- CloudWatch metrics
- Grafana dashboards
- Alerting rules
- On-call procedures
- Hands-on Lab: Configure monitoring

**Module 4: Backup and Disaster Recovery (90 minutes)**
- Backup strategy
- Restore procedures
- DR testing
- Hands-on Lab: DR scenario

**Module 5: Performance Tuning (60 minutes)**
- Performance monitoring
- Optimization techniques
- Scaling strategies
- Capacity planning

**Module 6: Security Operations (60 minutes)**
- Security monitoring
- Incident response
- Security tools (GuardDuty, Security Hub)
- Vulnerability management

**Module 7: Troubleshooting (90 minutes)**
- Diagnostic procedures
- Common infrastructure issues
- Escalation procedures
- Hands-on Lab: Troubleshooting scenarios

**Training Track 6: Developer Training (8 hours)**

**Module 1: Strapi Development Overview (60 minutes)**
- Strapi architecture for developers
- Development environment setup
- Code structure
- Development workflow

**Module 2: API Development (120 minutes)**
- RESTful API structure
- Custom API endpoints
- API authentication
- Hands-on Lab: Create custom API

**Module 3: Plugin Development (120 minutes)**
- Plugin architecture
- Creating custom plugins
- Plugin best practices
- Hands-on Lab: Develop simple plugin

**Module 4: Customizations (90 minutes)**
- Customizing admin panel
- Custom content types
- Custom fields
- Hooks and lifecycle events
- Hands-on Lab: Implement customization

**Module 5: Integration Development (90 minutes)**
- Integrating with external systems
- Webhooks
- Event-driven architecture
- Hands-on Lab: Build integration

**Module 6: Testing and Debugging (60 minutes)**
- Unit testing
- Integration testing
- Debugging techniques
- Hands-on Lab: Write tests

### 4.4 Training Delivery

**Training Format:**
- **In-Person Training:** Preferred for hands-on training (at Sydney Metro office)
- **Virtual Training:** Available via Microsoft Teams (for remote participants)
- **Recorded Sessions:** All sessions recorded for future reference
- **Hands-on Labs:** Dedicated UAT environment for practice

**Training Schedule (Week 10-11):**

| Date | Time | Session | Audience | Trainer |
|------|------|---------|----------|---------|
| **Week 10** | | | | |
| Monday | 9:00 AM - 1:00 PM | Content Editor Training (Batch 1) | 15 editors | HCL Trainer 1 |
| Monday | 2:00 PM - 6:00 PM | Content Editor Training (Batch 2) | 15 editors | HCL Trainer 2 |
| Tuesday | 9:00 AM - 11:00 AM | Content Approver Training | 8 approvers | HCL Trainer 1 |
| Tuesday | 1:00 PM - 7:00 PM | Content Manager Training | 8 managers | HCL Trainer 2 |
| Wednesday | 9:00 AM - 5:00 PM | System Administrator Training (Day 1) | 3 admins | HCL Technical Lead |
| Thursday | 9:00 AM - 5:00 PM | System Administrator Training (Day 2) | 3 admins | HCL Technical Lead |
| Friday | 9:00 AM - 5:00 PM | IT Operations Training | 5 ops team | HCL DevOps Lead |
| **Week 11** | | | | |
| Monday | 9:00 AM - 5:00 PM | IT Operations Training (Day 2) | 5 ops team | HCL DevOps Lead |
| Tuesday | 9:00 AM - 5:00 PM | Developer Training | 3 developers | HCL Development Lead |
| Wednesday | 9:00 AM - 12:00 PM | Application Support Training | 5 support team | HCL Support Lead |

**Training Materials:**
- Participant workbooks (printed and digital)
- Hands-on lab guides
- Quick reference cards
- Cheat sheets for common tasks
- Video recordings of all sessions

**Training Environment:**
- Dedicated UAT environment for training
- Each participant has individual login credentials
- Pre-populated with sample content
- Reset nightly for fresh start each day

### 4.5 Training Assessment

**Knowledge Checks:**
- Quiz at end of each session (10 multiple-choice questions)
- Passing score: 80%
- Retake available if needed

**Hands-on Assessment:**
- Practical exercises during training
- Final practical assessment (complete realistic scenario)
- Pass/Fail based on task completion

**Post-Training Survey:**
- Training content quality (1-5 scale)
- Trainer effectiveness (1-5 scale)
- Training materials quality (1-5 scale)
- Confidence in using new system (1-5 scale)
- Suggestions for improvement

**Training Success Metrics:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| **Training Attendance** | 100% of required users | Attendance records |
| **Training Completion** | 100% completion rate | Completion certificates |
| **Knowledge Assessment** | 90% pass rate (80%+ score) | Quiz scores |
| **Practical Assessment** | 90% pass rate | Hands-on evaluation |
| **User Satisfaction** | ≥ 4.0 / 5.0 | Post-training survey |
| **User Confidence** | ≥ 4.0 / 5.0 | Post-training survey |

**Remedial Training:**
- Users who don't pass assessment offered one-on-one coaching
- Recorded sessions available for review
- Optional "office hours" for additional help

### 4.6 Ongoing Training Support

**Post-Go-Live Training Support:**
- **Office Hours:** Weekly drop-in sessions for questions (Weeks 13-20)
- **Refresher Training:** Optional refresher sessions after 3 months
- **New User Onboarding:** Training for new hires joining after go-live
- **Advanced Training:** Optional advanced sessions on specific topics

**Self-Service Learning:**
- **Knowledge Base:** Searchable articles on common tasks
- **Video Library:** Short (5-10 min) videos on specific topics
- **Interactive Tutorials:** In-app guided tours
- **FAQs:** Frequently asked questions document

---

## 5. Documentation Deliverables

### 5.1 Documentation Strategy

**Documentation Principles:**
- **User-Centric:** Written for the audience (technical vs. business users)
- **Accurate:** Reflects actual system behavior
- **Concise:** Clear and to-the-point
- **Searchable:** Well-organized and indexed
- **Maintainable:** Easy to update as system evolves
- **Accessible:** Available in multiple formats (web, PDF)

### 5.2 Technical Documentation

**Architecture Documentation:**

| Document | Content | Audience | Format |
|----------|---------|----------|--------|
| **System Architecture Document** | High-level architecture, components, data flows | IT Operations, Architects | PDF + Confluence |
| **Infrastructure Architecture** | AWS resources, networking, security groups | IT Operations, DevOps | PDF + Confluence |
| **Security Architecture** | Security controls, access management, encryption | Security Team | PDF + Confluence |
| **Data Architecture** | Database schema, data models, relationships | Developers, DBAs | PDF + Confluence |
| **Integration Architecture** | API specifications, integration points | Developers | PDF + Confluence |

**Operations Documentation:**

| Document | Content | Audience | Format |
|----------|---------|----------|--------|
| **Deployment Runbook** | Step-by-step deployment procedures | DevOps, IT Ops | Confluence |
| **Backup and Restore Runbook** | Backup procedures, restore procedures | IT Operations | Confluence |
| **Disaster Recovery Procedures** | DR activation, recovery steps, testing | IT Operations | Confluence |
| **Monitoring and Alerting Guide** | Dashboard usage, alert response | IT Operations | Confluence |
| **Troubleshooting Guide** | Common issues, diagnostic steps, resolutions | IT Operations, App Support | Confluence |
| **Scaling Procedures** | Manual scaling, auto-scaling configuration | IT Operations | Confluence |
| **Patch Management Procedures** | Patching process, testing, rollback | IT Operations | Confluence |

**Developer Documentation:**

| Document | Content | Audience | Format |
|----------|---------|----------|--------|
| **API Documentation** | REST API endpoints, authentication, examples | Developers | Swagger UI + PDF |
| **Development Setup Guide** | Local dev environment setup | Developers | Confluence |
| **Coding Standards** | Code style, best practices | Developers | Confluence |
| **Plugin Development Guide** | How to create Strapi plugins | Developers | Confluence |
| **Customization Guide** | How to customize Strapi | Developers | Confluence |
| **Database Schema Documentation** | Tables, relationships, indexes | Developers, DBAs | PDF + Confluence |
| **Testing Guide** | Unit testing, integration testing | Developers, QA | Confluence |

**Security Documentation:**

| Document | Content | Audience | Format |
|----------|---------|----------|--------|
| **Security Administration Guide** | User management, RBAC, access reviews | System Admins, Security | Confluence |
| **Security Compliance Documentation** | ISO 27001, IRAP compliance evidence | Security, Auditors | PDF |
| **Incident Response Procedures** | Incident handling steps, escalation | Security, IT Operations | Confluence |
| **Security Monitoring Guide** | Security tools, alert response | Security Team | Confluence |
| **Penetration Testing Report** | Findings, remediation | Security Team | PDF (confidential) |

### 5.3 User Documentation

**End-User Documentation:**

| Document | Content | Audience | Format |
|----------|---------|----------|--------|
| **User Guide - Content Editor** | Content creation, editing, publishing | Content Editors | PDF + Web |
| **User Guide - Content Approver** | Approval workflows, content review | Content Approvers | PDF + Web |
| **User Guide - Content Manager** | Advanced content management, reporting | Content Managers | PDF + Web |
| **Quick Start Guide** | Getting started, basic tasks | All Users | PDF (2 pages) |
| **Quick Reference Card** | Common tasks, shortcuts | All Users | PDF (1 page, laminated) |
| **FAQs** | Frequently asked questions | All Users | Web + PDF |
| **Video Tutorials** | Screen recordings of common tasks | All Users | Video library |

**Administrator Documentation:**

| Document | Content | Audience | Format |
|----------|---------|----------|--------|
| **System Administrator Guide** | User management, configuration, security | System Admins | PDF + Confluence |
| **Configuration Guide** | System settings, plugins, customizations | System Admins | Confluence |
| **Reporting Guide** | How to generate and interpret reports | Admins, Managers | PDF + Confluence |

### 5.4 Process Documentation

**Business Process Documentation:**

| Document | Content | Audience | Format |
|----------|---------|----------|--------|
| **Content Publishing Workflow** | End-to-end content creation to publishing | Content Team | Confluence |
| **Content Approval Process** | Approval workflow, escalation | Content Team, Managers | Confluence |
| **User Onboarding Process** | How to onboard new users | System Admins | Confluence |
| **Change Management Process** | How system changes are requested and approved | IT Operations | Confluence |
| **Support Process** | How to log issues, escalation paths | All Users | Confluence |

### 5.5 Documentation Maintenance

**Documentation Updates:**
- **Ownership:** HCL owns documentation during warranty period
- **Update Frequency:** After each system change or update
- **Version Control:** All documentation versioned in Confluence
- **Review Cycle:** Quarterly review for accuracy

**Documentation Handover:**
- **Knowledge Transfer:** HCL trains Sydney Metro team on documentation maintenance
- **Ownership Transfer:** Documentation ownership transfers to Sydney Metro at end of warranty
- **Templates Provided:** Documentation templates for future updates

### 5.6 Documentation Delivery

**Delivery Format:**
- **Confluence Space:** Primary documentation repository (searchable, collaborative)
- **PDF Downloads:** PDF versions available for offline access
- **Video Library:** Hosted on Sydney Metro SharePoint or similar
- **Printed Manuals:** Quick Start Guides and Reference Cards (for select users)

**Delivery Timeline:**
- **Week 11:** All documentation finalized and approved
- **Week 12:** Documentation available in Confluence before go-live
- **Week 13:** Printed materials distributed to users
- **Ongoing:** Documentation updated as needed

---

## 6. Hypercare Support

### 6.1 Hypercare Objectives

**(Covered in Section 2.4 - see above for full details)**

- Provide intensive support during initial weeks post-go-live
- Ensure smooth transition for users
- Quickly resolve issues
- Build confidence in new system

### 6.2 Hypercare Support Model

**(Covered in Section 2.4 - see above for full details)**

**Weeks 13-14: Intensive Hypercare (24/7)**
**Weeks 15-16: Graduated Hypercare (Business hours)**

### 6.3 Hypercare Support Channels

**(Covered in Section 2.4 - see above for full details)**

- Dedicated Email
- Dedicated Phone Hotline
- On-site Support Desk
- Microsoft Teams Chat
- ServiceNow Portal

### 6.4 Hypercare Success Criteria

**(Covered in Section 2.4 - see above for full details)**

- All P0/P1 issues resolved
- User satisfaction ≥ 4.0/5.0
- System availability ≥ 99.9%
- Declining support requests

---

## 7. Warranty Period

### 7.1 Warranty Overview

**Warranty Duration:** 12 months from go-live date

**Warranty Coverage:**
- Defect resolution (bugs in delivered system)
- Performance issues related to original design
- Security vulnerabilities in delivered code
- Documentation corrections
- Knowledge transfer follow-up

**Warranty Exclusions:**
- New feature requests (scope changes)
- Issues caused by Sydney Metro modifications
- Issues caused by third-party changes
- Infrastructure issues beyond application code
- User error or misuse

### 7.2 Warranty Support Model

**Support Channels:**
| Channel | Availability | Purpose |
|---------|--------------|---------|
| **Email** | warranty-support@hcl.com | Non-urgent issues, documentation requests |
| **Phone** | Business hours (Mon-Fri, 9:00 AM - 5:00 PM AEST) | Urgent issues |
| **ServiceNow** | 24/7 (ticket submission) | Issue tracking |
| **Monthly Check-in** | Scheduled meetings | Proactive health checks |

**Support Response SLAs:**

| Severity | Definition | Response Time | Resolution Time |
|----------|------------|---------------|-----------------|
| **P0 - Critical** | Production outage, data loss | 2 hours | 8 hours |
| **P1 - High** | Major functionality broken, workaround available | 4 hours | 24 hours |
| **P2 - Medium** | Functionality impaired, acceptable workaround | 1 business day | 5 business days |
| **P3 - Low** | Minor issue, cosmetic | 2 business days | 10 business days |

**Warranty Support Team:**
- Dedicated HCL support engineer (1 FTE)
- Escalation to HCL technical team as needed
- Access to original development team for complex issues

### 7.3 Defect Management Process

**Defect Definition:**
- Software does not perform as documented in requirements
- Software does not meet acceptance criteria
- Security vulnerability in delivered code
- Performance degradation below specified thresholds

**Defect Reporting:**
1. Sydney Metro logs defect in ServiceNow
2. HCL support team triages within response SLA
3. HCL confirms defect (or classifies as enhancement/user error)
4. If confirmed defect, HCL assigns severity and prioritizes
5. HCL develops fix and tests in non-production environment
6. HCL deploys fix to production (with Sydney Metro approval)
7. Sydney Metro validates fix
8. Defect closed

**Defect Tracking:**
- All defects tracked in ServiceNow
- Weekly defect status reports shared with Sydney Metro
- Monthly trend analysis (defect volume, types, resolution time)

### 7.4 Warranty Support Activities

**Ongoing Support:**
- Defect resolution (as reported)
- Security patch application (for delivered code)
- Documentation updates (corrections only)
- Knowledge transfer follow-up sessions (as needed)

**Proactive Support:**
- **Monthly Health Checks:**
  - System performance review
  - Security posture review
  - Log analysis for potential issues
  - Backup validation
  - Capacity planning

- **Quarterly System Reviews:**
  - Comprehensive system assessment
  - Performance optimization recommendations
  - Security updates review
  - Documentation review
  - User feedback review

- **Knowledge Base Updates:**
  - Add new articles based on support tickets
  - Update existing articles for accuracy
  - Create troubleshooting guides

**Warranty Reporting:**
- **Weekly Status Report:** Defect status, open issues
- **Monthly Health Report:** System health, metrics, trends
- **Quarterly Review Report:** Comprehensive system review, recommendations

### 7.5 Warranty Exit

**End of Warranty Period (Month 16):**

**Transition to BAU:**
- **Final System Review:** Comprehensive system assessment
- **Knowledge Transfer Validation:** Confirm Sydney Metro team fully capable
- **Documentation Handover:** Transfer ownership of all documentation
- **Final Report:** Summary of warranty period, lessons learned, recommendations
- **Closure Meeting:** Formal handover and closure

**Post-Warranty Support Options:**
1. **Managed Services:** HCL continues to provide ongoing support (separate contract)
2. **Time and Materials:** HCL provides ad-hoc support as needed
3. **Break-Fix Support:** HCL provides support for critical issues only
4. **Fully Independent:** Sydney Metro manages system entirely in-house

---

## 8. BAU Handover Process

### 8.1 BAU Handover Objectives

1. **Operational Readiness:** Ensure Sydney Metro teams are ready to operate the system independently
2. **Knowledge Transfer:** Complete transfer of all operational knowledge
3. **Process Integration:** Integrate CMS operations into existing BAU processes
4. **Continuous Improvement:** Establish processes for ongoing system improvements
5. **Risk Mitigation:** Ensure smooth handover with minimal operational risk

### 8.2 BAU Handover Framework

**Handover Phases:**

```
Phase 1: Preparation          Phase 2: Transition          Phase 3: Validation
(Month 4-5)                   (Month 5-6)                  (Month 6)

- BAU team identification     - Shadowing HCL team         - Reverse shadowing
- Training completion         - Handling supervised        - Independent operations
- Documentation review           issues                    - HCL observes and validates
- Process alignment           - Gradual responsibility     - Final sign-off
                                transfer
```

### 8.3 BAU Roles and Responsibilities

**Sydney Metro BAU Roles:**

| Role | Responsibilities | Team Size |
|------|------------------|-----------|
| **Application Support Team** | L1/L2 user support, incident management, issue triage | 3-5 FTE |
| **System Administrators** | User management, configuration, access reviews | 2-3 FTE |
| **IT Operations Team** | Infrastructure monitoring, deployment, backup/restore | 3-5 FTE |
| **Security Operations** | Security monitoring, incident response, vulnerability management | 2 FTE (shared) |
| **Database Administrators** | Database maintenance, performance tuning (if dedicated) | 1 FTE (shared) |

**RACI Matrix for BAU Operations:**

| Activity | App Support | Sys Admin | IT Ops | Security | HCL (Warranty) |
|----------|-------------|-----------|--------|----------|----------------|
| **User Support (L1)** | R | C | I | I | I |
| **Issue Triage** | R | C | C | I | C |
| **Incident Management** | A | R | R | C | C |
| **User Management** | I | R | I | I | I |
| **System Configuration** | C | R | I | C | C |
| **Deployment** | I | C | R | C | C |
| **Monitoring** | C | C | R | C | I |
| **Backup/Restore** | I | C | R | I | C |
| **Security Monitoring** | I | C | C | R | C |
| **Defect Resolution (Warranty)** | C | C | C | C | R |

### 8.4 BAU Process Integration

**Integration with Existing Processes:**

**Incident Management:**
- CMS incidents logged in existing ServiceNow instance
- Follow Sydney Metro's incident management process
- Integration with existing escalation procedures
- SLA alignment with Sydney Metro standards

**Change Management:**
- CMS changes follow Sydney Metro change management process
- CAB (Change Advisory Board) approval for production changes
- Change windows aligned with Sydney Metro standards
- Rollback procedures documented and tested

**Access Management:**
- User access requests through existing IAM process
- Regular access reviews (quarterly)
- Joiner/Mover/Leaver process integration
- Compliance with Sydney Metro security policies

**Asset Management:**
- CMS registered in Sydney Metro CMDB (Configuration Management Database)
- Software licenses tracked
- Infrastructure assets documented
- Vendor contracts managed

**Monitoring and Alerting:**
- Integrate with Sydney Metro's monitoring platform (if exists)
- Alert routing to appropriate on-call teams
- Dashboard integration with existing NOC (Network Operations Center)

### 8.5 BAU Operational Procedures

**Day-to-Day Operations:**

**Daily Operations:**
- [ ] Review system health dashboard (CloudWatch, Grafana)
- [ ] Review overnight alerts and errors
- [ ] Check backup success status
- [ ] Monitor user support queue
- [ ] Respond to user inquiries

**Weekly Operations:**
- [ ] Review weekly system health report
- [ ] Perform security scan and review findings
- [ ] Review capacity and performance trends
- [ ] Update documentation (if changes made)
- [ ] Team standup meeting

**Monthly Operations:**
- [ ] Perform full backup restore test
- [ ] Review and update user access (access recertification)
- [ ] Review security logs and audit trail
- [ ] Apply security patches (if needed)
- [ ] Generate monthly health report
- [ ] Monthly health check with HCL (during warranty)

**Quarterly Operations:**
- [ ] Quarterly system review meeting
- [ ] Disaster recovery test
- [ ] Comprehensive security assessment
- [ ] Capacity planning review
- [ ] Performance optimization review
- [ ] Documentation review and update

**Runbooks Provided:**
- Incident Response Runbook
- Deployment Runbook
- Backup and Restore Runbook
- Disaster Recovery Runbook
- User Management Runbook
- Performance Tuning Runbook
- Security Operations Runbook
- Troubleshooting Runbook

### 8.6 BAU Support Model

**Support Tiers:**

**Tier 1 (Application Support Team):**
- User inquiries and requests
- Basic troubleshooting
- Password resets, access requests
- Documentation assistance
- Incident logging and triage
- Escalate to Tier 2 if needed

**Tier 2 (System Administrators / IT Operations):**
- Complex troubleshooting
- Configuration changes
- Performance issues
- Security investigations
- Root cause analysis
- Escalate to HCL (during warranty) or Tier 3 if needed

**Tier 3 (HCL Warranty Support / External Consultants):**
- Defect resolution (during warranty)
- Complex technical issues
- Architecture changes
- Custom development

**Support Escalation:**
- Tier 1 → Tier 2: If issue not resolved within 2 hours
- Tier 2 → Tier 3: If issue not resolved within 4 hours or requires code changes
- Urgent issues (P0/P1): Direct escalation to Tier 2/Tier 3

### 8.7 Continuous Improvement

**Continuous Improvement Framework:**

**Feedback Collection:**
- User feedback surveys (quarterly)
- Support ticket analysis (identify recurring issues)
- Performance metrics review
- Security posture assessment

**Improvement Initiatives:**
- Quarterly improvement planning sessions
- Prioritize based on business value and effort
- Implement high-value, low-effort improvements first
- Track improvement metrics

**Knowledge Management:**
- Maintain and expand knowledge base
- Document new troubleshooting procedures
- Share lessons learned
- Conduct "brown bag" learning sessions

**Performance Optimization:**
- Regular performance reviews
- Identify and resolve bottlenecks
- Capacity planning and scaling
- Cost optimization

### 8.8 BAU Handover Validation

**Validation Criteria:**

**Operational Readiness:**
- [ ] All BAU team members trained and certified
- [ ] All runbooks reviewed and understood
- [ ] BAU team has successfully resolved 80% of support issues independently (during hypercare)
- [ ] Reverse shadowing completed successfully
- [ ] BAU team demonstrates competency in all key operational tasks

**Process Integration:**
- [ ] CMS integrated into existing incident management process
- [ ] CMS integrated into existing change management process
- [ ] CMS integrated into existing access management process
- [ ] CMS registered in CMDB
- [ ] Monitoring integrated with existing platforms

**Documentation:**
- [ ] All documentation delivered and reviewed
- [ ] Runbooks tested and validated
- [ ] Knowledge base articles created
- [ ] BAU team comfortable navigating documentation

**System Stability:**
- [ ] System availability ≥ 99.9% over last 30 days
- [ ] No open P0 or P1 defects
- [ ] Performance targets consistently met
- [ ] Security posture acceptable

**Formal Sign-Off:**
- BAU Handover Review Meeting (Month 6)
- Attendees: Sydney Metro IT Director, BAU Team Leads, HCL Project Manager
- Review validation criteria
- Sign-off on BAU handover
- Transition to warranty support

### 8.9 Post-Handover Support

**Ongoing HCL Engagement (During Warranty):**
- Monthly health checks
- Quarterly system reviews
- Defect resolution (as per SLA)
- Knowledge transfer follow-up (as needed)

**Post-Warranty Options:**
- Managed Services (ongoing HCL support)
- Retained Support (ad-hoc HCL assistance)
- Break-Fix Support (critical issues only)
- Fully Independent (Sydney Metro self-sufficient)

---

## Appendices

### Appendix A: Transition Checklists

**Pre-Cutover Checklist:** (See Section 2.2)

**Cutover Checklist:**
- [ ] Sitecore set to read-only mode
- [ ] Final data export completed
- [ ] Data transformed and validated
- [ ] Data imported to Strapi production
- [ ] Data integrity checks passed
- [ ] Application deployed to production
- [ ] DNS updated
- [ ] Smoke tests passed
- [ ] Extended testing passed
- [ ] Pilot user testing successful
- [ ] Go/No-Go decision: GO
- [ ] DNS switched to production
- [ ] Monitoring active
- [ ] Support team standing by

**Post-Cutover Checklist:**
- [ ] All users can log in successfully
- [ ] Content creation works
- [ ] Content publishing works
- [ ] Media upload works
- [ ] Multi-language content works
- [ ] API endpoints responding correctly
- [ ] Performance targets met
- [ ] No critical errors in logs
- [ ] Go-live announcement sent
- [ ] Post-cutover review completed

### Appendix B: Training Attendance Register

| Name | Role | Training Track | Date | Attendance | Assessment Score | Pass/Fail |
|------|------|----------------|------|------------|------------------|-----------|
| [User 1] | Content Editor | Track 1 | [Date] | ✓ | 85% | Pass |
| [User 2] | Content Editor | Track 1 | [Date] | ✓ | 90% | Pass |
| ... | ... | ... | ... | ... | ... | ... |

### Appendix C: Knowledge Transfer Log

| Session | Date | Trainer | Attendees | Topics Covered | Materials Provided | Sign-off |
|---------|------|---------|-----------|----------------|--------------------| ---------|
| System Architecture | [Date] | [HCL Lead] | [Names] | Architecture, components | Presentation, Diagrams | ✓ |
| ... | ... | ... | ... | ... | ... | ... |

### Appendix D: Hypercare Issue Log

| Issue ID | Date | Severity | Description | Reported By | Assigned To | Status | Resolution |
|----------|------|----------|-------------|-------------|-------------|--------|------------|
| HC-001 | [Date] | P2 | Image upload slow | [User] | [HCL Engineer] | Resolved | Optimized upload process |
| ... | ... | ... | ... | ... | ... | ... | ... |

### Appendix E: Contact Information

**HCL Transition Team:**
| Role | Name | Email | Phone | Availability |
|------|------|-------|-------|--------------|
| Transition Manager | [Name] | transition@hcl.com | [Phone] | Business hours |
| Hypercare Lead | [Name] | hypercare@hcl.com | [Phone] | 24/7 (Weeks 13-14) |
| Training Lead | [Name] | training@hcl.com | [Phone] | Business hours |
| Technical Lead | [Name] | technical@hcl.com | [Phone] | 24/7 (on-call) |

**Sydney Metro BAU Team:**
| Role | Name | Email | Phone | Availability |
|------|------|-------|-------|--------------|
| IT Operations Manager | [Name] | [Email] | [Phone] | Business hours |
| Application Support Lead | [Name] | [Email] | [Phone] | Business hours |
| System Administrator | [Name] | [Email] | [Phone] | Business hours |

**Escalation Contacts:**
| Level | Role | Contact | When to Escalate |
|-------|------|---------|------------------|
| L1 | HCL Transition Manager | [Contact] | Standard escalation |
| L2 | HCL Delivery Manager | [Contact] | Issues not resolved within SLA |
| L3 | Sydney Metro IT Director | [Contact] | Critical business impact |

---

**Document End**
