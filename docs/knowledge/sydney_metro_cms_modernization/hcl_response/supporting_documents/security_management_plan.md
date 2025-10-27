# Security Management Plan
## Sydney Metro CMS Modernization Project

**Document Version:** 1.0
**Date:** October 2025
**Prepared by:** HCL Technologies
**Classification:** Commercial in Confidence

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | October 2025 | HCL Security Team | Initial version |

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Security Governance](#2-security-governance)
3. [Security Architecture and Controls](#3-security-architecture-and-controls)
4. [Access Management](#4-access-management)
5. [Data Protection](#5-data-protection)
6. [Security Testing](#6-security-testing)
7. [Incident Response](#7-incident-response)
8. [Security Monitoring and Logging](#8-security-monitoring-and-logging)
9. [Compliance Framework](#9-compliance-framework)

---

## 1. Executive Summary

This Security Management Plan establishes the comprehensive security framework for the Sydney Metro CMS Modernization project. The plan ensures the confidentiality, integrity, and availability of Sydney Metro's content management system and data through defense-in-depth security controls, continuous monitoring, and compliance with Australian government security standards.

### 1.1 Security Objectives

1. **Protect Sensitive Data:** Ensure all Sydney Metro data is protected against unauthorized access, modification, or disclosure
2. **Secure Authentication:** Implement robust identity and access management using Azure AD and OIDC
3. **Maintain Compliance:** Achieve and maintain compliance with ISO 27001 and IRAP standards
4. **Ensure Data Residency:** Keep all data within Australian borders (AWS Sydney region)
5. **Enable Secure Operations:** Provide secure, auditable system operations
6. **Rapid Incident Response:** Detect and respond to security incidents within defined SLAs

### 1.2 Security Principles

**Core Security Principles:**

1. **Defense in Depth:** Multiple layers of security controls
2. **Least Privilege:** Users granted minimum necessary access
3. **Zero Trust:** Verify explicitly, never assume trust
4. **Security by Design:** Security embedded from the start
5. **Privacy by Design:** Data protection built into system architecture
6. **Continuous Monitoring:** Real-time security visibility
7. **Secure by Default:** Secure configuration out-of-the-box
8. **Fail Securely:** System fails to secure state, not open state

### 1.3 Security Standards and Frameworks

| Framework | Applicability | Compliance Target |
|-----------|---------------|-------------------|
| **ISO 27001:2022** | Information security management | Full compliance |
| **IRAP (Infosec Registered Assessors Program)** | Australian government security | Assessment and remediation |
| **ISM (Information Security Manual)** | Australian cyber security guidance | Alignment with Essential Eight |
| **OWASP Top 10** | Web application security | Full mitigation |
| **CWE Top 25** | Software weaknesses | Proactive prevention |
| **NIST Cybersecurity Framework** | Security program structure | Framework alignment |
| **PSPF (Protective Security Policy Framework)** | Government security | Relevant controls applied |

---

## 2. Security Governance

### 2.1 Security Organization

**Security Governance Structure:**

```
┌──────────────────────────────────────────────────────────┐
│              Sydney Metro CISO/IT Security               │
│                  (Governance Oversight)                  │
└────────────────────┬─────────────────────────────────────┘
                     │
     ┌───────────────┴────────────────┐
     │                                │
┌────▼─────────────────┐   ┌─────────▼──────────────┐
│ HCL Security Lead    │   │  HCL Project Manager   │
│ (Security Execution) │   │  (Delivery Oversight)  │
└────┬─────────────────┘   └─────────┬──────────────┘
     │                               │
     ├───────────────┬───────────────┼────────────────┐
     │               │               │                │
┌────▼────┐  ┌──────▼─────┐  ┌─────▼──────┐  ┌──────▼──────┐
│Security │  │Application │  │Infrastructure│ │Security     │
│Architect│  │Security    │  │Security      │ │Operations   │
│         │  │Engineer    │  │Engineer      │ │Analyst      │
└─────────┘  └────────────┘  └──────────────┘ └─────────────┘
```

### 2.2 Roles and Responsibilities

| Role | Security Responsibilities |
|------|---------------------------|
| **Sydney Metro CISO** | Security governance, policy approval, risk acceptance, compliance oversight |
| **HCL Security Lead** | Security strategy, architecture, incident response, compliance delivery |
| **Security Architect** | Security design, threat modeling, security controls specification |
| **Application Security Engineer** | Secure code review, SAST/DAST, vulnerability remediation |
| **Infrastructure Security Engineer** | Cloud security, network security, infrastructure hardening |
| **Security Operations Analyst** | Security monitoring, log analysis, incident detection |
| **Project Manager** | Security milestone tracking, resource allocation, stakeholder communication |
| **Development Team** | Secure coding practices, security testing, vulnerability fixes |

### 2.3 Security Governance Framework

**Security Policies:**
- Information Security Policy
- Access Control Policy
- Data Classification and Handling Policy
- Acceptable Use Policy
- Incident Response Policy
- Change Management Policy
- Third-Party Risk Management Policy

**Security Standards:**
- Secure Development Standard
- Cloud Security Standard
- Encryption Standard
- Authentication and Authorization Standard
- Logging and Monitoring Standard
- Vulnerability Management Standard

**Security Procedures:**
- Security Incident Response Procedure
- Vulnerability Assessment Procedure
- Access Request and Review Procedure
- Security Testing Procedure
- Security Audit Procedure
- Disaster Recovery Procedure

### 2.4 Security Committees and Meetings

**Security Review Board:**
- **Frequency:** Monthly
- **Attendees:** Sydney Metro CISO, HCL Security Lead, Project Manager
- **Purpose:** Security posture review, risk assessment, compliance status

**Security Working Group:**
- **Frequency:** Weekly
- **Attendees:** Security team, development leads, operations
- **Purpose:** Security implementation, issue resolution, knowledge sharing

**Incident Response Team (IRT):**
- **Frequency:** On-demand (incidents), Monthly (exercises)
- **Attendees:** Security team, operations, communications
- **Purpose:** Incident handling, post-incident review, readiness drills

### 2.5 Risk Management

**Security Risk Assessment Process:**

```
┌──────────────┐   ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
│   Identify   │──→│   Analyze    │──→│   Evaluate   │──→│    Treat     │
│   Threats    │   │     Risk     │   │   Risk Level │   │     Risk     │
└──────────────┘   └──────────────┘   └──────────────┘   └──────────────┘
                                             │
                                             ▼
                                    ┌──────────────┐
                                    │   Monitor    │
                                    │   & Review   │
                                    └──────────────┘
```

**Risk Matrix:**

| Likelihood / Impact | Low | Medium | High | Critical |
|---------------------|-----|--------|------|----------|
| **Rare** | Low | Low | Medium | High |
| **Unlikely** | Low | Medium | Medium | High |
| **Possible** | Medium | Medium | High | Critical |
| **Likely** | Medium | High | High | Critical |
| **Almost Certain** | High | High | Critical | Critical |

**Risk Treatment Options:**
1. **Mitigate:** Implement controls to reduce risk
2. **Transfer:** Insurance or third-party assumption
3. **Avoid:** Eliminate the risk source
4. **Accept:** Acknowledge and monitor (with senior approval)

**Key Security Risks:**

| Risk | Impact | Likelihood | Risk Level | Mitigation |
|------|--------|------------|------------|------------|
| Unauthorized data access | High | Unlikely | Medium | RBAC, MFA, encryption, audit logging |
| Data breach | Critical | Rare | High | Encryption, DLP, access controls, monitoring |
| DDoS attack | High | Possible | High | AWS Shield, WAF, CloudFront, auto-scaling |
| Insider threat | High | Unlikely | Medium | Least privilege, audit logging, separation of duties |
| Supply chain attack | High | Unlikely | Medium | Dependency scanning, SBOM, vendor assessment |
| Account compromise | High | Unlikely | Medium | MFA, strong passwords, account monitoring |
| Malware infection | Medium | Rare | Medium | Anti-malware, sandboxing, secure build pipeline |
| Data loss | High | Rare | Medium | Automated backups, replication, disaster recovery |

---

## 3. Security Architecture and Controls

### 3.1 Security Architecture Overview

**Defense-in-Depth Architecture:**

```
┌───────────────────────────────────────────────────────────────┐
│ Layer 7: User Education & Awareness                           │
├───────────────────────────────────────────────────────────────┤
│ Layer 6: Physical Security (AWS Data Center Controls)         │
├───────────────────────────────────────────────────────────────┤
│ Layer 5: Application Security (OWASP, Secure Coding)          │
│   - Input Validation                                          │
│   - Output Encoding                                           │
│   - Authentication & Authorization                            │
│   - Session Management                                        │
├───────────────────────────────────────────────────────────────┤
│ Layer 4: Host Security (Container Security, OS Hardening)     │
│   - AWS ECS Fargate                                           │
│   - Immutable Infrastructure                                  │
│   - Vulnerability Scanning                                    │
├───────────────────────────────────────────────────────────────┤
│ Layer 3: Network Security (VPC, Security Groups, NACLs)       │
│   - Private Subnets                                           │
│   - Security Groups (Stateful Firewall)                       │
│   - Network ACLs (Stateless Firewall)                        │
│   - VPC Flow Logs                                             │
├───────────────────────────────────────────────────────────────┤
│ Layer 2: Perimeter Security (WAF, DDoS Protection)            │
│   - AWS WAF (OWASP Top 10 Rules)                             │
│   - AWS Shield Standard/Advanced                              │
│   - CloudFront (DDoS Mitigation)                              │
│   - Rate Limiting                                             │
├───────────────────────────────────────────────────────────────┤
│ Layer 1: Data Security (Encryption, Backup, DLP)              │
│   - Encryption at Rest (AES-256)                              │
│   - Encryption in Transit (TLS 1.3)                           │
│   - Key Management (AWS KMS)                                  │
│   - Data Backup & Replication                                 │
└───────────────────────────────────────────────────────────────┘
```

### 3.2 Network Security Controls

**VPC Architecture:**

```
┌─────────────────────────────────────────────────────────────┐
│                    AWS VPC (Sydney Region)                  │
│                      10.0.0.0/16                            │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Public Subnet (10.0.1.0/24)       AZ-1a             │  │
│  │  ┌─────────────┐         ┌─────────────┐            │  │
│  │  │   NAT GW    │         │  ALB (Public)│            │  │
│  │  └─────────────┘         └─────────────┘            │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Private Subnet (10.0.10.0/24)     AZ-1a             │  │
│  │  ┌─────────────┐         ┌─────────────┐            │  │
│  │  │  ECS Tasks  │         │  ECS Tasks  │            │  │
│  │  │  (Strapi)   │         │  (Strapi)   │            │  │
│  │  └─────────────┘         └─────────────┘            │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Database Subnet (10.0.20.0/24)    AZ-1a             │  │
│  │  ┌──────────────────────────────────────┐            │  │
│  │  │  RDS PostgreSQL (Primary)            │            │  │
│  │  └──────────────────────────────────────┘            │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                             │
│  [Similar subnets in AZ-1b and AZ-1c for HA]              │
└─────────────────────────────────────────────────────────────┘
```

**Security Groups (Stateful Firewall Rules):**

| Security Group | Inbound Rules | Outbound Rules |
|----------------|---------------|----------------|
| **ALB-SG** | 443 from 0.0.0.0/0<br>80 from 0.0.0.0/0 (redirect to 443) | All traffic to ECS-SG |
| **ECS-SG** | 1337 from ALB-SG | 5432 to RDS-SG<br>443 to 0.0.0.0/0 (AWS APIs)<br>443 to S3 endpoint |
| **RDS-SG** | 5432 from ECS-SG | None (managed by RDS) |

**Network ACLs (Stateless Firewall Rules):**
- **Public Subnet NACL:** Allow inbound 80, 443; ephemeral ports for responses
- **Private Subnet NACL:** Allow from public subnet, deny external direct access
- **Database Subnet NACL:** Allow only from private subnet on port 5432

**VPC Endpoints:**
- **S3 Gateway Endpoint:** Private connectivity to S3 without internet gateway
- **Secrets Manager Interface Endpoint:** Private access to secrets
- **CloudWatch Logs Interface Endpoint:** Private log streaming

### 3.3 Application Security Controls

**OWASP Top 10 Mitigation:**

| Vulnerability | Mitigation Controls |
|---------------|---------------------|
| **A01: Broken Access Control** | RBAC enforcement, ownership checks, API authorization, audit logging |
| **A02: Cryptographic Failures** | TLS 1.3, AES-256 encryption, secure key storage (KMS), HSTS headers |
| **A03: Injection** | Parameterized queries (Strapi ORM), input validation, output encoding |
| **A04: Insecure Design** | Threat modeling, secure architecture review, security requirements |
| **A05: Security Misconfiguration** | Infrastructure as Code, automated security checks, hardening baselines |
| **A06: Vulnerable Components** | Dependency scanning (Snyk), automated updates, SBOM tracking |
| **A07: Authentication Failures** | Azure AD + OIDC, MFA required, strong password policy, session management |
| **A08: Data Integrity Failures** | Digital signatures, integrity checks, secure CI/CD pipeline |
| **A09: Logging Failures** | Centralized logging, audit trails, CloudWatch integration, SIEM |
| **A10: SSRF** | Input validation, URL allowlisting, network segmentation |

**Content Security Policy (CSP):**

```http
Content-Security-Policy:
  default-src 'self';
  script-src 'self' 'unsafe-inline' 'unsafe-eval';
  style-src 'self' 'unsafe-inline';
  img-src 'self' data: https://cdn.sydneymetro.com.au;
  font-src 'self' data:;
  connect-src 'self' https://api.sydneymetro.com.au;
  media-src 'self' https://cdn.sydneymetro.com.au;
  frame-ancestors 'none';
  base-uri 'self';
  form-action 'self';
```

**Security Headers:**

```http
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

**API Security:**
- **Rate Limiting:** 100 requests/minute per IP, 1000 requests/hour per user
- **API Authentication:** JWT tokens (Azure AD issued)
- **Request Validation:** JSON schema validation, input sanitization
- **Response Filtering:** Sensitive data masking, error message sanitization
- **CORS Policy:** Strict origin allowlisting

### 3.4 Container Security

**AWS ECS Fargate Security:**
- **Immutable Infrastructure:** Containers rebuilt from scratch on each deployment
- **Non-Root User:** Containers run as non-privileged user
- **Read-Only Root Filesystem:** Application data in mounted volumes only
- **Resource Limits:** CPU and memory constraints to prevent resource exhaustion
- **Security Scanning:** Trivy scans for container vulnerabilities

**Container Image Security:**

```dockerfile
# Security-hardened Dockerfile example
FROM node:18-alpine AS base

# Run as non-root user
RUN addgroup -g 1001 -S nodejs && adduser -S nodejs -u 1001
USER nodejs

# Read-only root filesystem
WORKDIR /app
COPY --chown=nodejs:nodejs package*.json ./
RUN npm ci --only=production && npm cache clean --force

COPY --chown=nodejs:nodejs . .

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s \
  CMD node healthcheck.js

# Security labels
LABEL security.scan="enabled" \
      security.updates="auto"

EXPOSE 1337
CMD ["node", "server.js"]
```

**Image Scanning:**
- **Registry Scanning:** AWS ECR automated scanning on push
- **CI/CD Scanning:** Trivy scans in GitHub Actions pipeline
- **Vulnerability Threshold:** Block deployment if Critical vulnerabilities found
- **SBOM Generation:** Software Bill of Materials for supply chain security

### 3.5 Database Security

**PostgreSQL Security Hardening:**

| Control | Configuration |
|---------|---------------|
| **Encryption at Rest** | AWS RDS encryption enabled (AES-256) |
| **Encryption in Transit** | SSL/TLS required for all connections |
| **Network Isolation** | Private subnet, no public access |
| **Authentication** | IAM database authentication enabled |
| **Password Policy** | 16+ characters, rotated every 90 days |
| **Audit Logging** | PostgreSQL audit extension (pgaudit) enabled |
| **Backup Encryption** | Automated backups encrypted with KMS |
| **Connection Limits** | Max connections: 200 (monitored) |
| **Parameter Hardening** | log_connections=on, log_disconnections=on, log_statement='ddl' |

**Database Access Control:**
- **Principle of Least Privilege:** Each service has dedicated DB user with minimal permissions
- **No Shared Credentials:** Each environment has unique credentials
- **Secrets Rotation:** Automated 90-day rotation via AWS Secrets Manager
- **Read Replicas:** Separate credentials for read-only operations

---

## 4. Access Management

### 4.1 Identity and Access Management (IAM) Strategy

**Identity Provider:** Azure Active Directory (Azure AD)

**Authentication Protocol:** OpenID Connect (OIDC)

**Authorization Model:** Role-Based Access Control (RBAC)

### 4.2 Authentication Framework

**Azure AD Integration:**

```
┌────────────────┐         ┌──────────────┐         ┌─────────────┐
│  User Browser  │────1───→│   Azure AD   │────2───→│   Strapi    │
│                │         │   (IdP)      │         │    CMS      │
│                │←───5────│              │         │             │
└────────────────┘         └──────────────┘         └─────────────┘
                                  │                        ▲
                                  │                        │
                                  └────────3────────────────┘
                                   (JWT Token Exchange)

Flow:
1. User initiates login
2. Redirect to Azure AD login page
3. User authenticates with Azure AD credentials + MFA
4. Azure AD issues JWT token
5. User redirected back to Strapi with JWT token
6. Strapi validates JWT token signature and claims
7. User session established
```

**Multi-Factor Authentication (MFA):**
- **Requirement:** MFA mandatory for all users
- **Methods:** Microsoft Authenticator app (push notification or TOTP), SMS backup
- **Enforcement:** Azure AD Conditional Access policies
- **Exceptions:** None (no MFA bypass)

**Single Sign-On (SSO):**
- Azure AD serves as single source of identity
- Users authenticate once, access all authorized systems
- Session timeout: 8 hours of inactivity
- Absolute session timeout: 24 hours

**Password Policy:**
- **Minimum Length:** 14 characters
- **Complexity:** Uppercase, lowercase, number, special character
- **History:** Cannot reuse last 12 passwords
- **Expiration:** 90 days (Azure AD policy)
- **Account Lockout:** 5 failed attempts = 30-minute lockout
- **Password Breach Detection:** Azure AD Identity Protection

### 4.3 Role-Based Access Control (RBAC)

**Strapi CMS Roles:**

| Role | Permissions | Typical Users |
|------|-------------|---------------|
| **Super Admin** | Full system access, user management, system configuration | IT Administrators (2-3 users) |
| **Administrator** | User management, content moderation, plugin management | Content Managers (3-5 users) |
| **Content Manager** | Create, edit, delete, publish all content across all sections | Senior Editors (5-8 users) |
| **Content Editor** | Create, edit own content; publish with approval | Content Editors (20-30 users) |
| **Contributor** | Create and edit draft content only; cannot publish | External Contributors (10-15 users) |
| **Reviewer** | Review and approve content; cannot create or edit | Content Reviewers (5-8 users) |
| **Read-Only User** | View content and reports; no editing capability | Auditors, Stakeholders (as needed) |

**Permission Matrix:**

| Permission | Super Admin | Admin | Content Manager | Editor | Contributor | Reviewer | Read-Only |
|------------|-------------|-------|-----------------|--------|-------------|----------|-----------|
| System Configuration | ✓ | - | - | - | - | - | - |
| User Management | ✓ | ✓ | - | - | - | - | - |
| Plugin Management | ✓ | ✓ | - | - | - | - | - |
| Create Content | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| Edit Own Content | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| Edit Others' Content | ✓ | ✓ | ✓ | ✓ | - | - | - |
| Delete Content | ✓ | ✓ | ✓ | - | - | - | - |
| Publish Content | ✓ | ✓ | ✓ | Approval Req. | - | - | - |
| Approve Content | ✓ | ✓ | ✓ | - | - | ✓ | - |
| Manage Media | ✓ | ✓ | ✓ | ✓ | Limited | - | - |
| View Audit Logs | ✓ | ✓ | ✓ | - | - | - | - |
| Access API | ✓ | ✓ | ✓ | Read-Only | Read-Only | Read-Only | Read-Only |
| View Reports | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |

**Custom Role Capabilities:**
- Granular permission configuration per content type
- Geographic access restrictions (if needed)
- Time-based access (e.g., contractor access for project duration)

### 4.4 Access Request and Approval Process

**Access Request Workflow:**

```
┌──────────────┐   ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
│  User        │──→│  Manager     │──→│  Security    │──→│  Admin       │
│  Requests    │   │  Approves    │   │  Reviews     │   │  Provisions  │
│  Access      │   │              │   │              │   │  Access      │
└──────────────┘   └──────────────┘   └──────────────┘   └──────────────┘
    (Day 0)           (Day 1)            (Day 2)            (Day 3)
```

**Access Request Form:**
- User details (name, email, department)
- Role requested (with justification)
- Access duration (temporary or permanent)
- Business justification
- Manager approval
- Security team review

**Access Provisioning SLA:**
- **Standard Access:** 3 business days
- **Emergency Access:** 4 hours (with post-approval review)

### 4.5 Access Reviews and Recertification

**Quarterly Access Reviews:**
- **Frequency:** Every 90 days
- **Scope:** All user accounts and permissions
- **Owners:** Department managers review their team's access
- **Process:**
  1. Generate access report for each department
  2. Managers validate each user's access is still appropriate
  3. Remove access for users who have changed roles or left organization
  4. Document review results

**Automated Access Revocation:**
- **User Offboarding:** Access removed within 24 hours of termination
- **Inactive Accounts:** Disabled after 60 days of inactivity
- **Temporary Access:** Automatically revoked after expiration date
- **Role Changes:** Previous role permissions removed when new role assigned

### 4.6 Privileged Access Management

**Privileged Account Security:**

| Control | Implementation |
|---------|----------------|
| **Break-Glass Accounts** | 2 emergency Super Admin accounts (sealed envelopes, physically secured) |
| **Privileged Access Workstations** | Dedicated hardened workstations for admin access |
| **Just-in-Time (JIT) Access** | AWS SSM Session Manager for temporary infrastructure access |
| **Privilege Escalation Approval** | Requires approval and audit trail for elevated access |
| **Session Recording** | All privileged sessions recorded and archived |
| **Command Auditing** | All administrative commands logged |

**AWS IAM Roles and Policies:**
- Principle of Least Privilege applied to all IAM roles
- Service-specific IAM roles (ECS task role, Lambda execution role)
- No long-term AWS access keys (use IAM roles instead)
- MFA required for AWS Console access
- CloudTrail logging of all AWS API calls

---

## 5. Data Protection

### 5.1 Data Classification

**Data Classification Scheme:**

| Classification | Definition | Examples | Security Controls |
|----------------|------------|----------|-------------------|
| **Public** | Information intended for public disclosure | Published website content, marketing materials | Standard controls |
| **Internal** | General business information | Draft content, editorial calendars, meeting notes | Access control, encryption in transit |
| **Confidential** | Sensitive business information | User PII, unpublished strategic content, audit logs | Encryption at rest and in transit, access logging, restricted access |
| **Restricted** | Highly sensitive information | Authentication credentials, encryption keys, security configs | Strongest encryption, MFA, audit logging, need-to-know access |

**Data Handling Requirements:**

| Classification | Storage | Transmission | Disposal | Access |
|----------------|---------|--------------|----------|--------|
| Public | Any | Any | Normal deletion | Anyone |
| Internal | Encrypted storage | TLS 1.3 | Secure deletion | Authenticated users |
| Confidential | AES-256 encryption | TLS 1.3 | Cryptographic erasure | Authorized users only |
| Restricted | AES-256 + KMS | TLS 1.3 + MFA | Cryptographic erasure + verification | Named individuals only |

### 5.2 Data Residency and Sovereignty

**Geographic Requirements:**
- **Primary Requirement:** All data stored in Australia (AWS Sydney region: ap-southeast-2)
- **No Data Transfer:** No data stored or processed outside Australia
- **Backup Location:** AWS Sydney region only
- **DR Location:** Separate availability zones within Sydney region
- **CDN:** CloudFront edge locations globally, but origin in Sydney

**Compliance:**
- Aligns with Australian Privacy Principles (APPs)
- Meets government data residency requirements
- GDPR-equivalent data protection standards

### 5.3 Encryption Strategy

**Encryption at Rest:**

| Data Store | Encryption Method | Key Management |
|------------|-------------------|----------------|
| **RDS PostgreSQL** | AES-256 encryption | AWS KMS (Customer Managed Key) |
| **S3 Media Storage** | Server-Side Encryption (SSE-S3) | AWS managed keys |
| **EBS Volumes** | EBS encryption | AWS KMS |
| **Backup Snapshots** | Automated encryption | AWS KMS |
| **CloudWatch Logs** | Log group encryption | AWS KMS |
| **Secrets Manager** | Encryption by default | AWS KMS |

**Encryption in Transit:**

| Connection | Protocol | Cipher Suites |
|------------|----------|---------------|
| **Client ↔ CloudFront** | TLS 1.3 (minimum TLS 1.2) | TLS_AES_256_GCM_SHA384, TLS_AES_128_GCM_SHA256 |
| **CloudFront ↔ ALB** | TLS 1.3 | TLS_AES_256_GCM_SHA384 |
| **ALB ↔ ECS** | TLS 1.2 | TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 |
| **ECS ↔ RDS** | SSL/TLS (PostgreSQL SSL) | AES-256-GCM |
| **ECS ↔ S3** | TLS 1.3 | TLS_AES_256_GCM_SHA384 |
| **Admin ↔ Azure AD** | TLS 1.3 | TLS_AES_256_GCM_SHA384 |

**Key Management:**

```
┌──────────────────────────────────────────────────────┐
│            AWS Key Management Service (KMS)          │
├──────────────────────────────────────────────────────┤
│  Customer Managed Keys (CMKs)                        │
│  ├─ RDS-CMK: Database encryption                     │
│  ├─ S3-CMK: Media file encryption                    │
│  ├─ Backup-CMK: Backup encryption                    │
│  └─ Logs-CMK: Log encryption                         │
├──────────────────────────────────────────────────────┤
│  Key Rotation: Automatic annual rotation             │
│  Key Policy: Least privilege access                  │
│  Audit: CloudTrail logs all key usage                │
└──────────────────────────────────────────────────────┘
```

**Key Management Practices:**
- **Automatic Rotation:** CMKs rotated annually
- **Access Control:** IAM policies restrict key usage to authorized services
- **Audit Trail:** CloudTrail logs all KMS API calls
- **Key Backup:** Keys automatically backed up by AWS
- **No Key Export:** Keys never leave AWS KMS

### 5.4 Data Loss Prevention (DLP)

**DLP Controls:**

1. **Prevent Unauthorized Data Export:**
   - API rate limiting
   - Large data export requires approval
   - Audit logging of bulk exports

2. **Sensitive Data Detection:**
   - Automated scanning for PII in uploaded content
   - Warning prompts for sensitive information
   - Content classification labeling

3. **Data Leak Detection:**
   - Monitor for unusual data access patterns
   - Alert on large data downloads
   - Track content shared externally via APIs

4. **Email Security:**
   - Email gateway scans for sensitive data in outbound emails
   - Encryption required for emails containing confidential data

### 5.5 Personal Information Protection

**Privacy by Design:**
- Minimal data collection (only what's necessary)
- Purpose limitation (use data only for stated purpose)
- Data minimization (retain only as long as needed)
- Consent management (explicit user consent where required)

**PII Handling:**

| PII Type | Where Stored | Retention | Access |
|----------|--------------|-----------|--------|
| **User Names** | Azure AD, Strapi DB | Duration of employment + 7 years | Authorized admins only |
| **Email Addresses** | Azure AD, Strapi DB | Duration of employment + 7 years | Authorized admins only |
| **Audit Logs (User Actions)** | CloudWatch Logs | 7 years | Security team, auditors |
| **Session Data** | ECS memory (temporary) | Session duration only | Application only |

**Data Subject Rights (Australian Privacy Principles):**
- **Right to Access:** Users can request their personal data
- **Right to Correction:** Users can request data corrections
- **Right to Deletion:** Users can request data deletion (subject to legal requirements)
- **Data Portability:** Export user data in machine-readable format

### 5.6 Backup and Recovery

**Backup Strategy:**

| Data | Backup Frequency | Retention | Storage Location |
|------|------------------|-----------|------------------|
| **Database** | Daily automated RDS snapshots | 35 days | AWS Sydney region (cross-AZ) |
| **Media Files** | S3 versioning enabled | 90 days | S3 (same region, cross-AZ) |
| **Configuration** | Version controlled in Git | Indefinite | GitHub (private repo) |
| **Application Code** | Git commits | Indefinite | GitHub (private repo) |

**Backup Testing:**
- **Frequency:** Monthly restore tests
- **Scope:** Full database restore to test environment
- **Validation:** Data integrity verification, application functionality testing
- **Documentation:** Restore procedures documented and updated

**Backup Encryption:**
- All backups encrypted with AWS KMS
- Encryption keys rotated annually
- Backup access requires MFA

---

## 6. Security Testing

### 6.1 Security Testing Strategy

**Continuous Security Testing:**

```
Development → SAST → Dependency Scan → Build → DAST → Deploy → Pen Test
                ↓          ↓                       ↓               ↓
            SonarQube    Snyk              OWASP ZAP      External Firm
```

### 6.2 Static Application Security Testing (SAST)

**SAST Tools:**
- **SonarQube:** Code quality and security vulnerability detection
- **ESLint Security Plugin:** JavaScript/TypeScript security linting
- **Bandit:** Python security linting (if applicable)

**SAST Integration:**
- Runs on every pull request
- Blocks merge if critical security issues found
- Developer receives immediate feedback

**SonarQube Security Rules:**
- OWASP Top 10 coverage
- CWE Top 25 coverage
- SQL injection detection
- XSS vulnerability detection
- Hard-coded credentials detection
- Insecure cryptography detection

**Quality Gates:**
- Security Rating: A (no vulnerabilities)
- Reliability Rating: A
- Maintainability Rating: A
- Coverage: ≥ 80%
- Duplications: ≤ 3%

### 6.3 Dynamic Application Security Testing (DAST)

**DAST Tools:**
- **OWASP ZAP (Zed Attack Proxy):** Automated vulnerability scanning
- **Burp Suite Professional:** Manual security testing

**DAST Scanning Schedule:**
- **Automated Scans:** Weekly on INT environment
- **Full Scans:** Before each release (UAT environment)
- **Targeted Scans:** After significant feature changes

**DAST Test Scenarios:**
1. **Injection Attacks:**
   - SQL injection
   - NoSQL injection
   - Command injection
   - LDAP injection

2. **Authentication Testing:**
   - Brute force attacks
   - Session management flaws
   - Credential stuffing
   - JWT token manipulation

3. **Authorization Testing:**
   - Broken access control
   - Privilege escalation
   - Forced browsing
   - Parameter tampering

4. **Input Validation:**
   - XSS (reflected, stored, DOM-based)
   - XXE (XML External Entity)
   - File upload vulnerabilities
   - Path traversal

5. **Configuration Testing:**
   - HTTP headers security
   - TLS configuration
   - Cookie security flags
   - Error message information disclosure

**DAST Reporting:**
- Vulnerabilities categorized by severity (Critical, High, Medium, Low)
- Remediation guidance provided
- Re-scan after fixes to verify resolution

### 6.4 Dependency Scanning

**Dependency Scanning Tools:**
- **Snyk:** npm package vulnerability scanning
- **npm audit:** Built-in npm security auditing
- **OWASP Dependency-Check:** Software composition analysis

**Scanning Frequency:**
- **Every Build:** Automated in CI/CD pipeline
- **Daily:** Scheduled scans for new vulnerabilities
- **Ad-hoc:** Before major releases

**Vulnerability Management:**
- Critical/High vulnerabilities: Fix within 7 days
- Medium vulnerabilities: Fix within 30 days
- Low vulnerabilities: Fix in next sprint
- False positives: Document and suppress with justification

**Software Bill of Materials (SBOM):**
- Generate SBOM for each release
- Track all dependencies (direct and transitive)
- Monitor for newly disclosed vulnerabilities
- Share SBOM with Sydney Metro for supply chain security

### 6.5 Penetration Testing

**Penetration Testing Approach:**

**Frequency:**
- **Pre-Production:** Before go-live
- **Annual:** After go-live
- **Ad-hoc:** After major architecture changes

**Scope:**
- Web application (Strapi Admin UI)
- REST APIs
- Authentication and authorization
- Network perimeter
- AWS infrastructure configuration

**Testing Methodology:**
- **PTES (Penetration Testing Execution Standard)**
- **OWASP Testing Guide**

**Testing Phases:**
1. **Pre-Engagement:** Define scope, rules of engagement, contact points
2. **Intelligence Gathering:** Reconnaissance, information gathering
3. **Threat Modeling:** Identify attack vectors and prioritize
4. **Vulnerability Analysis:** Identify vulnerabilities
5. **Exploitation:** Attempt to exploit vulnerabilities (with caution)
6. **Post-Exploitation:** Assess impact and lateral movement potential
7. **Reporting:** Detailed findings with remediation recommendations

**Penetration Testing Provider:**
- IRAP-certified security firm
- Experienced with Australian government projects
- Provide detailed technical report and executive summary

**Remediation:**
- Critical findings: Fix within 7 days, re-test within 14 days
- High findings: Fix within 30 days, re-test within 45 days
- Medium findings: Fix within 90 days
- Final report with all fixes verified

### 6.6 Security Code Review

**Code Review Process:**
- All code changes peer-reviewed before merge
- Security-focused review for sensitive components (authentication, authorization, encryption)
- Security checklist used for reviews

**Security Code Review Checklist:**
- [ ] Input validation performed on all user inputs
- [ ] Output encoding applied to prevent XSS
- [ ] Parameterized queries used (no string concatenation)
- [ ] Authentication and authorization checks present
- [ ] Sensitive data encrypted (in transit and at rest)
- [ ] No hard-coded credentials or secrets
- [ ] Error handling doesn't leak sensitive information
- [ ] Security headers configured
- [ ] Rate limiting applied to sensitive endpoints
- [ ] Audit logging for sensitive operations

---

## 7. Incident Response

### 7.1 Incident Response Framework

**Incident Response Lifecycle:**

```
┌─────────────┐   ┌─────────────┐   ┌─────────────┐   ┌─────────────┐   ┌─────────────┐
│Preparation  │──→│  Detection  │──→│Containment  │──→│ Eradication │──→│  Recovery   │
│             │   │  & Analysis │   │             │   │             │   │             │
└─────────────┘   └─────────────┘   └─────────────┘   └─────────────┘   └─────────────┘
                                                                                │
                                                                                ▼
                                                                      ┌─────────────────┐
                                                                      │ Post-Incident   │
                                                                      │ Review          │
                                                                      └─────────────────┘
```

### 7.2 Incident Classification

**Incident Severity Levels:**

| Severity | Definition | Response Time | Examples |
|----------|------------|---------------|----------|
| **P0 - Critical** | Complete system outage, active data breach, severe security compromise | 15 minutes | Production down, data breach, ransomware |
| **P1 - High** | Major functionality impaired, security vulnerability actively exploited | 1 hour | Authentication failure, API down, DDoS attack |
| **P2 - Medium** | Degraded performance, potential security risk | 4 hours | Slow response times, suspicious activity detected |
| **P3 - Low** | Minor issue, no immediate security impact | 24 hours | Failed login attempts, minor config issue |

### 7.3 Incident Response Team

**Incident Response Team (IRT) Structure:**

| Role | Responsibilities | Primary Contact |
|------|------------------|-----------------|
| **Incident Commander** | Overall incident management, decision-making, stakeholder communication | HCL Project Manager |
| **Security Lead** | Security analysis, forensics, remediation coordination | HCL Security Lead |
| **Technical Lead** | Technical troubleshooting, fix implementation | HCL Development Lead |
| **Communications Lead** | Internal/external communications, status updates | HCL Communications Manager |
| **Sydney Metro Liaison** | Sydney Metro stakeholder communication, business impact assessment | Sydney Metro IT Manager |

### 7.4 Incident Response Procedures

**Phase 1: Detection and Analysis (0-1 hour)**

1. **Incident Detection:**
   - Automated alerts (CloudWatch, GuardDuty, Security Hub)
   - Security monitoring tools (SIEM)
   - User reports
   - Third-party notification

2. **Initial Assessment:**
   - Verify incident is genuine (not false positive)
   - Classify severity level
   - Document initial observations
   - Alert Incident Response Team

3. **Incident Declaration:**
   - Incident Commander declares incident
   - Activate IRT war room (virtual or physical)
   - Establish communication channels (dedicated Slack channel, conference bridge)

**Phase 2: Containment (1-4 hours)**

**Short-term Containment:**
- Isolate affected systems (security group changes)
- Block malicious IPs (WAF rules, NACLs)
- Disable compromised accounts
- Preserve evidence (EBS snapshots, memory dumps, logs)

**Long-term Containment:**
- Deploy patches or workarounds
- Implement additional monitoring
- Restore services to limited users (if possible)

**Evidence Preservation:**
- Take snapshots of all affected systems
- Collect logs (CloudWatch, VPC Flow Logs, CloudTrail, application logs)
- Document all actions taken with timestamps
- Preserve chain of custody for forensic analysis

**Phase 3: Eradication (4-24 hours)**

- Identify root cause of incident
- Remove malware, backdoors, or unauthorized access
- Apply security patches
- Change compromised credentials
- Update firewall rules and security policies
- Implement additional security controls

**Phase 4: Recovery (24-72 hours)**

- Restore systems from clean backups (if needed)
- Gradually restore services (phased approach)
- Monitor for signs of persistent compromise
- Verify system integrity
- Return to normal operations

**Phase 5: Post-Incident Review (1 week after resolution)**

- Conduct lessons learned meeting
- Document incident timeline
- Identify gaps in security controls
- Update incident response procedures
- Implement preventive measures
- Share findings with stakeholders

### 7.5 Communication Plan

**Internal Communication:**

| Audience | Update Frequency | Content |
|----------|------------------|---------|
| **IRT Members** | Continuous | Real-time updates in war room |
| **Sydney Metro IT Leadership** | Hourly (P0/P1), Daily (P2/P3) | Status, impact, ETA to resolution |
| **Sydney Metro Business Stakeholders** | Every 4 hours (P0/P1) | Business impact, user communication needed |
| **HCL Leadership** | Daily | Status summary, resource needs |

**External Communication:**

| Scenario | Audience | Approval Required | Timeline |
|----------|----------|-------------------|----------|
| **Service Outage** | All users | Sydney Metro Communications | Within 1 hour of detection |
| **Data Breach** | Affected individuals, OAIC | Sydney Metro Legal & Communications | Within 72 hours (as per Privacy Act) |
| **Security Incident (no breach)** | Internal only | HCL & Sydney Metro leadership | N/A |

**Communication Templates:**

**Initial Notification (P0/P1):**
```
Subject: [INCIDENT] Sydney Metro CMS - [Brief Description]

Severity: [P0/P1]
Start Time: [Timestamp]
Status: [Investigating / Contained / Resolving]

Impact:
- [User impact description]
- [Systems affected]

Current Actions:
- [What's being done]

Next Update: [Timestamp]

Incident Commander: [Name, Contact]
```

**All-Clear Notification:**
```
Subject: [RESOLVED] Sydney Metro CMS - [Brief Description]

The incident has been resolved.

Incident Summary:
- Start: [Timestamp]
- End: [Timestamp]
- Duration: [HH:MM]
- Root Cause: [Brief description]

Actions Taken:
- [List of remediation steps]

Preventive Measures:
- [Future safeguards]

A detailed post-incident report will be provided within 5 business days.
```

### 7.6 Incident Escalation

**Escalation Criteria:**

| Trigger | Escalation Action |
|---------|-------------------|
| No progress after 2 hours | Escalate to HCL Senior Management |
| Data breach confirmed | Escalate to Sydney Metro CISO immediately |
| Media attention | Escalate to Sydney Metro Communications team |
| Legal implications | Escalate to Sydney Metro Legal team |
| Cannot resolve with available resources | Request additional expertise (AWS, security vendor) |

**Escalation Contacts:**

| Level | Role | Contact | Availability |
|-------|------|---------|--------------|
| **L1** | Incident Commander | [Contact] | 24/7 |
| **L2** | HCL Security Lead | [Contact] | 24/7 |
| **L3** | HCL Delivery Manager | [Contact] | Business hours + on-call |
| **L4** | Sydney Metro CISO | [Contact] | 24/7 for P0/P1 |
| **External** | AWS Support (Enterprise) | AWS Console | 24/7 |

### 7.7 Incident Response Training and Drills

**IRT Training:**
- **Frequency:** Quarterly
- **Topics:** Incident response procedures, forensics, communication protocols
- **Format:** Classroom training, hands-on exercises

**Tabletop Exercises:**
- **Frequency:** Semi-annual
- **Scenarios:** Data breach, ransomware attack, DDoS attack, insider threat
- **Participants:** Full IRT + Sydney Metro stakeholders
- **Duration:** 2-3 hours
- **Outcome:** Identify gaps, update procedures

**Full-Scale Incident Simulation:**
- **Frequency:** Annual
- **Scenario:** Realistic security incident
- **Participants:** Full IRT, operations team
- **Duration:** 4-8 hours
- **Outcome:** Test end-to-end response, identify improvements

---

## 8. Security Monitoring and Logging

### 8.1 Security Monitoring Architecture

**Layered Monitoring Approach:**

```
┌─────────────────────────────────────────────────────────────┐
│               Security Information & Event Management        │
│                        (SIEM - AWS Security Hub)            │
├─────────────────────────────────────────────────────────────┤
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │   AWS        │  │  CloudWatch  │  │    VPC       │     │
│  │  GuardDuty   │  │    Logs      │  │  Flow Logs   │     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
│                                                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │  AWS WAF     │  │  CloudTrail  │  │  Application │     │
│  │    Logs      │  │              │  │     Logs     │     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼
          ┌────────────────────────────────┐
          │   Monitoring Dashboard         │
          │   (Grafana + CloudWatch)       │
          └────────────────────────────────┘
                          │
                          ▼
          ┌────────────────────────────────┐
          │  Alerting & Response           │
          │  (SNS, PagerDuty, IRT)         │
          └────────────────────────────────┘
```

### 8.2 Log Collection and Retention

**Log Sources:**

| Log Source | Information Captured | Retention Period | Storage |
|------------|----------------------|------------------|---------|
| **CloudTrail** | All AWS API calls | 7 years | S3 + CloudWatch Logs |
| **VPC Flow Logs** | Network traffic metadata | 90 days | CloudWatch Logs |
| **Application Logs** | Strapi application events, errors | 1 year | CloudWatch Logs |
| **Audit Logs** | User actions (create, edit, publish, delete) | 7 years | CloudWatch Logs + RDS |
| **AWS WAF Logs** | Web requests, blocks, rate limits | 90 days | S3 + CloudWatch Logs |
| **ECS Task Logs** | Container stdout/stderr | 30 days | CloudWatch Logs |
| **RDS Logs** | Database queries, connections, errors | 30 days | CloudWatch Logs |
| **Authentication Logs** | Login attempts, MFA, session management | 2 years | Azure AD + CloudWatch |

**Log Format Standardization:**
- JSON format for all application logs
- ISO 8601 timestamps (UTC)
- Structured logging with consistent fields (timestamp, severity, user, action, resource, result)

**Example Audit Log Entry:**
```json
{
  "timestamp": "2025-10-27T10:30:45.123Z",
  "severity": "INFO",
  "event_type": "content.publish",
  "user_id": "user@sydneymetro.nsw.gov.au",
  "user_role": "Content Editor",
  "resource_type": "news_article",
  "resource_id": "article_12345",
  "action": "publish",
  "result": "success",
  "ip_address": "203.0.113.42",
  "user_agent": "Mozilla/5.0...",
  "session_id": "sess_abc123xyz",
  "metadata": {
    "title": "Metro Expansion Update",
    "language": "en"
  }
}
```

### 8.3 Security Monitoring Tools

**AWS GuardDuty:**
- **Purpose:** Threat detection for AWS accounts and workloads
- **Detects:** Unusual API calls, compromised instances, reconnaissance, unauthorized access
- **Alerting:** Integrated with Security Hub and SNS

**AWS Security Hub:**
- **Purpose:** Centralized security findings aggregation
- **Sources:** GuardDuty, AWS Config, IAM Access Analyzer, Firewall Manager
- **Standards:** CIS AWS Foundations Benchmark, PCI DSS, AWS Foundational Security Best Practices

**AWS Config:**
- **Purpose:** Configuration compliance monitoring
- **Rules:** Custom rules for security compliance (e.g., encryption enabled, MFA required, public access blocked)
- **Remediation:** Automated remediation for non-compliant resources

**Amazon Macie (Optional):**
- **Purpose:** Sensitive data discovery and protection
- **Scope:** S3 buckets (media storage)
- **Detects:** PII, credentials, confidential information in uploaded files

**CloudWatch Alarms:**
- **Purpose:** Real-time alerting on security events
- **Metrics:** Failed login attempts, unusual API calls, high error rates, performance degradation
- **Actions:** SNS notifications, Lambda automation

### 8.4 Security Event Detection

**Security Events to Monitor:**

| Event Category | Specific Events | Alert Threshold | Response |
|----------------|-----------------|-----------------|----------|
| **Authentication** | Failed login attempts | 5 failures in 5 minutes from same IP | Account lockout, alert security team |
| **Authentication** | Login from new location | First time | MFA challenge, log for review |
| **Authorization** | Privilege escalation attempt | Any | Block action, alert security team |
| **Authorization** | Unauthorized API access | Any | Block request, alert security team |
| **Data Access** | Bulk data download | > 1000 records | Require approval, alert security team |
| **Data Access** | After-hours data access | Outside business hours | Log and review |
| **Infrastructure** | Security group changes | Any production change | Alert operations team, verify change approved |
| **Infrastructure** | Root account usage | Any | Immediate alert to security team |
| **Application** | High error rate | > 5% error rate | Alert operations team |
| **Application** | Slow response times | > 2 second average | Alert operations team |
| **Network** | Unusual traffic patterns | 3x normal traffic | DDoS mitigation, alert security team |
| **Network** | Traffic from malicious IPs | Any (threat intel feed) | Block IP, alert security team |

**Anomaly Detection:**
- Machine learning-based anomaly detection (AWS GuardDuty)
- Baseline normal behavior patterns
- Alert on statistically significant deviations

### 8.5 Audit Logging

**Audit Trail Requirements:**

**What to Log:**
- User authentication (login, logout, MFA)
- User actions (create, read, update, delete operations)
- Permission changes
- Configuration changes
- Data exports
- Failed access attempts
- System administration actions

**Audit Log Fields:**
- Timestamp (UTC)
- User identity (email, role)
- Action performed
- Resource affected (type, ID, name)
- Result (success, failure, reason)
- Source IP address
- User agent / client information
- Session ID

**Audit Log Security:**
- Stored in append-only CloudWatch Logs
- Encrypted with AWS KMS
- Access restricted to security team and auditors
- Integrity protection (CloudWatch Logs Insights queries can't modify logs)
- Off-site backup to S3 (cross-region replication optional for critical systems)

**Audit Log Review:**
- **Automated:** Real-time alerting on suspicious activities
- **Weekly:** Security team reviews high-risk user actions
- **Monthly:** Compliance team reviews access patterns
- **Quarterly:** External auditor reviews sample of logs

### 8.6 Security Dashboards and Reporting

**Real-Time Security Dashboard (Grafana):**

**Panel 1: Security Overview**
- Open security findings (by severity)
- Security events in last 24 hours
- Failed authentication attempts
- GuardDuty threats detected

**Panel 2: User Activity**
- Active user sessions
- Top users by activity
- After-hours access
- Failed authorization attempts

**Panel 3: Network Security**
- Traffic volume trends
- Blocked requests (WAF)
- Top source IPs
- Suspicious network activity

**Panel 4: Compliance Status**
- AWS Config compliance score
- Security Hub standards compliance
- Encryption coverage
- Backup success rate

**Panel 5: Vulnerability Management**
- Open vulnerabilities (by severity)
- Time to remediation (average)
- Patching status
- Dependency vulnerabilities

**Security Reports:**

**Daily Security Report:**
- Security events summary
- New threats detected
- Remediation actions taken
- Open security tasks

**Weekly Security Report:**
- Trend analysis (week-over-week)
- Security metrics dashboard
- Vulnerability status
- Compliance posture

**Monthly Security Report:**
- Executive summary
- Key security metrics
- Risk assessment
- Compliance status
- Upcoming security initiatives

**Quarterly Security Review:**
- Comprehensive security assessment
- Threat landscape analysis
- Security program effectiveness
- Improvement recommendations
- Audit readiness status

---

## 9. Compliance Framework

### 9.1 ISO 27001:2022 Compliance

**ISO 27001 Certification Timeline:**
- **Month 3:** Gap analysis
- **Month 6:** Implement missing controls
- **Month 9:** Internal audit
- **Month 12:** External certification audit
- **Ongoing:** Surveillance audits (annual)

**ISO 27001 Annex A Controls Implementation:**

| Control Category | Key Controls | Implementation Status |
|------------------|--------------|----------------------|
| **A.5: Organizational Controls** | Information security policies, roles and responsibilities | Implemented |
| **A.6: People Controls** | Screening, training, disciplinary process | Implemented |
| **A.7: Physical Controls** | Physical security (AWS data centers) | Inherited from AWS |
| **A.8: Technological Controls** | User endpoint security, information deletion | Implemented |
| **A.9: Access Control** | IAM, MFA, RBAC, access reviews | Implemented |
| **A.10: Cryptography** | Encryption at rest and in transit, key management | Implemented |
| **A.11: Physical & Environmental** | Equipment security, utilities (AWS controls) | Inherited from AWS |
| **A.12: Operations Security** | Change management, capacity management, malware protection | Implemented |
| **A.13: Communications Security** | Network security, segregation, data transfer | Implemented |
| **A.14: System Acquisition** | Secure development lifecycle, security testing | Implemented |
| **A.15: Supplier Relationships** | Vendor risk assessment, contracts | Implemented |
| **A.16: Incident Management** | Incident response procedures, forensics | Implemented |
| **A.17: Business Continuity** | DR, backups, redundancy | Implemented |
| **A.18: Compliance** | Legal requirements, audits, technical compliance | Implemented |

**Statement of Applicability (SoA):**
- Documents which Annex A controls are applicable
- Justification for excluded controls
- Implementation details for included controls

### 9.2 IRAP Assessment

**IRAP (Infosec Registered Assessors Program):**

**Purpose:** Independent security assessment for Australian government systems

**Assessment Scope:**
- Full system security architecture
- Technical security controls
- Governance and processes
- Physical security (inherited from AWS)
- Personnel security

**IRAP Assessment Timeline:**
- **Month 6:** Pre-assessment readiness review
- **Month 9:** Formal IRAP assessment
- **Month 10:** Remediate findings
- **Month 11:** Re-assessment (if needed)
- **Month 12:** IRAP report finalized

**ISM (Information Security Manual) Alignment:**

**Essential Eight Maturity:**

| Control | Target Maturity Level | Implementation |
|---------|----------------------|----------------|
| **Application Control** | Level 2 | ECS Fargate (immutable containers), allowed application list |
| **Patch Applications** | Level 2 | Automated patching within 48 hours of release |
| **Microsoft Office Macros** | Level 2 | Macro security settings (user endpoints, not CMS) |
| **User Application Hardening** | Level 2 | Browser security settings, extension restrictions |
| **Restrict Admin Privileges** | Level 2 | RBAC, least privilege, privileged access management |
| **Multi-Factor Authentication** | Level 2 | MFA required for all users (Azure AD) |
| **Regular Backups** | Level 2 | Daily automated backups, tested monthly |
| **Patch Operating Systems** | Level 3 | AWS managed patching for underlying OS (Fargate) |

### 9.3 Australian Privacy Principles (APP) Compliance

**Relevant APPs:**

| APP | Principle | Implementation |
|-----|-----------|----------------|
| **APP 1** | Open and transparent management of personal information | Privacy policy published, data handling documented |
| **APP 2** | Anonymity and pseudonymity | Users can use system with username (not full name visible) |
| **APP 3** | Collection of solicited personal information | Collect only necessary PII (name, email for authentication) |
| **APP 5** | Notification of collection | Users notified at registration |
| **APP 6** | Use or disclosure of personal information | Data used only for CMS purposes |
| **APP 8** | Cross-border disclosure | No data transfer outside Australia |
| **APP 10** | Quality of personal information | Users can update their profile information |
| **APP 11** | Security of personal information | Encryption, access controls, monitoring |
| **APP 12** | Access to personal information | Users can request their data |
| **APP 13** | Correction of personal information | Users can request data corrections |

**Notifiable Data Breaches (NDB) Scheme:**
- If breach likely to result in serious harm, notify OAIC within 72 hours
- Notify affected individuals as soon as practicable
- Maintain breach register

### 9.4 Accessibility Compliance

**WCAG 2.1 Level AA Compliance:**
- Full compliance with Web Content Accessibility Guidelines 2.1 Level AA
- Applies to all user interfaces (Admin panel, Editor interface)
- Automated and manual testing
- Annual third-party accessibility audit

**AS EN 301 549 Compliance:**
- European accessibility standard adopted in Australia
- Aligns with WCAG 2.1 Level AA
- Public sector procurement requirement

### 9.5 Compliance Audits and Assessments

**Internal Audits:**
- **Frequency:** Quarterly
- **Scope:** Security controls, processes, documentation
- **Auditor:** HCL Internal Audit team
- **Output:** Audit report with findings and remediation plan

**External Audits:**
- **ISO 27001 Surveillance Audit:** Annual
- **IRAP Assessment:** Initial + every 3 years
- **Penetration Testing:** Annual
- **Accessibility Audit:** Annual
- **Sydney Metro IT Audit:** As requested

**Compliance Documentation:**
- Information Security Management System (ISMS) documentation
- Security policies, standards, procedures
- Risk register
- Asset inventory
- Incident log
- Audit reports
- Training records
- Access review records

**Compliance Metrics:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| **ISO 27001 Compliance** | 100% of applicable controls | Annual certification audit |
| **IRAP Compliance** | Essential Eight Level 2+ | IRAP assessment |
| **Patch Compliance** | 100% within SLA | Automated scanning |
| **Access Review Compliance** | 100% quarterly reviews completed | Access review records |
| **Training Compliance** | 100% staff trained annually | Training completion records |
| **Backup Success Rate** | 100% successful backups | Backup monitoring |
| **Incident Response Drill** | 2 drills per year | Drill completion records |

---

## Appendices

### Appendix A: Security Tools and Technologies

| Category | Tool/Service | Purpose |
|----------|-------------|---------|
| **Cloud Security** | AWS GuardDuty | Threat detection |
| **Cloud Security** | AWS Security Hub | Security findings aggregation |
| **Cloud Security** | AWS Config | Configuration compliance |
| **SIEM** | AWS Security Hub + CloudWatch | Security monitoring and alerting |
| **SAST** | SonarQube | Static code analysis |
| **DAST** | OWASP ZAP | Dynamic vulnerability scanning |
| **Dependency Scanning** | Snyk | npm package vulnerability scanning |
| **Container Security** | Trivy, AWS ECR Scanning | Container image vulnerability scanning |
| **Secrets Management** | AWS Secrets Manager | Credential storage and rotation |
| **Key Management** | AWS KMS | Encryption key management |
| **Identity Provider** | Azure Active Directory | Authentication and SSO |
| **WAF** | AWS WAF | Web application firewall |
| **DDoS Protection** | AWS Shield, CloudFront | DDoS mitigation |
| **Logging** | CloudWatch Logs, CloudTrail | Centralized logging |
| **Monitoring** | Grafana, CloudWatch Dashboards | Security dashboards |

### Appendix B: Security Contacts

| Role | Contact | Availability |
|------|---------|--------------|
| Security Lead | [Name, Email, Phone] | 24/7 |
| Incident Commander | [Name, Email, Phone] | 24/7 |
| Security Architect | [Name, Email, Phone] | Business hours + on-call |
| AWS Support | AWS Enterprise Support | 24/7 |
| IRAP Assessor | [Firm Name, Contact] | Business hours |
| Penetration Testing Firm | [Firm Name, Contact] | Business hours |

### Appendix C: Security Policies and Standards

- Information Security Policy
- Access Control Policy
- Data Classification and Handling Policy
- Acceptable Use Policy
- Incident Response Policy
- Secure Development Standard
- Encryption Standard
- Password Policy
- Third-Party Risk Management Policy

### Appendix D: Compliance Certificates and Reports

- ISO 27001 Certificate (upon certification)
- IRAP Assessment Report (upon completion)
- Penetration Testing Reports
- Vulnerability Assessment Reports
- Accessibility Compliance Reports

---

**Document End**
