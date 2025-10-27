# Disaster Recovery and Business Continuity Plan
## Sydney Metro CMS Modernization Project

**Document Version:** 1.0
**Date:** October 2025
**Prepared by:** HCL Technologies
**Classification:** Commercial in Confidence

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | October 2025 | HCL DR/BC Team | Initial version |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [DR Strategy and Objectives](#2-dr-strategy-and-objectives)
3. [Multi-AZ Architecture](#3-multi-az-architecture)
4. [Backup Strategy](#4-backup-strategy)
5. [Recovery Procedures](#5-recovery-procedures)
6. [Failover Testing](#6-failover-testing)
7. [Business Continuity During Migration](#7-business-continuity-during-migration)
8. [Communication Plan During Incidents](#8-communication-plan-during-incidents)

---

## 1. Executive Summary

This Disaster Recovery (DR) and Business Continuity (BC) Plan establishes comprehensive strategies and procedures to ensure the Sydney Metro CMS remains available and recoverable in the event of system failures, disasters, or other disruptions. The plan ensures business continuity with minimal data loss and rapid recovery times.

### 1.1 DR/BC Objectives

1. **Minimize Downtime:** Achieve Recovery Time Objective (RTO) of ≤ 4 hours
2. **Minimize Data Loss:** Achieve Recovery Point Objective (RPO) of ≤ 1 hour
3. **Ensure Data Integrity:** Maintain data accuracy and completeness during recovery
4. **Business Continuity:** Enable continued business operations during and after incidents
5. **Rapid Recovery:** Restore full system functionality as quickly as possible
6. **Validated Procedures:** Ensure all DR procedures are tested and proven effective

### 1.2 Key Recovery Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| **RTO (Recovery Time Objective)** | ≤ 4 hours | Time from disaster declaration to system restored |
| **RPO (Recovery Point Objective)** | ≤ 1 hour | Maximum acceptable data loss (in time) |
| **MTTR (Mean Time To Restore)** | ≤ 2 hours | Average time to restore from backup |
| **Backup Success Rate** | 100% | Percentage of successful scheduled backups |
| **DR Test Success Rate** | 100% | Percentage of successful DR tests |
| **System Availability** | 99.9% uptime | Uptime excluding planned maintenance |

### 1.3 Disaster Scenarios Covered

This plan addresses the following disaster scenarios:

| Scenario | Impact | Likelihood | Recovery Strategy |
|----------|--------|------------|-------------------|
| **Single AZ Failure** | Partial service degradation | Medium | Automatic failover to healthy AZs |
| **Database Failure** | Full system outage | Low | RDS automatic failover to standby |
| **Data Corruption** | Partial data loss | Low | Point-in-time recovery from backups |
| **Application Failure** | Service disruption | Medium | Redeploy from last known good image |
| **Regional Failure (Sydney)** | Full system outage | Very Low | Manual recovery in same region (multi-AZ) |
| **Security Breach** | Potential data compromise | Low | Incident response, restore from clean backup |
| **Human Error** | Accidental deletion/modification | Medium | Point-in-time recovery from backups |
| **Ransomware Attack** | Data encryption/loss | Low | Restore from immutable backups |

### 1.4 Assumptions

- AWS Sydney region (ap-southeast-2) remains available
- Network connectivity to AWS is available
- DR team members are available and trained
- Backup data is intact and accessible
- Documentation and runbooks are current and accessible

---

## 2. DR Strategy and Objectives

### 2.1 DR Strategy Overview

**High Availability + Disaster Recovery Architecture:**

The DR strategy employs a multi-layered approach combining:

1. **High Availability (HA):** Multi-AZ deployment for automatic failover
2. **Automated Backups:** Daily automated backups with point-in-time recovery
3. **Infrastructure as Code:** Rapid infrastructure rebuild capability
4. **Immutable Infrastructure:** Clean redeployment from container images
5. **Data Replication:** Real-time database replication across availability zones

```
┌────────────────────────────────────────────────────────────────┐
│                    DR Strategy Layers                          │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Layer 1: High Availability (Multi-AZ)                        │
│  └─ Automatic failover, no data loss, seconds recovery        │
│                                                                │
│  Layer 2: Automated Backups                                   │
│  └─ Daily backups, point-in-time recovery, < 1 hour RPO       │
│                                                                │
│  Layer 3: Infrastructure as Code                              │
│  └─ Rapid rebuild from Terraform, < 2 hours RTO               │
│                                                                │
│  Layer 4: Regional DR (Same Region Multi-AZ)                  │
│  └─ Recovery within Sydney region, < 4 hours RTO              │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### 2.2 Recovery Time Objective (RTO)

**RTO Target: ≤ 4 hours**

**RTO by Scenario:**

| Disaster Scenario | RTO Target | Recovery Method |
|-------------------|------------|-----------------|
| **Single ECS Task Failure** | < 1 minute | Automatic ECS replacement |
| **Single Container Failure** | < 2 minutes | Automatic health check + restart |
| **AZ Failure (1 of 3 AZs)** | < 5 minutes | Automatic ALB routing to healthy AZs |
| **Database Primary Failure** | < 2 minutes | Automatic RDS failover to standby |
| **Application Code Bug** | < 30 minutes | Rollback to previous deployment |
| **Data Corruption (Partial)** | < 2 hours | Restore affected data from backup |
| **Complete System Failure** | < 4 hours | Full rebuild from IaC + restore data |
| **Security Incident** | < 4 hours | Isolate, clean, restore from clean backup |

### 2.3 Recovery Point Objective (RPO)

**RPO Target: ≤ 1 hour**

**RPO by Data Type:**

| Data Type | RPO Target | Protection Method |
|-----------|------------|-------------------|
| **Database (Content)** | < 1 hour | Continuous backup (RDS automated backups, point-in-time recovery) |
| **Media Files (S3)** | 0 (no data loss) | S3 versioning enabled, cross-AZ replication |
| **Application Code** | 0 (no data loss) | Git version control, container registry |
| **Infrastructure Config** | 0 (no data loss) | Terraform version control in Git |
| **User Sessions** | Acceptable loss | Session data in memory, users re-authenticate |

**RPO Achievement:**
- **Database:** RDS automated backups every 5 minutes (transaction logs)
- **Media Files:** S3 versioning captures every change immediately
- **Configuration:** Git commits provide version history
- **Worst Case:** Maximum 1 hour of database transactions could be lost (since last backup)

### 2.4 DR Team Roles and Responsibilities

**Disaster Recovery Team:**

| Role | Responsibilities | Primary Contact | Backup Contact |
|------|------------------|-----------------|----------------|
| **DR Coordinator** | Overall DR coordination, decision-making, communication | [HCL Project Manager] | [Sydney Metro IT Manager] |
| **Infrastructure Lead** | AWS infrastructure recovery, network restoration | [HCL DevOps Lead] | [HCL DevOps Engineer] |
| **Database Lead** | Database recovery, data validation | [HCL Database Engineer] | [HCL Senior Developer] |
| **Application Lead** | Application deployment, configuration | [HCL Technical Lead] | [HCL Developer] |
| **QA Lead** | Post-recovery validation testing | [HCL QA Lead] | [HCL QA Engineer] |
| **Communications Lead** | Stakeholder communication, status updates | [HCL Communications Manager] | [Sydney Metro Communications] |
| **Security Lead** | Security validation, access restoration | [HCL Security Lead] | [Sydney Metro Security] |

**DR Team Activation:**
- **Trigger:** DR Coordinator declares disaster event
- **Notification:** All team members alerted via phone, SMS, email, PagerDuty
- **Assembly:** Team joins dedicated conference bridge and Slack channel
- **Coordination:** War room established (virtual or physical)

### 2.5 DR Activation Criteria

**When to Activate DR:**

**Automatic Activation (by monitoring systems):**
- Complete system outage (all health checks failing) for > 5 minutes
- Database unavailable for > 2 minutes (after automatic failover attempts)
- Multiple AZs simultaneously unavailable

**Manual Activation (by DR Coordinator):**
- Widespread data corruption detected
- Security incident requiring system isolation and rebuild
- Regional AWS outage declared
- Prolonged degraded performance affecting business operations

**DR Activation Decision Tree:**

```
Is the system completely unavailable?
├─ Yes → Activate DR immediately
└─ No → Is there data corruption or security breach?
    ├─ Yes → Activate DR immediately
    └─ No → Is performance severely degraded?
        ├─ Yes → Consider DR activation (evaluate business impact)
        └─ No → Follow standard incident response (not DR)
```

---

## 3. Multi-AZ Architecture

### 3.1 High Availability Architecture

**Multi-AZ Deployment:**

The CMS is deployed across three Availability Zones (AZs) in the AWS Sydney region for maximum resilience:

```
┌─────────────────────────────────────────────────────────────────┐
│              AWS Sydney Region (ap-southeast-2)                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌───────────────────┐  ┌───────────────────┐  ┌──────────────┐│
│  │ AZ-2a (Primary)   │  │ AZ-2b (Secondary) │  │ AZ-2c (Tertiary)││
│  ├───────────────────┤  ├───────────────────┤  ├──────────────┤│
│  │ - ALB (Active)    │  │ - ALB (Active)    │  │ - ALB (Active)││
│  │ - ECS Tasks (2)   │  │ - ECS Tasks (2)   │  │ - ECS Tasks (2)││
│  │ - RDS Primary     │  │ - RDS Standby     │  │              ││
│  │ - NAT Gateway     │  │ - NAT Gateway     │  │ - NAT Gateway││
│  └───────────────────┘  └───────────────────┘  └──────────────┘│
│                                                                 │
│  ┌─────────────────────────────────────────────────────────────┤
│  │ S3 (Sydney Region) - Automatically multi-AZ replicated      ││
│  │ CloudFront - Global edge locations + Sydney origin          ││
│  └─────────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────────┘
```

**Component Availability:**

| Component | Availability Model | Failover Mechanism | RTO |
|-----------|--------------------|--------------------|-----|
| **Application Load Balancer** | Multi-AZ (all AZs) | Automatic traffic routing to healthy AZs | < 1 minute |
| **ECS Fargate Tasks** | Distributed across 3 AZs (2 tasks per AZ = 6 total) | ECS auto-replacement of failed tasks | < 2 minutes |
| **RDS PostgreSQL** | Multi-AZ (Primary in AZ-2a, Standby in AZ-2b) | Automatic failover to standby | < 2 minutes |
| **S3 Storage** | Multi-AZ by default (AWS managed) | No failover needed, always available | N/A |
| **CloudFront CDN** | Global multi-region (AWS managed) | Automatic edge failover | < 1 minute |
| **NAT Gateway** | One per AZ (3 total) | Route to different NAT if one AZ fails | < 1 minute |

### 3.2 Automatic Failover Mechanisms

**Application Layer Failover:**

1. **Load Balancer Health Checks:**
   - **Frequency:** Every 30 seconds
   - **Threshold:** 2 consecutive failures = unhealthy
   - **Action:** Stop routing traffic to unhealthy target
   - **Recovery:** 3 consecutive successes = healthy, resume traffic

2. **ECS Task Failure:**
   - **Detection:** Health check failure or container crash
   - **Action:** ECS automatically launches replacement task in healthy AZ
   - **Time:** New task running within 1-2 minutes

3. **AZ Failure:**
   - **Detection:** All tasks in one AZ unhealthy
   - **Action:** ALB routes 100% traffic to remaining healthy AZs
   - **Capacity:** Remaining AZs handle full load (over-provisioned by 50%)
   - **Recovery:** When AZ restored, gradually shift traffic back

**Database Layer Failover:**

1. **RDS Multi-AZ Automatic Failover:**
   - **Primary Failure Detection:** RDS monitors primary instance
   - **Failover Trigger:** Primary unresponsive, AZ failure, storage failure
   - **Failover Process:**
     1. RDS detects primary failure (< 1 minute)
     2. RDS promotes standby to primary (< 1 minute)
     3. RDS updates DNS to point to new primary (automatic)
     4. Applications reconnect to new primary (< 30 seconds)
   - **Total Failover Time:** < 2 minutes
   - **Data Loss:** Zero (synchronous replication to standby)

2. **Connection Handling:**
   - Application uses connection pooling with automatic retry
   - Transient connection errors handled gracefully
   - Users may experience brief delay (< 30 seconds) but no data loss

**Storage Layer Resilience:**

1. **S3 Multi-AZ Replication:**
   - S3 automatically replicates objects across multiple AZs
   - 99.999999999% (11 nines) durability
   - No manual failover required

2. **S3 Versioning:**
   - Every object change creates new version
   - Accidental deletion/overwrite can be reversed
   - 90-day version retention

**CDN Layer Resilience:**

1. **CloudFront Failover:**
   - CloudFront automatically routes to healthy origin
   - Multiple origin setup (if configured)
   - Edge location failure transparent to users

### 3.3 Capacity Planning for Failover

**Over-Provisioning for AZ Failure:**

Normal State (3 AZs):
- 6 ECS tasks total (2 per AZ)
- Each task handles ~85 concurrent users
- Total capacity: 510 concurrent users

AZ Failure State (2 AZs):
- 4 ECS tasks remaining (2 per AZ)
- Total capacity: 340 concurrent users
- Still exceeds peak usage of 500 concurrent users with auto-scaling

**Auto-Scaling During Failure:**
- ECS auto-scaling triggers when CPU > 70%
- Additional tasks launched in healthy AZs
- Scale from 4 to 6+ tasks within 3-5 minutes
- Ensures no performance degradation during AZ failure

### 3.4 Testing Multi-AZ Resilience

**Chaos Engineering Tests:**

**Monthly AZ Failure Simulation:**
1. Disable one AZ's ECS tasks during business hours
2. Verify traffic automatically routes to other AZs
3. Monitor user experience (expect no impact)
4. Verify auto-scaling compensates for reduced capacity
5. Re-enable AZ, verify traffic rebalances

**Quarterly Database Failover Test:**
1. Trigger manual RDS failover (non-production, then production during maintenance)
2. Measure failover time (target < 2 minutes)
3. Verify application reconnects automatically
4. Verify zero data loss
5. Document results and any improvements needed

---

## 4. Backup Strategy

### 4.1 Backup Strategy Overview

**Comprehensive Backup Approach:**

```
┌────────────────────────────────────────────────────────────┐
│                    Backup Strategy                          │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  Database Backups:                                         │
│  ├─ Automated daily snapshots (35-day retention)          │
│  ├─ Continuous transaction log backups (point-in-time)    │
│  └─ Monthly full backups (7-year retention)               │
│                                                            │
│  Media File Backups:                                       │
│  ├─ S3 versioning (90-day version retention)              │
│  ├─ Cross-AZ replication (automatic)                      │
│  └─ Optional: Cross-region replication for DR             │
│                                                            │
│  Configuration Backups:                                    │
│  ├─ Terraform state in S3 with versioning                 │
│  ├─ Application config in Git                             │
│  └─ Secrets in AWS Secrets Manager (versioned)            │
│                                                            │
│  Application Code:                                         │
│  ├─ Git repository (GitHub)                               │
│  └─ Container images in ECR (tagged versions)             │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

### 4.2 Database Backup Strategy

**RDS Automated Backups:**

| Backup Type | Frequency | Retention | Storage Location |
|-------------|-----------|-----------|------------------|
| **Automated Snapshots** | Daily (3:00 AM AEST) | 35 days | S3 (Sydney region, encrypted) |
| **Transaction Logs** | Continuous (every 5 min) | 35 days | S3 (Sydney region, encrypted) |
| **Manual Snapshots** | On-demand (before major changes) | Indefinite (until deleted) | S3 (Sydney region, encrypted) |
| **Monthly Archives** | 1st of each month | 7 years | S3 Glacier (Sydney region) |

**Backup Process:**

1. **Daily Automated Backup (3:00 AM AEST):**
   - RDS automatically takes snapshot of entire database
   - Minimal performance impact (using storage-level snapshots)
   - Incremental after first full snapshot (efficient storage)
   - Encrypted using AWS KMS

2. **Continuous Transaction Log Backup:**
   - RDS continuously backs up transaction logs (every 5 minutes)
   - Enables point-in-time recovery (restore to any time within 35 days)
   - RPO of 5 minutes achievable

3. **Manual Snapshots (Pre-Change):**
   - Before major deployments or database changes
   - Provides rollback point if change causes issues
   - Retained indefinitely (deleted after validation of change)

4. **Monthly Archive to Glacier:**
   - First snapshot of each month copied to S3 Glacier
   - Long-term retention for compliance (7 years)
   - Lower storage cost for infrequently accessed backups

**Backup Encryption:**
- All backups encrypted with AES-256
- Encryption keys managed by AWS KMS
- Keys automatically rotated annually
- Access to backups requires IAM permissions + KMS key access

**Backup Validation:**

| Validation Type | Frequency | Method | Success Criteria |
|-----------------|-----------|--------|------------------|
| **Automated Validation** | Daily | Verify backup completed successfully, check backup size | Backup exists, size within expected range |
| **Restore Test** | Monthly | Restore backup to test environment | Database restored, data queryable |
| **Full DR Test** | Quarterly | Full restore to production-like environment | Complete system functional |
| **Point-in-Time Recovery Test** | Quarterly | Restore to specific point in time | Data matches expected state at that time |

### 4.3 Media File Backup Strategy

**S3 Versioning and Lifecycle:**

| Feature | Configuration | Purpose |
|---------|---------------|---------|
| **S3 Versioning** | Enabled | Retain all versions of files for 90 days |
| **Cross-AZ Replication** | Automatic (S3 default) | Protect against AZ failure |
| **Lifecycle Policy** | Non-current versions → Delete after 90 days | Balance retention and storage cost |
| **MFA Delete** | Enabled | Require MFA to permanently delete versions |

**Media Backup Process:**

1. **Automatic Versioning:**
   - Every file upload/modification creates new version
   - Old versions retained for 90 days
   - Can restore previous version if needed

2. **Accidental Deletion Protection:**
   - Deleted files retained as "delete marker"
   - Can be restored within 90 days by removing delete marker
   - MFA required to permanently delete (prevent ransomware)

3. **Cross-Region Replication (Optional):**
   - For critical media, can enable replication to another AWS region
   - Provides DR capability if entire Sydney region unavailable
   - Additional cost, evaluate necessity

**Media Backup Validation:**
- Automated S3 inventory reports (weekly)
- Verify object counts match expected
- Periodically test restoring deleted files

### 4.4 Configuration and Code Backups

**Infrastructure as Code (Terraform):**

| Backup Element | Storage Location | Versioning | Retention |
|----------------|------------------|------------|-----------|
| **Terraform Code** | GitHub private repository | Git version control | Indefinite |
| **Terraform State** | S3 bucket with versioning | S3 versioning enabled | All versions retained |
| **Terraform State Lock** | DynamoDB table | N/A | N/A |

**Application Code:**

| Backup Element | Storage Location | Versioning | Retention |
|----------------|------------------|------------|-----------|
| **Application Code** | GitHub private repository | Git version control | Indefinite |
| **Container Images** | AWS ECR | Tagged versions | Last 10 versions per image |
| **Build Artifacts** | S3 bucket | Versioned | 6 months |

**Application Configuration:**

| Backup Element | Storage Location | Versioning | Retention |
|----------------|------------------|------------|-----------|
| **Environment Variables** | AWS Systems Manager Parameter Store | Versioned | All versions retained |
| **Secrets** | AWS Secrets Manager | Versioned | All versions retained |
| **Strapi Config** | Git repository + S3 backup | Git + S3 versioning | Indefinite |

**Backup Process:**
- All code changes committed to Git (enforced via branch protection)
- CI/CD pipeline automatically builds and tags container images
- Terraform state automatically backed up to S3 after every apply
- Secrets versioned automatically by AWS Secrets Manager

### 4.5 Backup Retention Policy

**Retention Summary:**

| Data Type | Daily | Weekly | Monthly | Yearly | Long-Term |
|-----------|-------|--------|---------|--------|-----------|
| **Database** | 35 days | N/A | 7 years | N/A | N/A |
| **Media Files** | 90 days (versions) | N/A | N/A | N/A | N/A |
| **Application Code** | Indefinite (Git) | N/A | N/A | N/A | N/A |
| **Infrastructure Config** | Indefinite (Git) | N/A | N/A | N/A | N/A |
| **Audit Logs** | 7 years | N/A | N/A | N/A | N/A |

**Retention Rationale:**
- **35 days database backups:** Balance between recovery flexibility and storage cost
- **7 years monthly archives:** Compliance with government record retention requirements
- **90 days media versions:** Sufficient for accidental deletion recovery
- **Indefinite code retention:** Enables rollback to any previous version
- **7 years audit logs:** Compliance with security and audit requirements

### 4.6 Backup Monitoring and Alerting

**Backup Monitoring:**

| Metric | Threshold | Alert | Action |
|--------|-----------|-------|--------|
| **Backup Success Rate** | < 100% | Critical alert | Investigate failed backup immediately |
| **Backup Size Variance** | > 50% change | Warning | Verify data integrity, investigate anomaly |
| **Backup Duration** | > 2 hours | Warning | Optimize backup process |
| **Backup Age** | Oldest backup > 36 hours | Critical alert | Trigger manual backup |
| **S3 Object Count** | Unexpected drop | Critical alert | Investigate potential data loss |

**Alerts Sent To:**
- CloudWatch Alarms → SNS Topic → Email + PagerDuty
- DevOps team receives immediate notification
- Daily backup summary report emailed to operations team

**Backup Dashboard:**
- Real-time backup status in Grafana
- Last successful backup timestamp
- Backup size trends
- Backup duration trends
- Failed backup alerts

---

## 5. Recovery Procedures

### 5.1 Recovery Procedure Overview

**Recovery Scenarios and Procedures:**

| Scenario | Procedure | Estimated RTO | Estimated RPO |
|----------|-----------|---------------|---------------|
| **Single ECS Task Failure** | 5.2.1 | < 2 minutes | 0 (no data loss) |
| **Database Failure (Multi-AZ Failover)** | 5.2.2 | < 2 minutes | 0 (no data loss) |
| **Application Code Issue** | 5.2.3 | < 30 minutes | 0 (no data loss) |
| **Database Corruption** | 5.3 | < 2 hours | < 1 hour |
| **Accidental Data Deletion** | 5.4 | < 1 hour | < 5 minutes |
| **Complete System Failure** | 5.5 | < 4 hours | < 1 hour |
| **Security Incident (Compromise)** | 5.6 | < 4 hours | < 1 hour |

### 5.2 High Availability Recovery (Automatic)

**5.2.1 ECS Task Failure Recovery (Automatic)**

**Scenario:** One or more ECS tasks fail or become unhealthy.

**Automatic Recovery Process:**
1. ECS health check detects unhealthy task (within 30 seconds)
2. ALB stops routing traffic to unhealthy task (immediately)
3. ECS stops unhealthy task and launches replacement (within 1 minute)
4. New task passes health check (within 1 minute)
5. ALB resumes routing traffic to new healthy task
6. **Total Time:** < 2 minutes
7. **User Impact:** None (other tasks handle traffic)

**Manual Intervention (if needed):**
- If tasks repeatedly fail: Investigate application logs (CloudWatch)
- If deployment issue: Rollback to previous task definition
- If resource issue: Check CPU/memory limits, scale up if needed

**5.2.2 Database Multi-AZ Failover (Automatic)**

**Scenario:** RDS primary database instance fails.

**Automatic Recovery Process:**
1. RDS detects primary failure (< 1 minute)
   - Database unresponsive
   - AZ failure
   - Storage failure
2. RDS promotes standby to primary (< 1 minute)
   - Standby (in AZ-2b) promoted to primary
   - DNS updated to point to new primary
3. Applications reconnect to new primary (< 30 seconds)
   - Connection pool retries failed connections
   - New connections succeed to new primary
4. RDS creates new standby in different AZ (background, 5-10 minutes)
5. **Total Time:** < 2 minutes
6. **Data Loss:** Zero (synchronous replication)
7. **User Impact:** Brief connection errors (< 30 seconds), automatic retry

**Manual Monitoring:**
- Monitor RDS events in AWS Console
- Verify new primary is functioning correctly
- Check application error logs for connection issues
- Confirm new standby is created

**5.2.3 Application Code Rollback (Manual)**

**Scenario:** New deployment causes issues (bugs, performance degradation).

**Rollback Procedure:**
1. **Identify Issue:** (0-10 minutes)
   - Monitoring alerts (error rate increase, latency increase)
   - User reports
   - QA validation failure

2. **Make Rollback Decision:** (10-15 minutes)
   - Incident commander decides to rollback
   - Notify stakeholders

3. **Execute Rollback:** (15-25 minutes)
   ```bash
   # Identify previous working version
   aws ecs describe-services --cluster cms-production --services cms-service

   # Update service to previous task definition revision
   aws ecs update-service \
     --cluster cms-production \
     --service cms-service \
     --task-definition cms-task:previous-revision

   # Monitor deployment
   aws ecs wait services-stable --cluster cms-production --services cms-service
   ```

4. **Validate Rollback:** (25-30 minutes)
   - Smoke test critical functionality
   - Monitor error rates return to normal
   - Confirm performance back to baseline

5. **Post-Rollback:**
   - Incident report
   - Root cause analysis
   - Fix issue in code before re-deploying

**Rollback Time:** < 30 minutes
**Data Loss:** None

### 5.3 Point-in-Time Database Recovery

**Scenario:** Database data corruption detected (e.g., accidental mass deletion, bad data migration).

**Recovery Procedure:**

**Step 1: Identify Corruption and Recovery Point (0-30 minutes)**
1. Identify what data is corrupted
2. Determine when corruption occurred (query audit logs)
3. Identify last good state (time before corruption)
4. Decision: Full restore vs. partial restore
   - If limited scope: Restore specific tables (faster, lower impact)
   - If widespread: Full database restore

**Step 2: Prepare for Recovery (30-45 minutes)**
1. **Alert stakeholders:** System will be in read-only mode or offline
2. **Take snapshot of current state:** (for forensics)
   ```bash
   aws rds create-db-snapshot \
     --db-instance-identifier cms-production-db \
     --db-snapshot-identifier cms-prod-corrupted-$(date +%Y%m%d-%H%M%S)
   ```
3. **Set application to read-only mode or maintenance mode**
   ```bash
   # Update ECS task with MAINTENANCE_MODE=true environment variable
   ```

**Step 3: Restore Database (45-90 minutes)**

**Option A: Point-in-Time Restore to New Instance (Full Restore)**
```bash
# Restore to new RDS instance from automated backup
aws rds restore-db-instance-to-point-in-time \
  --source-db-instance-identifier cms-production-db \
  --target-db-instance-identifier cms-production-db-restored \
  --restore-time 2025-10-27T08:30:00Z \
  --db-subnet-group-name cms-db-subnet-group \
  --vpc-security-group-ids sg-xxxxx \
  --multi-az

# Wait for restore to complete (30-60 minutes depending on database size)
aws rds wait db-instance-available --db-instance-identifier cms-production-db-restored
```

**Option B: Restore Specific Tables (Partial Restore)**
```bash
# Restore to temporary instance
aws rds restore-db-instance-to-point-in-time \
  --source-db-instance-identifier cms-production-db \
  --target-db-instance-identifier cms-temp-restore \
  --restore-time 2025-10-27T08:30:00Z

# Wait for restore, then dump specific tables
pg_dump -h cms-temp-restore.xxxxx.rds.amazonaws.com \
  -U admin -d strapi \
  -t content_table -t metadata_table \
  > specific_tables.sql

# Restore tables to production
psql -h cms-production-db.xxxxx.rds.amazonaws.com \
  -U admin -d strapi \
  -f specific_tables.sql
```

**Step 4: Validate Restored Data (90-110 minutes)**
1. **Connect to restored database:** Verify data integrity
   ```sql
   -- Check record counts
   SELECT COUNT(*) FROM content_table;

   -- Verify recent content exists
   SELECT * FROM content_table WHERE created_at > '2025-10-27 08:00:00';

   -- Check user accounts
   SELECT COUNT(*) FROM users;
   ```

2. **Run data validation scripts:**
   - Foreign key integrity checks
   - Content completeness checks
   - User permissions validation

3. **QA testing:**
   - Test critical user journeys
   - Verify content publishing works
   - Check media file access

**Step 5: Swap to Restored Database (110-120 minutes)**

**If Full Restore:**
```bash
# Rename current production DB to old
aws rds modify-db-instance \
  --db-instance-identifier cms-production-db \
  --new-db-instance-identifier cms-production-db-old \
  --apply-immediately

# Rename restored DB to production
aws rds modify-db-instance \
  --db-instance-identifier cms-production-db-restored \
  --new-db-instance-identifier cms-production-db \
  --apply-immediately

# Update application connection string (if needed)
# Restart ECS tasks to reconnect
aws ecs update-service --cluster cms-production --service cms-service --force-new-deployment
```

**If Partial Restore:**
- No swap needed, tables already restored to production

**Step 6: Resume Operations (120 minutes)**
1. Remove maintenance mode
2. Resume normal operations
3. Monitor for issues
4. Notify users system is back to normal

**Total RTO:** < 2 hours
**RPO:** < 1 hour (depends on when corruption occurred)

### 5.4 Accidental Deletion Recovery

**Scenario:** Content or media files accidentally deleted.

**5.4.1 Content (Database) Recovery**

**If Recent (within last 1 hour):**
1. Identify deleted content ID and deletion time (from audit logs)
2. Use point-in-time recovery to restore database to just before deletion
3. Export deleted content from restored database
4. Import deleted content back to production database
5. **Time:** < 30 minutes
6. **RPO:** < 5 minutes

**If Older (within last 35 days):**
1. Restore daily snapshot from before deletion
2. Extract deleted content
3. Merge back to production
4. **Time:** < 1 hour
5. **RPO:** Up to 24 hours (depending on when deletion occurred relative to last backup)

**5.4.2 Media File (S3) Recovery**

**S3 Versioning Recovery:**
```bash
# List all versions of deleted object
aws s3api list-object-versions \
  --bucket cms-media-production \
  --prefix path/to/deleted-file.jpg

# Identify version ID of file before deletion

# Remove delete marker to restore file
aws s3api delete-object \
  --bucket cms-media-production \
  --key path/to/deleted-file.jpg \
  --version-id <delete-marker-version-id>

# File is now restored
```

**Time:** < 5 minutes
**RPO:** 0 (S3 versioning captures every change)

**Bulk Deletion Recovery:**
- If many files deleted, can restore all versions using script
- S3 Batch Operations can restore large number of files
- **Time:** 10-30 minutes depending on volume

### 5.5 Complete System Failure Recovery

**Scenario:** Complete system outage (all components failed, multi-AZ failure).

**Recovery Procedure:**

**Phase 1: Assessment and Preparation (0-30 minutes)**

1. **Declare Disaster:** DR Coordinator activates DR team
2. **Assemble DR Team:** Conference bridge + Slack war room
3. **Assess Damage:**
   - What components are affected?
   - What is root cause? (AWS outage, application bug, security breach)
   - What is scope? (single AZ, multiple AZs, region)
4. **Identify Recovery Strategy:**
   - Can we failover within existing infrastructure?
   - Do we need to rebuild infrastructure?
   - What is recovery point (which backup to restore)?

**Phase 2: Infrastructure Rebuild (30-120 minutes)**

**If Infrastructure Intact (just application issue):**
```bash
# Rollback to last known good deployment
aws ecs update-service \
  --cluster cms-production \
  --service cms-service \
  --task-definition cms-task:last-good-revision

# Monitor deployment
aws ecs wait services-stable --cluster cms-production --services cms-service
```
**Time:** 15-30 minutes

**If Infrastructure Needs Rebuild:**
```bash
# Clone infrastructure repository
git clone https://github.com/hcl/sydney-metro-cms-infra.git
cd sydney-metro-cms-infra

# Initialize Terraform
terraform init

# Review existing resources (if any)
terraform plan

# Destroy compromised resources (if needed)
terraform destroy -target=aws_ecs_service.cms
terraform destroy -target=aws_ecs_cluster.cms

# Rebuild infrastructure
terraform apply

# Deploy application
aws ecs update-service --cluster cms-production --service cms-service --force-new-deployment
```
**Time:** 60-90 minutes

**Phase 3: Database Recovery (120-180 minutes)**

**Option A: RDS Instance Intact, Just Restore Data**
```bash
# Point-in-time restore (see Section 5.3)
```
**Time:** 30-60 minutes

**Option B: RDS Instance Destroyed, Restore from Snapshot**
```bash
# Restore from latest automated snapshot
aws rds restore-db-instance-from-db-snapshot \
  --db-instance-identifier cms-production-db \
  --db-snapshot-identifier cms-prod-automated-2025-10-27 \
  --db-subnet-group-name cms-db-subnet-group \
  --vpc-security-group-ids sg-xxxxx \
  --multi-az

# Wait for restore (30-60 minutes)
aws rds wait db-instance-available --db-instance-identifier cms-production-db

# Update application connection strings
aws secretsmanager update-secret \
  --secret-id cms/database/connection \
  --secret-string '{"host":"cms-production-db.xxxxx.rds.amazonaws.com",...}'

# Restart application to pick up new connection
aws ecs update-service --cluster cms-production --service cms-service --force-new-deployment
```
**Time:** 60-90 minutes

**Phase 4: Application Configuration (180-210 minutes)**

1. **Restore Application Configuration:**
   ```bash
   # Restore Strapi configuration from Git
   git checkout production

   # Apply configuration to ECS task environment variables
   aws ecs register-task-definition --cli-input-json file://task-definition.json

   # Update service
   aws ecs update-service \
     --cluster cms-production \
     --service cms-service \
     --task-definition cms-task:latest
   ```

2. **Restore Secrets:**
   - Secrets already in AWS Secrets Manager (versioned)
   - If Secrets Manager also compromised, restore from backup

3. **Configure Monitoring and Alerting:**
   - CloudWatch alarms (defined in Terraform, already restored)
   - Grafana dashboards (restore from Git)

**Phase 5: Validation and Testing (210-240 minutes)**

1. **Smoke Tests:**
   - Application loads
   - Login works (Azure AD OIDC)
   - Content displays
   - Media files accessible
   - API endpoints responding

2. **Critical User Journeys:**
   - Create content
   - Edit content
   - Publish content
   - Approve content
   - Upload media

3. **Data Validation:**
   - Query database for expected record counts
   - Verify recent content exists
   - Check user accounts
   - Validate media files

4. **Performance Validation:**
   - Page load times < 2 seconds
   - API response times < 500ms
   - No unusual errors in logs

**Phase 6: Resume Operations (240 minutes = 4 hours)**

1. **Remove Maintenance Mode:** System back online
2. **Notify Users:** System recovered, normal operations resumed
3. **Monitor Closely:** Watch for any issues in first 24 hours
4. **Document Recovery:** Detailed incident report

**Total RTO:** < 4 hours
**RPO:** < 1 hour

### 5.6 Security Incident Recovery

**Scenario:** Security breach, ransomware, compromised credentials.

**Recovery Procedure:**

**Phase 1: Isolation (0-15 minutes)**
1. **Isolate Affected Systems:**
   ```bash
   # Block all inbound traffic to affected resources
   aws ec2 revoke-security-group-ingress \
     --group-id sg-affected \
     --ip-permissions '[{"IpProtocol": "-1", "IpRanges": [{"CidrIp": "0.0.0.0/0"}]}]'

   # Take snapshot of affected instance for forensics
   aws ec2 create-snapshot --volume-id vol-affected --description "Forensic snapshot"
   ```

2. **Revoke Compromised Credentials:**
   - Disable compromised user accounts (Azure AD)
   - Rotate all secrets (database passwords, API keys)
   - Revoke AWS IAM credentials if compromised

**Phase 2: Assessment (15-60 minutes)**
1. **Forensic Analysis:**
   - What was compromised?
   - When did compromise occur?
   - What data was accessed/exfiltrated?
   - Are backups also compromised?

2. **Identify Clean Recovery Point:**
   - Find last known clean backup (before compromise)
   - Verify backup integrity

**Phase 3: Clean Rebuild (60-180 minutes)**
1. **Destroy Compromised Infrastructure:**
   ```bash
   terraform destroy
   ```

2. **Rebuild from Clean State:**
   - Use Infrastructure as Code (Terraform) to rebuild
   - Deploy application from clean container images (verified)
   - Restore database from clean backup (before compromise)
   - Restore media files from clean backup (if affected)

3. **Apply Security Patches:**
   - Update all packages
   - Apply security fixes
   - Harden configuration

**Phase 4: Restore Operations (180-240 minutes)**
1. Restore data from clean backup
2. Validate system integrity
3. Re-enable user access (with new credentials)
4. Resume operations

**Phase 5: Post-Incident (after recovery)**
1. **Incident Report:** Detailed writeup for Sydney Metro
2. **Notify Affected Parties:** If personal data compromised, notify per Privacy Act
3. **Improve Security:** Implement additional controls to prevent recurrence
4. **Lessons Learned:** Update incident response procedures

**Total RTO:** < 4 hours (may be longer depending on severity)
**RPO:** < 1 hour (may lose data since last clean backup)

---

## 6. Failover Testing

### 6.1 Failover Testing Strategy

**Testing Objectives:**
1. Validate that failover mechanisms work as designed
2. Measure actual RTO and RPO
3. Identify gaps in procedures
4. Train DR team
5. Build confidence in DR capabilities

**Testing Frequency:**

| Test Type | Frequency | Scope | RTO Target |
|-----------|-----------|-------|------------|
| **Component Failover Test** | Monthly | Single component (ECS task, database) | < 2 minutes |
| **AZ Failover Test** | Quarterly | Single AZ failure simulation | < 5 minutes |
| **Full DR Test** | Semi-annually | Complete system recovery | < 4 hours |
| **Tabletop Exercise** | Quarterly | Discussion-based scenario walkthrough | N/A |

### 6.2 Monthly Component Failover Tests

**6.2.1 ECS Task Failure Test**

**Procedure:**
1. Identify one ECS task in production
2. Manually stop the task
   ```bash
   aws ecs stop-task --cluster cms-production --task <task-arn>
   ```
3. Monitor:
   - Time for ECS to detect failure
   - Time to launch replacement task
   - Time for replacement to be healthy
   - ALB routing behavior (should route to other tasks)
4. Measure total recovery time
5. Verify no user impact (check error logs, user reports)

**Expected Result:** Task replaced within 2 minutes, no user impact

**6.2.2 Database Failover Test**

**Procedure:**
1. Schedule during low-traffic window (if testing in production) or use pre-production
2. Trigger manual RDS failover
   ```bash
   aws rds reboot-db-instance \
     --db-instance-identifier cms-production-db \
     --force-failover
   ```
3. Monitor:
   - Time for RDS to detect and failover
   - Application connection errors (should retry and reconnect)
   - User-visible impact
4. Measure:
   - Total failover time
   - Number of failed requests
   - Data loss (should be zero)

**Expected Result:** Failover within 2 minutes, zero data loss, brief connection errors

### 6.3 Quarterly AZ Failover Test

**Test Procedure:**

**Preparation (Day 0):**
1. Schedule test during business hours (to validate user experience)
2. Notify stakeholders (this is a test, may see brief degradation)
3. Prepare monitoring dashboards
4. Assemble DR team (observers)

**Execution (Day 1, 10:00 AM):**
1. **Simulate AZ-2a Failure:**
   ```bash
   # Stop all ECS tasks in AZ-2a
   for task in $(aws ecs list-tasks --cluster cms-production --query 'taskArns[*]' --output text); do
     # Check if task is in AZ-2a (check subnet)
     SUBNET=$(aws ecs describe-tasks --cluster cms-production --tasks $task \
       --query 'tasks[0].attachments[0].details[?name==`subnetId`].value' --output text)

     if [ "$SUBNET" == "subnet-az2a" ]; then
       aws ecs stop-task --cluster cms-production --task $task
     fi
   done

   # Block traffic to AZ-2a at security group level
   aws ec2 revoke-security-group-ingress \
     --group-id sg-ecs-tasks \
     --source-group sg-alb \
     --ip-permissions '[...]' \
     --subnet-ids subnet-az2a
   ```

2. **Monitor:**
   - ALB routes traffic to AZ-2b and AZ-2c (should be immediate)
   - ECS launches replacement tasks in healthy AZs (1-2 minutes)
   - User experience (monitor error rates, response times)
   - Auto-scaling (should trigger to compensate)

3. **Measure:**
   - Time to full recovery (all traffic routed to healthy AZs)
   - User-visible impact (error rate, latency increase)
   - Auto-scaling response time

4. **Restore AZ-2a (after 30 minutes):**
   ```bash
   # Re-enable traffic to AZ-2a
   # ECS will gradually launch tasks back in AZ-2a
   # ALB will gradually resume routing to AZ-2a
   ```

5. **Validate Return to Normal:**
   - Tasks running in all 3 AZs
   - Traffic evenly distributed
   - No errors

**Expected Results:**
- Traffic immediately routes to healthy AZs (< 1 minute)
- Auto-scaling compensates for lost capacity (< 5 minutes)
- User impact: minimal (< 5% error rate increase for < 1 minute)

**Post-Test Review:**
- Document results
- Identify any issues or gaps
- Update procedures if needed

### 6.4 Semi-Annual Full DR Test

**Full DR Test Procedure:**

**Preparation (Week before test):**
1. Schedule DR test day (typically Saturday, low traffic)
2. Notify all stakeholders
3. Assemble full DR team
4. Review DR procedures
5. Prepare test environment (use pre-production or isolated production)
6. Define success criteria

**Test Day (Saturday, 8:00 AM - 5:00 PM):**

**Scenario: Complete System Failure**

**8:00 AM - Simulate Disaster:**
1. Declare simulated disaster (e.g., "entire production environment compromised")
2. "Destroy" production environment (actually just isolate/disable, don't actually destroy)
   ```bash
   # Set ECS desired count to 0 (stop all tasks)
   aws ecs update-service --cluster cms-production --service cms-service --desired-count 0

   # Rename production RDS instance (simulate loss)
   aws rds modify-db-instance \
     --db-instance-identifier cms-production-db \
     --new-db-instance-identifier cms-production-db-disaster-test
   ```

**8:15 AM - Activate DR Team:**
1. DR Coordinator activates DR team (phone calls, PagerDuty)
2. Team assembles on conference bridge and Slack war room
3. Begin following DR procedures (Section 5.5)

**8:30 AM - 11:30 AM - Execute Recovery:**
1. **Infrastructure Rebuild:**
   - Use Terraform to rebuild infrastructure
   - Deploy application containers
   - Configure networking

2. **Database Recovery:**
   - Restore RDS from latest snapshot
   - Validate data integrity

3. **Application Configuration:**
   - Restore configuration from Git
   - Apply secrets from Secrets Manager

4. **Validation:**
   - Smoke tests
   - Critical user journeys
   - Performance validation

**11:30 AM - 12:00 PM - Declare Recovery Complete:**
1. System fully functional
2. Measure actual RTO (should be < 4 hours)
3. Measure RPO (check data currency)

**12:00 PM - 2:00 PM - Extended Monitoring:**
1. Monitor recovered system for stability
2. Simulate user traffic (load testing)
3. Verify performance matches baseline

**2:00 PM - 3:00 PM - Restore Production:**
1. Shutdown DR test environment
2. Restore actual production environment (reverse simulation)
3. Verify production back to normal

**3:00 PM - 5:00 PM - Post-Test Review:**
1. Review DR test results
   - What went well?
   - What went wrong?
   - RTO achieved? RPO achieved?
2. Document lessons learned
3. Update DR procedures
4. Create action items for improvements

**Success Criteria:**
- [ ] DR team activated within 15 minutes
- [ ] Infrastructure rebuilt within 2 hours
- [ ] Database restored within 1 hour
- [ ] Full system recovery within 4 hours (RTO)
- [ ] Data loss < 1 hour (RPO)
- [ ] All critical functionality working
- [ ] Performance meets baseline

**Post-Test Actions:**
- Update DR procedures based on lessons learned
- Train team on any new procedures
- Implement improvements identified
- Schedule next DR test

### 6.5 Quarterly Tabletop Exercises

**Tabletop Exercise Format:**

**Participants:**
- DR team members
- Sydney Metro stakeholders
- Operations team
- Security team

**Duration:** 2-3 hours

**Format:**
1. **Facilitator presents scenario** (e.g., ransomware attack, regional outage)
2. **Team discusses response:**
   - What are the first steps?
   - Who is responsible for what?
   - What decisions need to be made?
   - What are the communication steps?
3. **Facilitator introduces complications** (e.g., backup corrupted, key person unavailable)
4. **Team adapts response**
5. **Debrief and lessons learned**

**Sample Scenarios:**
- **Scenario 1:** Database corruption discovered, need point-in-time recovery
- **Scenario 2:** Ransomware encrypts production database
- **Scenario 3:** Insider threat - employee deletes critical data
- **Scenario 4:** AWS region outage in Sydney
- **Scenario 5:** Major security breach, need to rebuild from scratch

**Benefits:**
- Low cost, low risk (discussion only)
- Identifies gaps in procedures
- Cross-functional communication practice
- Builds team familiarity

### 6.6 DR Test Reporting

**DR Test Report Template:**

```
DR Test Report
==============

Test Date: [Date]
Test Type: [Component / AZ / Full DR / Tabletop]
Test Duration: [Hours]
Test Environment: [Production / Pre-production]

Scenario:
[Description of simulated disaster]

Participants:
- [Name, Role]
- [Name, Role]

Timeline:
- [Time]: [Event]
- [Time]: [Event]

Results:
- RTO Achieved: [Hours] (Target: < 4 hours)
- RPO Achieved: [Hours] (Target: < 1 hour)
- Success Criteria Met: [Yes/No]

What Went Well:
- [Point 1]
- [Point 2]

Issues Encountered:
- [Issue 1] - [Severity: High/Medium/Low]
- [Issue 2]

Lessons Learned:
- [Lesson 1]
- [Lesson 2]

Action Items:
- [Action 1] - [Owner] - [Due Date]
- [Action 2] - [Owner] - [Due Date]

Recommendations:
- [Recommendation 1]
- [Recommendation 2]

Next Test Scheduled: [Date]
```

**Reporting:**
- DR test report shared with Sydney Metro IT leadership
- Action items tracked in project management tool
- Quarterly summary of all DR tests presented to Steering Committee

---

## 7. Business Continuity During Migration

### 7.1 Migration Business Continuity Strategy

**Objective:** Ensure zero disruption to business operations during migration from Sitecore to Strapi.

**Principles:**
1. **Maintain Sitecore Availability:** Sitecore remains operational until cutover
2. **Zero Business Downtime:** Public-facing websites continue serving content
3. **Phased Migration:** Gradual migration of content, not "big bang"
4. **Fallback Plan:** Ability to revert to Sitecore if issues arise
5. **User Communication:** Clear communication to content editors and users

### 7.2 Migration Phases and Continuity

**Phase 1: Build and Test (Weeks 1-9)**
- **Business Impact:** None
- **Sitecore:** Remains fully operational
- **Strapi:** Built and tested in parallel (non-production)
- **Content Editors:** Continue using Sitecore normally

**Phase 2: Parallel Run (Week 10-11)**
- **Business Impact:** Minimal (content editors pilot Strapi)
- **Sitecore:** Remains primary CMS
- **Strapi:** UAT environment with migrated content
- **Content Editors:** Pilot users test Strapi, provide feedback
- **Fallback:** Sitecore still primary, can abort migration if needed

**Phase 3: Cutover (Week 12)**
- **Business Impact:** Content freeze during cutover window (48 hours)
- **Sitecore:** Set to read-only on Friday evening
- **Public Websites:** Continue serving content (cached, no impact)
- **Content Editors:** No editing during cutover window (planned for weekend)
- **Strapi:** Migration executed, validated, go-live
- **Fallback:** Rollback plan ready (see Section 7.3)

**Phase 4: Hypercare (Weeks 13-16)**
- **Business Impact:** None (Strapi now primary)
- **Sitecore:** Kept online in read-only mode (safety net for 4 weeks)
- **Content Editors:** Using Strapi, intensive support available
- **Fallback:** Sitecore available if critical issues (see Section 7.4)

**Phase 5: Decommission (Month 5+)**
- **Business Impact:** None
- **Sitecore:** Decommissioned after successful hypercare
- **Content Editors:** Fully on Strapi
- **Fallback:** Database backups only (no live Sitecore)

### 7.3 Cutover Rollback Plan

**Rollback Decision Criteria:**

Rollback to Sitecore if:
1. **Critical Data Loss:** Data migration failed, data missing or corrupted
2. **Critical Functionality Broken:** Content publishing not working, cannot create content
3. **Unacceptable Performance:** Page load times > 5 seconds, system unresponsive
4. **Security Issue:** Security vulnerability discovered during validation
5. **Business Decision:** Sydney Metro leadership decides to abort

**Rollback Decision Point:** Saturday 12:00 PM (halfway through cutover window)

**Rollback Procedure:**

**Step 1: Declare Rollback (12:00 PM)**
1. DR Coordinator declares rollback decision
2. Notify all stakeholders immediately
3. Stop all Strapi migration activities

**Step 2: Re-enable Sitecore (12:15 PM)**
```bash
# Set Sitecore back to read-write mode
# (Exact steps depend on Sitecore configuration)

# Update DNS to point back to Sitecore (if already switched)
aws route53 change-resource-record-sets \
  --hosted-zone-id Z123456 \
  --change-batch file://rollback-dns.json

# DNS propagation: 5-15 minutes
```

**Step 3: Sync Content Changes (12:30 PM)**
- If any content was created in Strapi during cutover testing:
  - Manually export from Strapi
  - Import to Sitecore
  - (Unlikely, as content freeze in effect)

**Step 4: Notify Users (12:45 PM)**
- Email all content editors: "Migration postponed, Sitecore back online"
- Public announcement (if needed): "Brief maintenance complete"

**Step 5: Resume Operations (1:00 PM)**
- Content editors can resume work in Sitecore
- Public websites continue serving from Sitecore
- Total downtime: < 1 hour (user-facing: 0, content editors: 1 hour)

**Post-Rollback:**
1. Root cause analysis: Why did we need to rollback?
2. Fix issues in Strapi
3. Rehearse migration again
4. Schedule new cutover date (2-4 weeks later)

**Rollback RTO:** < 1 hour
**Data Loss:** None (Sitecore remained intact)

### 7.4 Emergency Rollback (Post-Cutover)

**Scenario:** Critical issue discovered after cutover complete, need to rollback to Sitecore.

**Timeline:** Within 48 hours of go-live (while Sitecore still online in read-only)

**Emergency Rollback Procedure:**

**Step 1: Assess Situation (0-30 minutes)**
1. What is the critical issue?
2. Is it fixable in Strapi quickly? (< 2 hours)
   - If yes: Fix in Strapi (faster than rollback)
   - If no: Proceed with rollback
3. Decision to rollback made by DR Coordinator + Sydney Metro Sponsor

**Step 2: Data Sync (30-90 minutes)**
- Critical step: Sync content created in Strapi back to Sitecore
```bash
# Export all content created/modified since cutover
node scripts/export-new-content.js --since "2025-10-27T18:00:00Z"

# Import to Sitecore (manual or script)
# (Exact process depends on Sitecore APIs)
```

**Step 3: Switch Back to Sitecore (90-120 minutes)**
```bash
# Set Sitecore to read-write mode

# Update DNS back to Sitecore
aws route53 change-resource-record-sets \
  --hosted-zone-id Z123456 \
  --change-batch file://rollback-to-sitecore.json

# Wait for DNS propagation (15-30 minutes)
```

**Step 4: Validate and Resume (120-150 minutes)**
1. Verify Sitecore operational
2. Verify content changes synced correctly
3. Test critical functionality
4. Notify users Sitecore is back online

**Total Rollback Time:** 2-3 hours
**Data Loss:** Minimize by syncing Strapi changes back

**Note:** Emergency rollback only feasible within first 48 hours (while Sitecore still online). After Sitecore decommissioned, must fix forward in Strapi.

### 7.5 Content Freeze Management

**Content Freeze Period:** Friday 6:00 PM - Sunday 8:00 AM (38 hours)

**Content Freeze Communication:**

**3 Weeks Before Cutover:**
- Email all content editors: "Cutover scheduled for [date], content freeze [date/time]"
- Add to team calendars
- Post in content editor Slack channel

**1 Week Before Cutover:**
- Reminder email: "Content freeze in 1 week"
- Encourage editors to complete urgent content updates before freeze
- Identify any critical content needs during freeze (emergency plan)

**1 Day Before Cutover:**
- Final reminder: "Content freeze starts tomorrow at 6:00 PM"
- Set Sitecore to read-only mode at 6:00 PM sharp

**During Content Freeze:**
- Content editors cannot edit content (Sitecore read-only)
- Public websites continue serving existing content
- If emergency content update needed:
  - Contact DR Coordinator
  - Evaluate if truly critical
  - If yes: Manual process to update content in Sitecore, track for migration

**After Cutover:**
- Sunday 8:00 AM: Strapi goes live, content editing resumes
- Content editors log into Strapi (not Sitecore)

### 7.6 Public-Facing Website Continuity

**Objective:** Ensure public-facing websites (fed by CMS APIs) continue operating during migration.

**Strategy:**

**Before Cutover:**
- Public websites consume content from Sitecore APIs
- Content cached in CDN (CloudFront)
- No disruption

**During Cutover (Content Freeze):**
- Public websites continue serving cached content from CDN
- No new content published (content freeze)
- Users see existing content (no impact)

**During Strapi Migration:**
- Public websites still serving from Sitecore APIs
- Content remains cached in CDN
- Migration happens in background (no user impact)

**Cutover to Strapi APIs:**
- Update API endpoints to point to Strapi (configuration change)
- Gradual rollout: 10% traffic → 50% → 100%
- Monitor for errors
- If issues: Rollback API endpoints to Sitecore

**Result:** Public-facing websites experience zero downtime during migration

### 7.7 User Support During Migration

**Support Model During Migration:**

**Week Before Cutover:**
- Daily office hours for content editors
- Answer questions about new Strapi system
- Additional training sessions if needed

**Cutover Weekend:**
- DR team on-site and on-call
- Hotline for urgent issues
- Slack channel for real-time updates

**Week After Cutover (Hypercare):**
- Intensive support (24/7)
- On-site support desk
- Daily check-ins with content editors
- Quick resolution of issues

**Support Channels:**
- Dedicated email: cms-migration-support@hcl.com
- Dedicated phone: 1800-HCL-MIGRATION
- On-site support desk (business hours)
- Slack channel: #cms-migration-support

---

## 8. Communication Plan During Incidents

### 8.1 Communication Objectives

1. **Timely:** Communicate quickly, even if information incomplete
2. **Accurate:** Provide accurate information, correct if wrong
3. **Transparent:** Be honest about impact and timeline
4. **Consistent:** Use templates, consistent messaging
5. **Multi-Channel:** Email, phone, SMS, portal, website

### 8.2 Communication Stakeholders

**Internal Stakeholders:**

| Stakeholder Group | Communication Need | Channel | Frequency |
|-------------------|-------------------|---------|-----------|
| **Sydney Metro IT Leadership** | Strategic decisions, business impact, resource needs | Phone, Email | Hourly during incident |
| **Sydney Metro Content Editors** | User impact, workarounds, ETA to resolution | Email, Portal | Every 2 hours during incident |
| **HCL Project Team** | Technical details, actions needed | Slack, Email | Real-time during incident |
| **Operations Team** | System status, required actions | PagerDuty, Slack | Real-time during incident |

**External Stakeholders:**

| Stakeholder Group | Communication Need | Channel | Frequency |
|-------------------|-------------------|---------|-----------|
| **Public (Website Users)** | Service availability, user impact | Website banner, Twitter | Only if public-facing impact |
| **Media** | PR statement (if major outage) | PR team | Only if newsworthy |
| **Regulators** | Data breach notification (if applicable) | Formal letter | Within 72 hours (Privacy Act) |

### 8.3 Communication Templates

**Template 1: Initial Incident Notification**

```
Subject: [INCIDENT] Sydney Metro CMS - [Brief Description]

Severity: [P0 - Critical / P1 - High / P2 - Medium]
Start Time: [Timestamp]
Status: Investigating

Impact:
- [User impact description]
- [Affected systems/features]

Current Actions:
- [What we're doing to resolve]

Next Update: [Timestamp, typically +1 hour]

Contact: [Incident Commander Name, Contact]

This is an automated message from the Sydney Metro CMS incident management system.
```

**Template 2: Incident Update**

```
Subject: [UPDATE] Sydney Metro CMS - [Brief Description]

Severity: [P0 - Critical / P1 - High / P2 - Medium]
Start Time: [Timestamp]
Status: [Investigating / Identified / Resolving]
Elapsed Time: [HH:MM]

Update:
[What we've learned, progress made]

Impact:
[Current user impact, any changes]

Current Actions:
[What we're doing now]

Next Update: [Timestamp]

Contact: [Incident Commander Name, Contact]
```

**Template 3: Incident Resolution**

```
Subject: [RESOLVED] Sydney Metro CMS - [Brief Description]

Severity: [P0 - Critical / P1 - High / P2 - Medium]
Start Time: [Timestamp]
Resolution Time: [Timestamp]
Duration: [HH:MM]

Summary:
[Brief description of what happened]

Impact:
[User impact summary]

Root Cause:
[What caused the incident]

Resolution:
[How it was fixed]

Preventive Measures:
[What we're doing to prevent recurrence]

A detailed post-incident report will be provided within 5 business days.

Thank you for your patience.

Contact: [Incident Commander Name, Contact]
```

**Template 4: Public-Facing Message (Website Banner)**

```
Service Alert: The Sydney Metro website is currently experiencing technical difficulties.
We are working to resolve the issue.
Last updated: [Timestamp] | Next update: [Timestamp]
For urgent inquiries, please contact [phone number].
```

**Template 5: Data Breach Notification (If Applicable)**

```
Subject: Important Security Notice - Sydney Metro CMS

Dear [Recipient],

We are writing to inform you of a data security incident involving the Sydney Metro
Content Management System.

What Happened:
[Description of incident]

What Information Was Involved:
[Types of personal information potentially affected]

What We Are Doing:
[Response actions taken]

What You Can Do:
[Recommended actions for affected individuals]

For More Information:
[Contact information]

We sincerely apologize for this incident and any inconvenience it may cause.

Regards,
Sydney Metro IT Security Team
```

### 8.4 Communication Channels and Tools

**Internal Communication Channels:**

| Channel | Purpose | Audience | Availability |
|---------|---------|----------|--------------|
| **Email** | Formal incident notifications, updates | All stakeholders | 24/7 |
| **SMS** | Critical alerts, escalations | DR team, on-call engineers | 24/7 |
| **Phone** | Urgent communication, conference bridge | DR team, leadership | 24/7 |
| **Slack (#incident-response)** | Real-time team coordination | Technical team | 24/7 |
| **PagerDuty** | Alert delivery, on-call scheduling | Operations team | 24/7 |
| **Status Page (Internal)** | Self-service incident status | All Sydney Metro staff | 24/7 |

**External Communication Channels:**

| Channel | Purpose | Audience | Availability |
|---------|---------|----------|--------------|
| **Website Banner** | Public service alerts | Website visitors | 24/7 |
| **Twitter** | Public updates, outage notifications | Public, media | 24/7 |
| **Email (Broadcast)** | Notification to registered users | Content editors, partners | 24/7 |

### 8.5 Communication Escalation

**Escalation Triggers:**

| Scenario | Communication Escalation |
|----------|-------------------------|
| **P0 Incident > 1 hour** | Notify Sydney Metro CIO/IT Director |
| **P0 Incident > 4 hours** | Escalate to Sydney Metro Executive Leadership |
| **Data Breach Confirmed** | Immediate notification to CISO, Legal, PR team |
| **Media Inquiry** | Route to Sydney Metro PR team, prepare statement |
| **Regulatory Reporting Required** | Notify Legal team, prepare formal notification |

**Escalation Contacts:**

| Level | Role | Contact | When to Escalate |
|-------|------|---------|------------------|
| **L1** | Incident Commander | [Phone] | All incidents (default) |
| **L2** | Sydney Metro IT Manager | [Phone] | P0 incidents, no progress after 1 hour |
| **L3** | Sydney Metro CIO | [Phone] | P0 incidents > 4 hours, significant business impact |
| **Legal** | Sydney Metro Legal Counsel | [Phone] | Data breach, regulatory issues |
| **PR** | Sydney Metro Communications Director | [Phone] | Media attention, public-facing impact |

### 8.6 Communication During DR Activation

**DR Activation Communication Timeline:**

**T+0 (Disaster Declared):**
- **Activate DR Team:** Phone calls, SMS, PagerDuty to all DR team members
- **Notify Leadership:** Phone call to Sydney Metro IT Director
- **Initial Notification:** Email to all stakeholders (Template 1)
- **Status Page Update:** "System outage - disaster recovery in progress"

**T+30 minutes:**
- **First Update:** Email with initial assessment and recovery plan
- **Leadership Briefing:** Conference call with Sydney Metro leadership

**T+1 hour, T+2 hours, etc:**
- **Hourly Updates:** Email updates on recovery progress
- **Leadership Updates:** Hourly phone briefings

**Recovery Complete:**
- **All-Clear Notification:** Email announcing system restored (Template 3)
- **Status Page Update:** "System operational"
- **User Communication:** Email to content editors with testing/validation instructions

**Post-Incident (within 5 days):**
- **Detailed Post-Incident Report:** Comprehensive writeup with timeline, root cause, lessons learned
- **Executive Briefing:** Present findings to Sydney Metro leadership
- **Improvement Plan:** Action items to prevent recurrence

### 8.7 Communication Metrics

**Communication Effectiveness Metrics:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| **Time to Initial Notification** | < 15 minutes | Time from incident detection to first communication |
| **Update Frequency** | Every 1 hour (P0), Every 2 hours (P1) | Adherence to communication schedule |
| **Stakeholder Satisfaction** | ≥ 4.0 / 5.0 | Post-incident survey |
| **Information Accuracy** | 100% | Number of corrections needed |
| **Post-Incident Report Delivery** | Within 5 business days | Time from resolution to report delivery |

---

## Appendices

### Appendix A: DR Contact List

**HCL DR Team:**

| Role | Primary Contact | Backup Contact | Phone | Email |
|------|----------------|----------------|-------|-------|
| DR Coordinator | [Name] | [Name] | [Phone] | [Email] |
| Infrastructure Lead | [Name] | [Name] | [Phone] | [Email] |
| Database Lead | [Name] | [Name] | [Phone] | [Email] |
| Application Lead | [Name] | [Name] | [Phone] | [Email] |
| QA Lead | [Name] | [Name] | [Phone] | [Email] |
| Communications Lead | [Name] | [Name] | [Phone] | [Email] |
| Security Lead | [Name] | [Name] | [Phone] | [Email] |

**Sydney Metro Stakeholders:**

| Role | Name | Phone | Email | Escalation Level |
|------|------|-------|-------|------------------|
| IT Director | [Name] | [Phone] | [Email] | L2 |
| CIO | [Name] | [Phone] | [Email] | L3 |
| CISO | [Name] | [Phone] | [Email] | Security incidents |
| Legal Counsel | [Name] | [Phone] | [Email] | Data breaches |
| Communications Director | [Name] | [Phone] | [Email] | PR/Media |

**External Vendors:**

| Vendor | Contact | Phone | Email | Purpose |
|--------|---------|-------|-------|---------|
| AWS Enterprise Support | AWS Console | 24/7 hotline | aws-support@amazon.com | Infrastructure issues |
| [Security Firm] | [Contact] | [Phone] | [Email] | Security incidents |

### Appendix B: DR Runbook Quick Reference

**Emergency Quick Reference:**

1. **System Down?**
   - Check AWS Health Dashboard: https://health.aws.amazon.com
   - Check CloudWatch Alarms: [URL]
   - Check ECS Service Status: `aws ecs describe-services --cluster cms-production --services cms-service`

2. **Database Down?**
   - Check RDS Status: `aws rds describe-db-instances --db-instance-identifier cms-production-db`
   - Check RDS Events: AWS Console → RDS → Events
   - Manual Failover: `aws rds reboot-db-instance --db-instance-identifier cms-production-db --force-failover`

3. **Need to Rollback Deployment?**
   - `aws ecs update-service --cluster cms-production --service cms-service --task-definition cms-task:previous-revision`

4. **Need to Restore Database?**
   - See Section 5.3 (Point-in-Time Recovery)

5. **Need to Activate Full DR?**
   - See Section 5.5 (Complete System Failure Recovery)

### Appendix C: DR Testing Schedule

| Test Type | Frequency | Next Scheduled | Owner |
|-----------|-----------|----------------|-------|
| ECS Task Failover | Monthly | [Date] | DevOps Lead |
| Database Failover | Monthly | [Date] | Database Lead |
| AZ Failover | Quarterly | [Date] | DR Coordinator |
| Full DR Test | Semi-annually | [Date] | DR Coordinator |
| Tabletop Exercise | Quarterly | [Date] | DR Coordinator |

### Appendix D: Backup Validation Log

| Date | Backup Type | Validation Result | Tested By | Notes |
|------|-------------|-------------------|-----------|-------|
| [Date] | Daily DB Snapshot | Success | [Name] | Restored to test env, data validated |
| [Date] | S3 Versioning | Success | [Name] | Deleted file restored successfully |

### Appendix E: DR Test Results Summary

| Test Date | Test Type | RTO Achieved | RPO Achieved | Pass/Fail | Issues |
|-----------|-----------|--------------|--------------|-----------|--------|
| [Date] | Full DR Test | 3.5 hours | 45 minutes | Pass | None |
| [Date] | AZ Failover | 4 minutes | 0 | Pass | Minor delay in auto-scaling |

---

**Document End**
