# Technical Proposal
## Sydney Metro CMS Modernization Project

**Prepared by:** HCL Technologies
**Date:** October 2025
**Version:** 1.0

---

## Executive Summary

HCL Technologies proposes a comprehensive, modern, and secure content management solution for Sydney Metro that addresses all key requirements while delivering exceptional performance, security, and user experience. Our solution leverages proven enterprise-grade technologies combined with cloud-native architecture to deliver a scalable, resilient, and compliant platform.

**Key Solution Highlights:**
- **Headless CMS Architecture** using Contentful Enterprise with API-first content delivery
- **Cloud-Native Infrastructure** on AWS Sydney region with multi-AZ deployment
- **Advanced Security** with NSW Identity integration, zero-trust architecture, and comprehensive audit logging
- **High Performance** targeting p95 < 500ms at 500 RPS through intelligent caching and edge delivery
- **Full Compliance** with NSW Government standards, WCAG 2.1 AA accessibility, and data residency requirements
- **Robust DR/BC** with RTO ≤ 4 hours and RPO ≤ 1 hour

---

## 1. Solution Architecture Overview

### 1.1 Architecture Philosophy

Our proposed architecture is built on four core principles:

1. **Cloud-Native First**: Leveraging AWS managed services for scalability, reliability, and reduced operational overhead
2. **API-Driven**: Headless CMS approach enabling omnichannel content delivery and future flexibility
3. **Security by Design**: Zero-trust architecture with defense-in-depth security layers
4. **Performance-Optimized**: Edge caching, static generation, and intelligent rendering strategies

### 1.2 High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        End Users (Public)                        │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                   CloudFront CDN + AWS WAF                       │
│              (Sydney + Melbourne Edge Locations)                 │
│        • DDoS Protection  • Rate Limiting  • Geo-blocking       │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                  Next.js Frontend (ap-southeast-2)               │
│                         Multi-AZ Deployment                      │
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │   AZ-1       │  │    AZ-2      │  │    AZ-3      │         │
│  │  ECS Fargate │  │  ECS Fargate │  │  ECS Fargate │         │
│  │  Tasks       │  │  Tasks       │  │  Tasks       │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
│                                                                  │
│  • Server-Side Rendering (SSR)                                  │
│  • Incremental Static Regeneration (ISR)                        │
│  • Static Site Generation (SSG) for public pages               │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                    API Gateway (AWS ALB + Kong)                  │
│                                                                  │
│  • OIDC/JWT Authentication                                      │
│  • Rate Limiting & Throttling                                   │
│  • Request/Response Transformation                              │
│  • API Analytics & Monitoring                                   │
└────────────────────────────┬────────────────────────────────────┘
                             │
                ┌────────────┴────────────┐
                ▼                         ▼
┌───────────────────────────┐  ┌──────────────────────────┐
│   Contentful CMS          │  │  NSW Identity Service    │
│   (SaaS - AU Region)      │  │  (External Integration)  │
│                           │  │                          │
│  • Content Modeling       │  │  • OIDC Authentication   │
│  • Workflow Engine        │  │  • SAML 2.0 SSO         │
│  • Multi-language         │  │  • User Provisioning     │
│  • Version Control        │  └──────────────────────────┘
│  • Webhook Triggers       │
└───────────┬───────────────┘
            │
            ▼
┌─────────────────────────────────────────────────────────────────┐
│                   Supporting Services (AWS)                      │
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │  S3 Buckets  │  │  RDS Aurora  │  │ OpenSearch   │         │
│  │  (Assets)    │  │  (Metadata)  │  │  (Search)    │         │
│  │              │  │              │  │              │         │
│  │  • Images    │  │  • Analytics │  │  • Full-text │         │
│  │  • Documents │  │  • Audit Log │  │  • Faceted   │         │
│  │  • Media     │  │  • Config    │  │  • Suggest   │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │  Secrets     │  │  CloudWatch  │  │   X-Ray      │         │
│  │  Manager     │  │  Logs/Metrics│  │  (Tracing)   │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
└─────────────────────────────────────────────────────────────────┘
```

### 1.3 Headless CMS: Contentful Enterprise

**Why Contentful?**

We recommend Contentful Enterprise as the headless CMS platform for the following strategic reasons:

**Enterprise-Grade Capabilities:**
- **Proven Scale**: Powers 28% of Fortune 500 companies with 99.99% uptime SLA
- **Content Modeling Flexibility**: Custom content types with complex relationships and validation rules
- **Multi-language Support**: Built-in localization for English, Chinese, and other languages
- **Workflow Engine**: Configurable approval workflows with role-based permissions
- **Version Control**: Full content versioning with rollback capabilities

**Security & Compliance:**
- **SOC 2 Type II Certified**: Independently audited security controls
- **ISO 27001 Certified**: Information security management standards
- **GDPR Compliant**: Data protection and privacy controls
- **Data Residency**: Content served from Australian CDN endpoints
- **Granular RBAC**: Fine-grained access control with audit logging

**Developer Experience:**
- **RESTful & GraphQL APIs**: Flexible content delivery options
- **Comprehensive SDKs**: JavaScript, React, .NET, Java, Python support
- **Webhook System**: Real-time integration with downstream systems
- **Content Preview**: Draft content preview before publishing
- **CLI & Management API**: Infrastructure-as-code and automation support

**Performance Optimization:**
- **Global CDN**: Fastly CDN with Sydney and Melbourne edge locations
- **Intelligent Caching**: Configurable cache headers and invalidation
- **Image Optimization**: Automatic format conversion, resizing, and compression
- **Asset Pipeline**: 50GB storage included, expandable with lifecycle policies

**Alternative Considered: Strapi (Open Source)**

We evaluated Strapi as a self-hosted alternative but recommend against it for this project:

| Factor | Contentful | Strapi |
|--------|-----------|--------|
| Operational Overhead | Managed SaaS | Self-hosted infrastructure required |
| Security Updates | Automatic | Manual patching required |
| Scalability | Automatic | Manual scaling configuration |
| Support | 24/7 Enterprise Support | Community + paid plans |
| Compliance | Pre-certified (SOC 2, ISO 27001) | Self-certification required |
| Total Cost | Higher licensing, lower operations | Lower licensing, higher operations |

**Decision**: Contentful Enterprise provides superior operational efficiency, security, and compliance posture while reducing Sydney Metro's long-term maintenance burden.

### 1.4 Cloud Infrastructure: AWS Sydney Region

**Regional Strategy:**

- **Primary Region**: ap-southeast-2 (Sydney)
- **DR Region**: ap-southeast-4 (Melbourne) for DR failover
- **Multi-AZ Deployment**: All critical components across 3 availability zones

**Core AWS Services:**

| Service | Purpose | Configuration |
|---------|---------|---------------|
| **VPC** | Network isolation | 10.0.0.0/16 with public/private/data subnets |
| **ECS Fargate** | Container hosting | Auto-scaling 2-10 tasks, 2 vCPU, 4GB RAM |
| **Application Load Balancer** | Traffic distribution | Cross-AZ with health checks every 30s |
| **CloudFront** | CDN & edge caching | 50+ global edge locations, Sydney origin |
| **S3** | Asset storage | Versioning enabled, lifecycle policies |
| **RDS Aurora PostgreSQL** | Metadata & analytics | Multi-AZ, automated backups, read replicas |
| **OpenSearch** | Full-text search | 3-node cluster across AZs |
| **Secrets Manager** | Credential management | Automatic rotation, encryption at rest |
| **CloudWatch** | Observability | Logs, metrics, alarms, dashboards |
| **X-Ray** | Distributed tracing | End-to-end request tracing |
| **WAF** | Web application firewall | OWASP Top 10 rules, rate limiting |
| **Route 53** | DNS management | Health checks, failover routing |

**Infrastructure as Code:**

All infrastructure will be defined using **AWS CDK (TypeScript)**, providing:
- Version-controlled infrastructure definitions
- Automated deployments via CI/CD pipeline
- Environment parity (dev, staging, production)
- Disaster recovery automation
- Cost estimation and optimization

### 1.5 Frontend: Next.js with Hybrid Rendering

**Framework Selection: Next.js 14**

Next.js provides the optimal balance of performance, SEO, and developer experience:

**Key Capabilities:**
- **Server-Side Rendering (SSR)**: Dynamic content with fresh data on each request
- **Incremental Static Regeneration (ISR)**: Static pages with periodic updates
- **Static Site Generation (SSG)**: Pre-rendered pages for maximum performance
- **Edge Runtime**: Middleware execution at CloudFront edge locations
- **Image Optimization**: Automatic responsive images with next/image
- **Internationalization**: Built-in i18n routing for multi-language support

**Rendering Strategy by Content Type:**

| Content Type | Strategy | Rationale | Revalidation |
|--------------|----------|-----------|--------------|
| Homepage | ISR | Balance freshness and performance | 60 seconds |
| Service Pages | ISR | Moderate update frequency | 300 seconds |
| News/Updates | SSR | Frequently changing content | On-demand |
| Help/FAQ | SSG | Static, rarely changing | On content update |
| Timetables | SSR | Real-time accuracy required | On-demand |
| Contact Forms | SSR | Dynamic, user-specific | On-demand |

**Performance Optimizations:**
- Code splitting with automatic chunking
- Lazy loading for below-the-fold content
- Prefetching for critical navigation paths
- Service worker for offline functionality
- Resource hints (preconnect, prefetch, preload)

**Technology Stack:**
- **React 18**: Component framework with concurrent rendering
- **TypeScript**: Type safety and improved developer experience
- **Tailwind CSS**: Utility-first styling with design system
- **React Hook Form**: Performant form handling with validation
- **Axios**: HTTP client with request/response interceptors
- **React Query**: Server state management and caching
- **Jest + React Testing Library**: Unit and integration testing

### 1.6 CDN and Security: CloudFront + AWS WAF

**Amazon CloudFront Configuration:**

**Global Edge Network:**
- 50+ edge locations in Asia-Pacific region
- 10+ regional edge caches
- Sub-50ms latency for 90% of Australian users

**Caching Strategy:**

| Content Type | Cache TTL | Cache-Control Headers |
|--------------|-----------|----------------------|
| Static Assets (JS, CSS, Images) | 1 year | immutable, max-age=31536000 |
| HTML Pages (SSG/ISR) | 60-300s | public, s-maxage=60, stale-while-revalidate |
| API Responses | No cache | no-store, must-revalidate |
| Media Files | 1 week | public, max-age=604800 |

**Cache Invalidation:**
- Webhook-triggered invalidation on content publish
- Pattern-based invalidation for related content
- Cost-optimized using path patterns instead of full purge

**AWS WAF Configuration:**

**Managed Rule Groups:**
- AWS Core Rule Set (CRS) - OWASP Top 10 protection
- Known Bad Inputs - CVE-based attack signatures
- SQL Database - SQL injection protection
- Linux Operating System - OS-specific attacks
- POSIX Operating System - Shell command injection

**Custom Rules:**
- Rate limiting: 2000 requests per 5 minutes per IP
- Geo-blocking: Allow Australia, New Zealand, Pacific Islands
- Bot detection: Challenge automated traffic
- IP reputation: Block known malicious IPs

**DDoS Protection:**
- AWS Shield Standard (included, layer 3/4 protection)
- AWS Shield Advanced (optional upgrade for layer 7 protection)
- Real-time attack notifications and DDoS Response Team (DRT) support

### 1.7 Security Architecture: Zero-Trust Model

**Authentication & Authorization:**

**NSW Identity Integration (Primary):**
- **Protocol**: OIDC (OpenID Connect) with PKCE flow
- **Fallback**: SAML 2.0 for legacy systems
- **Session Management**: JWT tokens with 1-hour expiry, refresh tokens with 24-hour expiry
- **MFA Support**: Delegated to NSW Identity service
- **Attribute Mapping**:
  - `sub` → User ID
  - `email` → Email address
  - `given_name`, `family_name` → User profile
  - `groups` → Role assignments

**Role-Based Access Control (RBAC):**

| Role | Permissions | Typical Users |
|------|-------------|---------------|
| **Super Admin** | Full system access, user management, settings | IT administrators |
| **Content Admin** | Content CRUD, workflow management, publishing | Senior content managers |
| **Content Editor** | Content create/edit, submit for approval | Content creators |
| **Content Reviewer** | Review and approve content | Content managers |
| **Analyst** | Read-only, analytics access | Business analysts |
| **API Consumer** | Read-only API access | External integrations |

**Network Security:**

**VPC Architecture:**
```
VPC (10.0.0.0/16)
├── Public Subnets (10.0.0.0/20) - AZ A, B, C
│   ├── Application Load Balancer
│   └── NAT Gateways
├── Private Subnets (10.0.16.0/20) - AZ A, B, C
│   ├── ECS Fargate Tasks
│   └── Application Servers
└── Data Subnets (10.0.32.0/20) - AZ A, B, C
    ├── RDS Aurora
    └── OpenSearch
```

**Security Groups:**
- ALB Security Group: Allow 443 from 0.0.0.0/0, 80 from 0.0.0.0/0 (redirect to HTTPS)
- Application Security Group: Allow 3000 from ALB Security Group only
- Database Security Group: Allow 5432 from Application Security Group only
- OpenSearch Security Group: Allow 9200 from Application Security Group only

**Secrets Management:**

- **AWS Secrets Manager**: Store API keys, database credentials, OAuth secrets
- **Automatic Rotation**: 90-day rotation for database credentials
- **Encryption**: AES-256 encryption at rest using AWS KMS
- **Access Logging**: All secret access logged to CloudWatch
- **Least Privilege**: IAM policies grant minimal required permissions

**Data Encryption:**

| Layer | Encryption Method | Key Management |
|-------|-------------------|----------------|
| **In Transit** | TLS 1.3 | AWS Certificate Manager |
| **At Rest - S3** | AES-256 | AWS KMS (CMK) |
| **At Rest - RDS** | AES-256 | AWS KMS (CMK) |
| **At Rest - OpenSearch** | AES-256 | AWS KMS (CMK) |
| **Backups** | AES-256 | AWS KMS (CMK) |
| **Application Secrets** | AES-256 | AWS KMS (CMK) |

**Audit Logging:**

All security-relevant events logged to CloudWatch with 7-year retention:
- Authentication events (login, logout, failed attempts)
- Authorization decisions (access granted/denied)
- Content changes (create, update, delete, publish)
- Configuration changes (settings, permissions, roles)
- Administrative actions (user management, system config)
- API access (endpoint, user, timestamp, response)

---

## 2. Content Migration Strategy

### 2.1 Migration Approach Overview

Our content migration strategy follows a proven **four-phase approach**:

1. **Discovery & Audit** - Inventory existing content and assess quality
2. **Design & Mapping** - Define target content model and transformation rules
3. **ETL Pipeline Development** - Build automated migration tooling
4. **Parallel Publishing & Cutover** - Gradual transition with rollback capability

### 2.2 Phase 1: Discovery & Audit

**Content Inventory Process:**

**Automated Discovery:**
- Web crawler to inventory all public pages (using Scrapy framework)
- CMS database export for content metadata
- Asset repository scan for media files
- Sitemap analysis for page hierarchy

**Content Audit Metrics:**

| Metric | Collection Method | Purpose |
|--------|-------------------|---------|
| **Page Count** | Crawler + CMS | Migration scope sizing |
| **Content Types** | Manual classification | Content model design |
| **Word Count** | Automated analysis | Effort estimation |
| **Asset Count & Size** | File system scan | Storage planning |
| **Broken Links** | Link checker | Quality issues |
| **Duplicate Content** | Content hashing | Deduplication opportunities |
| **Last Updated Date** | CMS metadata | Content freshness assessment |
| **Page Views** | Analytics export | Priority ranking |

**Quality Assessment:**

For each content item, we will score:
- **Relevance**: Does content align with current Metro objectives? (1-5)
- **Accuracy**: Is information current and correct? (1-5)
- **Completeness**: Are all required fields populated? (1-5)
- **Accessibility**: Does content meet WCAG 2.1 AA? (Pass/Fail)

**Content Decision Matrix:**

| Score Range | Decision | Action |
|-------------|----------|--------|
| 12-15 | Migrate as-is | Automated migration |
| 8-11 | Migrate with updates | Manual review and editing |
| 4-7 | Consolidate or rewrite | Content strategy review |
| 0-3 | Archive or discard | Redirect to relevant page |

**Deliverable**: Content Audit Report with:
- Inventory spreadsheet (title, URL, content type, quality score)
- Recommendations for content consolidation
- Asset manifest with file sizes and formats
- Broken link report

### 2.3 Phase 2: Design & Mapping

**Content Model Design:**

Based on Sydney Metro's needs, we propose the following Contentful content types:

**Core Content Types:**

1. **Page** (Generic content page)
   - Title (Short Text)
   - Slug (Short Text, URL-friendly)
   - Meta Description (Short Text, 160 chars)
   - Hero Image (Media)
   - Body (Rich Text with embedded assets)
   - Sidebar Modules (References to Callout, Download, RelatedLinks)
   - SEO Fields (og:title, og:description, og:image)

2. **NewsArticle**
   - Title, Slug, Meta Description
   - Publish Date (Date/Time)
   - Featured Image (Media)
   - Summary (Long Text, 300 chars)
   - Body (Rich Text)
   - Categories (References to Category)
   - Author (Reference to Author)

3. **ServicePage** (Train services, stations)
   - Service Name, Slug
   - Service Type (Dropdown: Metro, Bus, Ferry)
   - Service Description (Rich Text)
   - Timetable Link (Short Text, URL)
   - Station List (References to Station)
   - Maps (Media, multiple)

4. **Station**
   - Station Name, Code
   - Address (Location, lat/long)
   - Facilities (Multi-select: Lift, Escalator, Parking, Bike Storage)
   - Operating Hours (Short Text)
   - Station Image (Media)
   - Accessibility Information (Rich Text)

5. **HelpArticle** (FAQ, guides)
   - Question (Short Text)
   - Answer (Rich Text)
   - Category (Reference to Category)
   - Related Articles (References to HelpArticle)
   - Helpful Vote Count (Number)

6. **Event**
   - Event Name, Slug
   - Event Date/Time (Date/Time)
   - Location (Short Text or Reference to Station)
   - Description (Rich Text)
   - Registration Link (Short Text, URL)
   - Event Type (Dropdown: Maintenance, Service Change, Community)

**Supporting Content Types:**

7. **Category** (Taxonomy)
   - Name (Short Text)
   - Parent Category (Reference to Category, optional)

8. **Author**
   - Name (Short Text)
   - Bio (Long Text)
   - Photo (Media)
   - Email (Short Text)

9. **Callout** (Reusable component)
   - Title (Short Text)
   - Message (Long Text)
   - Type (Dropdown: Info, Warning, Success, Error)
   - Link (Short Text, URL, optional)

10. **Download**
    - Title (Short Text)
    - File (Media, PDF/DOC)
    - Description (Long Text)
    - File Size (Short Text, auto-populated)

**Content Relationship Diagram:**

```
Page
├── Hero Image (Media)
├── Body (Rich Text)
└── Sidebar Modules
    ├── Callout
    ├── Download
    └── RelatedLinks

NewsArticle
├── Featured Image (Media)
├── Categories (Category)
└── Author (Author)

ServicePage
├── Maps (Media)
└── Station List (Station)

HelpArticle
├── Category (Category)
└── Related Articles (HelpArticle)

Event
├── Location (Station or text)
└── Event Type (Category)
```

**Field Mapping Specification:**

Example mapping from legacy CMS to Contentful:

| Legacy Field | Contentful Field | Transformation Rule |
|--------------|------------------|---------------------|
| `post_title` | `Page.title` | Direct copy |
| `post_name` | `Page.slug` | Slugify (lowercase, hyphens) |
| `post_content` | `Page.body` | HTML to Contentful Rich Text |
| `post_excerpt` | `Page.metaDescription` | Truncate to 160 chars |
| `featured_image_url` | `Page.heroImage` | Upload asset, store reference |
| `post_date` | `NewsArticle.publishDate` | ISO 8601 format |
| `post_category` | `NewsArticle.categories` | Lookup Category by name |
| `custom_field_x` | `ServicePage.serviceType` | Map value to enum |

**Rich Text Transformation:**

Legacy HTML will be converted to Contentful Rich Text JSON:

```javascript
// Example transformation
// Input HTML: <h2>Heading</h2><p>Paragraph with <a href="/link">link</a></p>

// Output Contentful Rich Text JSON:
{
  "nodeType": "document",
  "content": [
    {
      "nodeType": "heading-2",
      "content": [{ "nodeType": "text", "value": "Heading" }]
    },
    {
      "nodeType": "paragraph",
      "content": [
        { "nodeType": "text", "value": "Paragraph with " },
        {
          "nodeType": "hyperlink",
          "data": { "uri": "/link" },
          "content": [{ "nodeType": "text", "value": "link" }]
        }
      ]
    }
  ]
}
```

### 2.4 Phase 3: ETL Pipeline Development

**Migration Architecture:**

```
┌──────────────┐
│ Legacy CMS   │
│  Database    │
└──────┬───────┘
       │ Export (SQL/CSV)
       ▼
┌──────────────────┐     ┌──────────────────┐
│  Extract Module  │────→│  Transform Module │
│                  │     │                   │
│  • Read CSV/JSON │     │  • Map fields     │
│  • Download      │     │  • Clean data     │
│    assets        │     │  • Validate       │
│  • Parse HTML    │     │  • Rich text      │
└──────────────────┘     │    conversion     │
                         └─────────┬──────────┘
                                   │
                                   ▼
                         ┌──────────────────┐
                         │   Load Module    │
                         │                  │
                         │  • Upload assets │
                         │    to S3         │
                         │  • Create entries│
                         │    in Contentful │
                         │  • Link references│
                         │  • Publish       │
                         └──────────────────┘
                                   │
                                   ▼
                         ┌──────────────────┐
                         │  Validation DB   │
                         │  (PostgreSQL)    │
                         │                  │
                         │  • Track progress│
                         │  • Error logging │
                         │  • Rollback data │
                         └──────────────────┘
```

**ETL Pipeline Implementation:**

**Technology Stack:**
- **Python 3.11** - Primary scripting language
- **Pandas** - Data manipulation and transformation
- **BeautifulSoup4** - HTML parsing
- **Contentful Management API** - Content creation
- **Boto3** - AWS S3 asset upload
- **SQLAlchemy** - Database ORM for tracking
- **Celery** - Distributed task queue for parallel processing
- **Redis** - Task queue backend

**Pipeline Features:**

1. **Idempotency**: Rerunning the pipeline multiple times produces the same result
   - Check for existing entries by source ID before creating
   - Use upsert operations (create if not exists, update if exists)
   - Content versioning to track changes

2. **Parallel Processing**: Process multiple content items concurrently
   - Celery workers for distributed processing
   - 10 parallel workers (configurable)
   - Estimated throughput: 100 pages/minute

3. **Error Handling**: Robust error recovery and logging
   - Retry failed operations (3 attempts with exponential backoff)
   - Log errors to database with context (source ID, error message, stack trace)
   - Continue processing on partial failures
   - Generate error report for manual resolution

4. **Progress Tracking**: Monitor migration progress in real-time
   - Dashboard showing items processed, remaining, failed
   - Estimated time to completion
   - Per-content-type statistics

5. **Validation**: Ensure data quality post-migration
   - Schema validation against Contentful content model
   - Link integrity checks (all internal links resolve)
   - Asset availability checks (all media files uploaded)
   - Content completeness (required fields populated)

**Migration Script Example:**

```python
# Simplified migration script structure

class ContentMigrator:
    def __init__(self, contentful_client, s3_client, db_session):
        self.contentful = contentful_client
        self.s3 = s3_client
        self.db = db_session

    def migrate_page(self, legacy_page):
        # Check if already migrated
        if self.db.query(MigrationLog).filter_by(
            source_id=legacy_page['id'],
            status='completed'
        ).first():
            return {'status': 'skipped', 'reason': 'already migrated'}

        try:
            # Transform data
            transformed = self.transform_page(legacy_page)

            # Upload assets
            if transformed['hero_image']:
                transformed['hero_image'] = self.upload_asset(
                    transformed['hero_image']
                )

            # Create or update Contentful entry
            entry = self.contentful.entries().create(
                'page',
                {
                    'fields': {
                        'title': {'en-US': transformed['title']},
                        'slug': {'en-US': transformed['slug']},
                        'body': {'en-US': transformed['body']},
                        # ... other fields
                    }
                }
            )

            # Publish entry
            entry.publish()

            # Log success
            self.db.add(MigrationLog(
                source_id=legacy_page['id'],
                contentful_id=entry.id,
                status='completed'
            ))
            self.db.commit()

            return {'status': 'success', 'entry_id': entry.id}

        except Exception as e:
            # Log error
            self.db.add(MigrationLog(
                source_id=legacy_page['id'],
                status='failed',
                error_message=str(e)
            ))
            self.db.commit()

            return {'status': 'error', 'message': str(e)}

    def transform_page(self, legacy_page):
        # Field mapping and transformation logic
        return {
            'title': legacy_page['post_title'],
            'slug': self.slugify(legacy_page['post_name']),
            'body': self.html_to_rich_text(legacy_page['post_content']),
            'hero_image': legacy_page['featured_image_url'],
            # ...
        }

    def html_to_rich_text(self, html):
        # Convert HTML to Contentful Rich Text JSON
        # Implementation details...
        pass

    def upload_asset(self, url):
        # Download asset from legacy system
        # Upload to S3
        # Create Contentful asset
        # Return asset reference
        pass
```

### 2.5 URL Redirect Management

**Redirect Strategy:**

To maintain SEO value and prevent broken links, we will implement comprehensive URL redirects:

**Redirect Types:**

1. **1:1 Redirects** - Legacy URL maps to single new URL
   - Example: `/old-services/train` → `/services/metro-train`
   - HTTP 301 (Permanent Redirect)

2. **Consolidation Redirects** - Multiple legacy URLs map to single new URL
   - Example: `/help/faq1`, `/help/faq2` → `/help/faqs`
   - HTTP 301 (Permanent Redirect)

3. **Gone Pages** - Content no longer exists, redirect to relevant category
   - Example: `/old-promo` → `/services` (or 410 Gone)
   - HTTP 301 to category or HTTP 410 Gone

**Redirect Implementation:**

**Option 1: CloudFront Functions (Recommended)**
- Lightweight JavaScript executed at CloudFront edge
- Sub-millisecond latency overhead
- No additional infrastructure cost
- Example:

```javascript
function handler(event) {
    var request = event.request;
    var uri = request.uri;

    // Redirect map
    var redirects = {
        '/old-services/train': '/services/metro-train',
        '/help/faq1': '/help/faqs',
        // ... (up to 10KB function size)
    };

    if (redirects[uri]) {
        return {
            statusCode: 301,
            statusDescription: 'Moved Permanently',
            headers: {
                'location': { value: redirects[uri] }
            }
        };
    }

    return request;
}
```

**Option 2: Lambda@Edge (For complex rules)**
- Full Node.js runtime for complex logic
- Regex pattern matching
- Database lookups for dynamic redirects
- Higher latency (5-10ms) and cost

**Option 3: Application-Level (Next.js)**
- Redirects defined in `next.config.js`
- Supports regex patterns and wildcard matching
- Example:

```javascript
// next.config.js
module.exports = {
    async redirects() {
        return [
            {
                source: '/old-services/:path*',
                destination: '/services/:path*',
                permanent: true,
            },
            {
                source: '/news/:year/:month/:slug',
                destination: '/news/:slug',
                permanent: true,
            },
        ];
    },
};
```

**Redirect Testing:**

- Automated testing of all redirects using Playwright
- Validate correct status code (301 vs 302)
- Verify destination URL is accessible (200 OK)
- Check redirect chain (max 1 hop, no loops)

**Redirect Documentation:**

Maintain a **Redirect Registry** in CSV format:

| Legacy URL | New URL | Redirect Type | Status Code | Reason |
|------------|---------|---------------|-------------|--------|
| /old-services/train | /services/metro-train | 1:1 | 301 | URL restructure |
| /help/faq1 | /help/faqs | Consolidation | 301 | Content merged |
| /old-promo | /services | Category | 301 | Content removed |

### 2.6 Data Validation & Quality Assurance

**Validation Checklist:**

**Content Integrity:**
- [ ] All legacy pages migrated (count matches inventory)
- [ ] No data loss in field mapping (spot-check 10% sample)
- [ ] Rich text formatting preserved (headings, lists, links)
- [ ] Special characters encoded correctly (quotes, apostrophes, em dashes)

**Asset Integrity:**
- [ ] All images uploaded to S3 (count matches inventory)
- [ ] Image dimensions preserved or optimized
- [ ] File names sanitized (no spaces, special characters)
- [ ] Alt text migrated for accessibility

**Link Integrity:**
- [ ] Internal links updated to new URLs
- [ ] External links functional (HTTP 200 OK)
- [ ] No broken links (404 errors)
- [ ] Anchor links functional (#section-id)

**Content Relationships:**
- [ ] Category assignments correct
- [ ] Author assignments correct
- [ ] Related content links functional
- [ ] Tag associations preserved

**SEO Metadata:**
- [ ] Page titles present (50-60 characters)
- [ ] Meta descriptions present (150-160 characters)
- [ ] Open Graph tags populated
- [ ] Canonical URLs set correctly

**Automated Validation Tools:**

1. **Content Comparison Script**
   - Compare legacy HTML vs. new Contentful content
   - Calculate similarity score (Levenshtein distance)
   - Flag pages with < 90% similarity for manual review

2. **Link Checker**
   - Crawl all migrated pages
   - Validate all links (internal and external)
   - Generate broken link report

3. **Asset Verification**
   - Compare asset counts (legacy vs. S3)
   - Verify file hashes match (no corruption)
   - Check for missing assets

4. **Schema Validator**
   - Validate all entries against Contentful content model
   - Check required fields populated
   - Verify field types correct (e.g., date fields are valid dates)

### 2.7 Parallel Publishing & Cutover

**Transition Strategy:**

To minimize risk, we propose a **gradual cutover** approach:

**Phase 1: Parallel Publishing (2 weeks)**
- Both legacy and new CMS operational
- Content updates made in both systems
- Sync script runs every 15 minutes
- Internal testing on new system (staff-only access)

**Phase 2: Beta Launch (1 week)**
- 10% of traffic routed to new system (via CloudFront weighted routing)
- Monitor errors, performance, user feedback
- Content updates still synced between systems
- Rollback capability if issues detected

**Phase 3: Gradual Rollout (1 week)**
- Increase traffic to new system: 25% → 50% → 75% → 100%
- Monitor at each stage (24-hour soak period)
- Disable content sync after 75% cutover
- Legacy CMS set to read-only

**Phase 4: Decommissioning (2 weeks post-cutover)**
- Legacy CMS remains read-only for 2 weeks
- Export final archive for records
- Decommission legacy infrastructure

**Rollback Plan:**

If critical issues arise, we can rollback within 15 minutes:

1. Update CloudFront distribution to point to legacy origin
2. Wait for edge cache propagation (5-10 minutes)
3. Verify legacy system operational
4. Investigate and resolve issues in new system
5. Re-plan cutover after resolution

**Cutover Checklist:**

- [ ] All content migrated and validated
- [ ] All redirects implemented and tested
- [ ] DNS TTL reduced to 300 seconds (24 hours before cutover)
- [ ] Staff trained on new CMS
- [ ] Monitoring dashboards configured
- [ ] On-call support team identified
- [ ] Communication plan executed (internal and external)
- [ ] Rollback procedures documented and rehearsed

---

## 3. Security and Compliance

### 3.1 NSW Identity Integration

**Integration Architecture:**

```
┌─────────────┐                  ┌─────────────────┐
│   User      │                  │  NSW Identity   │
│   Browser   │                  │    Service      │
└──────┬──────┘                  └────────┬────────┘
       │                                  │
       │ 1. Initiate Login                │
       ├─────────────────────────────────►│
       │                                  │
       │ 2. Redirect to NSW Identity     │
       │◄─────────────────────────────────┤
       │                                  │
       │ 3. Authenticate (username/pw/MFA)│
       ├─────────────────────────────────►│
       │                                  │
       │ 4. Authorization Code            │
       │◄─────────────────────────────────┤
       │                                  │
       ▼                                  │
┌─────────────────┐                      │
│   Next.js App   │                      │
│   (Backend)     │                      │
└────────┬────────┘                      │
         │ 5. Exchange Code for Tokens   │
         ├──────────────────────────────►│
         │                                │
         │ 6. Access Token + ID Token     │
         │◄───────────────────────────────┤
         │                                │
         │ 7. Fetch User Info (optional)  │
         ├───────────────────────────────►│
         │                                │
         │ 8. User Profile                │
         │◄───────────────────────────────┤
         │                                │
         ▼
   [Create Session]
   [Set Secure Cookie]
```

**OIDC Configuration:**

| Parameter | Value |
|-----------|-------|
| **Authorization Endpoint** | `https://identity.nsw.gov.au/oauth2/authorize` |
| **Token Endpoint** | `https://identity.nsw.gov.au/oauth2/token` |
| **UserInfo Endpoint** | `https://identity.nsw.gov.au/oauth2/userinfo` |
| **JWKS URI** | `https://identity.nsw.gov.au/.well-known/jwks.json` |
| **Scopes** | `openid profile email` |
| **Response Type** | `code` (Authorization Code Flow) |
| **PKCE** | Required (code_challenge_method: S256) |
| **Client Authentication** | `client_secret_post` |

**Token Validation:**

All ID tokens and access tokens will be validated:
- Signature verification using NSW Identity JWKS
- Issuer check (`iss` claim matches NSW Identity)
- Audience check (`aud` claim matches client ID)
- Expiration check (`exp` claim not in past)
- Not-before check (`nbf` claim not in future)
- Nonce validation (prevent replay attacks)

**Session Management:**

- **Session Storage**: Redis cluster (multi-AZ)
- **Session TTL**: 1 hour (configurable)
- **Refresh Token**: 24 hours (configurable)
- **Secure Cookies**: HttpOnly, Secure, SameSite=Strict
- **Session Fixation Prevention**: New session ID on privilege escalation

**Implementation (Next.js + NextAuth.js):**

```typescript
// pages/api/auth/[...nextauth].ts
import NextAuth from 'next-auth';
import { OAuthConfig } from 'next-auth/providers';

const NSWIdentityProvider: OAuthConfig = {
    id: 'nsw-identity',
    name: 'NSW Identity',
    type: 'oauth',
    wellKnown: 'https://identity.nsw.gov.au/.well-known/openid-configuration',
    authorization: {
        params: {
            scope: 'openid profile email',
            code_challenge_method: 'S256',
        },
    },
    clientId: process.env.NSW_IDENTITY_CLIENT_ID,
    clientSecret: process.env.NSW_IDENTITY_CLIENT_SECRET,
    profile(profile) {
        return {
            id: profile.sub,
            name: `${profile.given_name} ${profile.family_name}`,
            email: profile.email,
            roles: profile.groups || [],
        };
    },
};

export default NextAuth({
    providers: [NSWIdentityProvider],
    session: {
        strategy: 'jwt',
        maxAge: 3600, // 1 hour
    },
    callbacks: {
        async jwt({ token, account, profile }) {
            if (account && profile) {
                token.accessToken = account.access_token;
                token.roles = profile.groups || [];
            }
            return token;
        },
        async session({ session, token }) {
            session.accessToken = token.accessToken;
            session.user.roles = token.roles;
            return session;
        },
    },
});
```

### 3.2 Data Residency Compliance

**Australian Data Sovereignty Requirements:**

All data will be stored and processed within Australian regions:

| Data Type | Storage Location | Backup Location | Transit Path |
|-----------|------------------|-----------------|--------------|
| **Content** | Contentful AU CDN | Contentful AU datacenter | Sydney → Melbourne (if DR) |
| **Assets** | S3 ap-southeast-2 (Sydney) | S3 ap-southeast-4 (Melbourne) | Intra-region only |
| **User Data** | RDS ap-southeast-2 (Sydney) | RDS ap-southeast-4 (Melbourne) | Encrypted replication |
| **Logs** | CloudWatch ap-southeast-2 | S3 Glacier ap-southeast-2 | Within region |
| **Analytics** | RDS ap-southeast-2 | S3 ap-southeast-2 | Within region |

**Compliance Measures:**

1. **S3 Block Public Access**: Enabled at bucket and account level
2. **VPC Endpoints**: S3 and RDS accessed via private endpoints (no internet routing)
3. **Bucket Policies**: Deny requests from outside AU regions
4. **AWS Organizations SCP**: Service control policies prevent region restrictions
5. **Data Classification**: All data tagged with classification level (Public, Internal, Confidential)

**Third-Party Data Processing Agreements:**

- **Contentful**: Data Processing Agreement (DPA) in place, GDPR-compliant
- **AWS**: Customer Agreement covers data residency commitments
- **Cloudflare** (if used): Enterprise agreement with AU data processing clause

### 3.3 Security Testing Framework

**SAST (Static Application Security Testing):**

**Tools:**
- **SonarQube** - Code quality and security analysis
- **Semgrep** - Custom security rules for JavaScript/TypeScript
- **npm audit** - Dependency vulnerability scanning
- **Trivy** - Container image scanning

**Integration Points:**
- Pre-commit hooks: Run Semgrep on changed files
- Pull request checks: SonarQube quality gate (no critical/high vulnerabilities)
- CI pipeline: Full scan on every commit to main branch
- Scheduled: Weekly deep scan with updated rule sets

**SAST Policy:**
- **Critical vulnerabilities**: Build fails, immediate remediation required
- **High vulnerabilities**: Build fails, remediation within 48 hours
- **Medium vulnerabilities**: Warning, remediation within 2 weeks
- **Low vulnerabilities**: Informational, remediation at discretion

**DAST (Dynamic Application Security Testing):**

**Tools:**
- **OWASP ZAP** - Automated web application scanner
- **Burp Suite Professional** - Manual penetration testing
- **Nuclei** - Fast vulnerability scanner with templates

**Testing Frequency:**
- **Automated DAST**: Nightly scans against staging environment
- **Manual Penetration Testing**: Quarterly by certified ethical hackers (CEH/OSCP)
- **Bug Bounty Program**: Public program after initial launch (HackerOne or Bugcrowd)

**DAST Coverage:**
- OWASP Top 10 vulnerabilities (SQL injection, XSS, CSRF, etc.)
- Authentication and session management flaws
- Authorization bypass attempts
- API security testing (GraphQL/REST)
- Business logic vulnerabilities

**DAST Reporting:**
- Vulnerability reports generated automatically
- Severity classification (Critical, High, Medium, Low, Informational)
- Proof-of-concept (PoC) for each finding
- Remediation recommendations with code examples

**Security Testing Schedule:**

| Test Type | Frequency | Environment | Responsible Party |
|-----------|-----------|-------------|-------------------|
| SAST - Automated | Every commit | CI/CD | Development team |
| SAST - Deep scan | Weekly | CI/CD | Security team |
| DAST - Automated | Nightly | Staging | Security team |
| DAST - Manual pentest | Quarterly | Staging | External pentest firm |
| Vulnerability scanning | Weekly | Production | Security team |
| Security audit | Annually | Production | External auditor |

### 3.4 Audit Logging and Monitoring

**Audit Log Requirements:**

All audit logs will capture the following attributes:
- **Timestamp**: ISO 8601 format with timezone (e.g., 2025-10-27T14:30:00+11:00)
- **Event Type**: Authentication, Authorization, Content Change, Configuration Change, etc.
- **User Identity**: User ID, email, IP address, user agent
- **Action**: Specific action performed (e.g., "content.published")
- **Resource**: Resource affected (e.g., page ID, asset ID)
- **Result**: Success or failure
- **Context**: Additional metadata (e.g., before/after values for changes)

**Audit Event Categories:**

**1. Authentication Events:**
- Login success/failure
- Logout
- Session expiration
- Password reset
- MFA challenge success/failure

**2. Authorization Events:**
- Access granted to resource
- Access denied to resource (with reason)
- Permission change
- Role assignment/removal

**3. Content Events:**
- Content created
- Content updated (with diff)
- Content deleted (soft delete)
- Content published
- Content unpublished
- Content archived
- Asset uploaded
- Asset deleted

**4. Configuration Events:**
- User created/updated/deleted
- Role created/updated/deleted
- Permission change
- Integration enabled/disabled
- System setting changed

**5. System Events:**
- Deployment initiated/completed
- Backup created
- DR failover initiated
- Security alert triggered

**Audit Log Storage:**

- **Primary Storage**: CloudWatch Logs with 7-year retention
- **Long-term Archive**: S3 Glacier with 10-year retention
- **SIEM Integration**: Forward logs to Sydney Metro's SIEM (if available) via Kinesis Firehose
- **Encryption**: AES-256 encryption at rest, TLS 1.3 in transit

**Log Format (JSON):**

```json
{
  "timestamp": "2025-10-27T14:30:00+11:00",
  "event_type": "content.published",
  "user": {
    "id": "user-12345",
    "email": "editor@sydneymetro.nsw.gov.au",
    "ip": "203.0.113.45",
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7)"
  },
  "action": "publish",
  "resource": {
    "type": "page",
    "id": "content-67890",
    "title": "Service Updates"
  },
  "result": "success",
  "context": {
    "previous_state": "draft",
    "new_state": "published",
    "workflow_stage": "approved"
  }
}
```

**Alerting:**

Real-time alerts for security-relevant events:
- Multiple failed login attempts (5 failures in 5 minutes)
- Privilege escalation (role change to admin)
- Bulk content deletion (>10 items in 1 minute)
- Unauthorized access attempts
- Anomalous API usage (rate limit exceeded)
- Configuration changes in production

**Audit Log Access Controls:**

- Read access: Security team, compliance officer, designated auditors
- Write access: System only (no manual writes)
- Logs immutable (append-only, no deletion except automated retention policy)
- Access to logs is itself audited

---

## 4. Accessibility Implementation

### 4.1 WCAG 2.1 AA Compliance Strategy

**Accessibility Principles (POUR):**

1. **Perceivable** - Information and UI components must be presentable to users
2. **Operable** - UI components and navigation must be operable
3. **Understandable** - Information and UI operation must be understandable
4. **Robust** - Content must be robust enough to be interpreted by assistive technologies

**Key WCAG 2.1 AA Requirements:**

| Success Criterion | Level | Implementation Strategy |
|-------------------|-------|-------------------------|
| **1.1.1 Non-text Content** | A | All images have descriptive alt text; decorative images marked with empty alt="" |
| **1.3.1 Info and Relationships** | A | Semantic HTML (headings, lists, landmarks); ARIA labels where needed |
| **1.4.3 Contrast (Minimum)** | AA | Text contrast ratio ≥4.5:1 (normal text), ≥3:1 (large text) |
| **1.4.4 Resize Text** | AA | Text resizable to 200% without loss of functionality |
| **1.4.5 Images of Text** | AA | Avoid images of text; use web fonts or SVG |
| **2.1.1 Keyboard** | A | All functionality accessible via keyboard (no mouse-only interactions) |
| **2.4.1 Bypass Blocks** | A | Skip navigation link to main content |
| **2.4.2 Page Titled** | A | Descriptive page titles (<title> tag) |
| **2.4.3 Focus Order** | A | Logical tab order following visual flow |
| **2.4.7 Focus Visible** | AA | Visible focus indicator (outline or highlight) |
| **3.1.1 Language of Page** | A | HTML lang attribute set (en-AU) |
| **3.2.3 Consistent Navigation** | AA | Navigation consistent across pages |
| **3.3.1 Error Identification** | A | Form errors identified in text (not just color) |
| **3.3.2 Labels or Instructions** | A | All form fields have labels; required fields indicated |
| **4.1.2 Name, Role, Value** | A | All UI components have accessible names and roles (ARIA) |

### 4.2 Design System and Component Library

**Accessible Component Standards:**

All components in our design system will meet WCAG 2.1 AA out of the box:

**Button Component:**
```tsx
// Accessible button with proper semantics
<button
  type="button"
  aria-label="Close dialog"
  onClick={handleClose}
  className="btn btn-primary"
>
  <IconClose aria-hidden="true" />
  Close
</button>
```

**Form Input Component:**
```tsx
// Accessible input with label, error, and hint
<div className="form-field">
  <label htmlFor="email" className="form-label">
    Email Address <span aria-label="required">*</span>
  </label>
  <span id="email-hint" className="form-hint">
    We'll never share your email with anyone else.
  </span>
  <input
    id="email"
    type="email"
    aria-describedby="email-hint email-error"
    aria-invalid={hasError}
    className="form-input"
  />
  {hasError && (
    <span id="email-error" className="form-error" role="alert">
      Please enter a valid email address.
    </span>
  )}
</div>
```

**Modal Dialog Component:**
```tsx
// Accessible modal with focus trap and keyboard support
<div
  role="dialog"
  aria-labelledby="dialog-title"
  aria-describedby="dialog-description"
  aria-modal="true"
  className="modal"
>
  <h2 id="dialog-title">Confirm Action</h2>
  <p id="dialog-description">
    Are you sure you want to proceed with this action?
  </p>
  <button onClick={handleConfirm}>Confirm</button>
  <button onClick={handleCancel}>Cancel</button>
</div>
```

**Accessible Design Tokens:**

```css
/* Color palette with WCAG AA contrast ratios */
:root {
  /* Primary colors */
  --color-primary: #0056B3; /* Sydney Metro blue */
  --color-primary-text: #FFFFFF; /* Contrast ratio: 7.4:1 */

  /* Text colors */
  --color-text-primary: #1A1A1A; /* On white: 14.3:1 */
  --color-text-secondary: #4A4A4A; /* On white: 9.7:1 */

  /* Focus indicator */
  --color-focus: #FFBF47; /* High-visibility yellow */
  --focus-outline-width: 3px;
  --focus-outline-offset: 2px;

  /* Error/success colors */
  --color-error: #D4351C; /* Contrast ratio: 5.3:1 on white */
  --color-success: #00703C; /* Contrast ratio: 6.2:1 on white */
}

/* Focus styles */
*:focus-visible {
  outline: var(--focus-outline-width) solid var(--color-focus);
  outline-offset: var(--focus-outline-offset);
}
```

### 4.3 Automated Testing Framework

**Testing Tools:**

1. **axe-core** - Industry-leading accessibility testing engine
2. **Pa11y** - Command-line accessibility testing
3. **Lighthouse** - Automated accessibility audits in CI/CD
4. **Storybook + axe addon** - Component-level accessibility testing

**Integration Points:**

**1. Component Tests (Jest + React Testing Library + jest-axe):**

```typescript
import { render } from '@testing-library/react';
import { axe, toHaveNoViolations } from 'jest-axe';
import { Button } from './Button';

expect.extend(toHaveNoViolations);

describe('Button accessibility', () => {
  it('should have no accessibility violations', async () => {
    const { container } = render(<Button>Click me</Button>);
    const results = await axe(container);
    expect(results).toHaveNoViolations();
  });

  it('should be keyboard accessible', () => {
    const { getByRole } = render(<Button onClick={jest.fn()}>Click me</Button>);
    const button = getByRole('button');

    button.focus();
    expect(button).toHaveFocus();

    fireEvent.keyDown(button, { key: 'Enter' });
    expect(onClick).toHaveBeenCalled();
  });
});
```

**2. Integration Tests (Playwright + axe-playwright):**

```typescript
import { test, expect } from '@playwright/test';
import AxeBuilder from '@axe-core/playwright';

test('homepage should be accessible', async ({ page }) => {
  await page.goto('/');

  // Run axe accessibility scan
  const accessibilityScanResults = await new AxeBuilder({ page })
    .withTags(['wcag2a', 'wcag2aa'])
    .analyze();

  expect(accessibilityScanResults.violations).toEqual([]);
});

test('should be keyboard navigable', async ({ page }) => {
  await page.goto('/');

  // Tab through interactive elements
  await page.keyboard.press('Tab');
  await expect(page.locator('a:focus')).toBeVisible();

  await page.keyboard.press('Tab');
  await expect(page.locator('button:focus')).toBeVisible();
});
```

**3. CI/CD Pipeline (Lighthouse CI):**

```yaml
# .github/workflows/accessibility.yml
name: Accessibility Tests

on: [pull_request]

jobs:
  accessibility:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install dependencies
        run: npm ci

      - name: Build application
        run: npm run build

      - name: Start server
        run: npm run start &

      - name: Wait for server
        run: npx wait-on http://localhost:3000

      - name: Run Lighthouse CI
        uses: treosh/lighthouse-ci-action@v9
        with:
          urls: |
            http://localhost:3000
            http://localhost:3000/services
            http://localhost:3000/help
          configPath: './lighthouserc.json'
          uploadArtifacts: true
```

**Lighthouse CI Configuration:**

```json
{
  "ci": {
    "collect": {
      "numberOfRuns": 3
    },
    "assert": {
      "assertions": {
        "categories:accessibility": ["error", {"minScore": 0.95}],
        "categories:performance": ["warn", {"minScore": 0.90}],
        "categories:seo": ["warn", {"minScore": 0.90}]
      }
    },
    "upload": {
      "target": "temporary-public-storage"
    }
  }
}
```

**Automated Testing Policy:**

- Pull requests must pass all accessibility tests to merge
- Accessibility score must be ≥95 (Lighthouse)
- Zero critical or serious axe violations allowed
- Component library components must have 100% accessibility coverage

### 4.4 Manual Testing Process

**Manual Testing Scope:**

Automated testing catches ~60-70% of accessibility issues. Manual testing is required for:
- Keyboard navigation flow and logic
- Screen reader announcements and context
- Cognitive load and comprehension
- Complex interactions (drag-and-drop, multi-step forms)

**Testing Tools:**

| Assistive Technology | Purpose | Platform |
|----------------------|---------|----------|
| **NVDA** (Free) | Screen reader testing | Windows |
| **JAWS** (Licensed) | Screen reader testing (most common enterprise screen reader) | Windows |
| **VoiceOver** (Built-in) | Screen reader testing | macOS, iOS |
| **TalkBack** (Built-in) | Screen reader testing | Android |
| **Dragon NaturallySpeaking** | Voice control testing | Windows |
| **ZoomText** | Screen magnification testing | Windows |

**Manual Testing Checklist:**

**Keyboard Navigation:**
- [ ] All interactive elements reachable via Tab key
- [ ] Tab order follows logical reading order
- [ ] Focus indicator visible on all elements
- [ ] Shift+Tab navigates backward
- [ ] Enter/Space activates buttons and links
- [ ] Escape closes modals and dropdowns
- [ ] Arrow keys navigate within components (menus, tabs)

**Screen Reader:**
- [ ] Page title announced on navigation
- [ ] Headings create logical document outline
- [ ] Landmarks (header, nav, main, footer) identified
- [ ] Images have descriptive alt text
- [ ] Form labels announced with inputs
- [ ] Error messages announced and associated with fields
- [ ] Dynamic content changes announced (ARIA live regions)
- [ ] Loading states communicated

**Visual:**
- [ ] Text readable at 200% zoom (no horizontal scrolling)
- [ ] Color not sole indicator of meaning
- [ ] High contrast mode functional
- [ ] Animations can be disabled (prefers-reduced-motion)
- [ ] Focus indicators visible against all backgrounds

**Cognitive:**
- [ ] Instructions clear and concise
- [ ] Error messages specific and actionable
- [ ] Navigation consistent across pages
- [ ] Complex processes broken into steps with progress indicators

**Manual Testing Schedule:**

- **Component Development**: Developers test with keyboard and screen reader
- **Pull Request**: Peer review includes accessibility spot-check
- **Sprint End**: Accessibility specialist reviews completed features
- **UAT**: Sydney Metro stakeholders test with assistive technologies
- **Pre-release**: Full accessibility audit by certified WCAG auditor

**User Testing with People with Disabilities:**

- Recruit 5-10 users with diverse disabilities (vision, motor, cognitive)
- Conduct moderated usability testing sessions
- Focus on real-world tasks (find timetable, plan journey, submit inquiry)
- Iterate on findings before launch

---

## 5. Performance and Resilience

### 5.1 Performance Targets and Monitoring

**Performance SLOs (Service Level Objectives):**

| Metric | Target | Measurement |
|--------|--------|-------------|
| **Page Load Time (p95)** | < 500ms | Time to Interactive (TTI) |
| **Time to First Byte (TTFB)** | < 100ms | Server response time |
| **First Contentful Paint (FCP)** | < 1.5s | Initial content visible |
| **Largest Contentful Paint (LCP)** | < 2.5s | Main content loaded |
| **Cumulative Layout Shift (CLS)** | < 0.1 | Visual stability |
| **First Input Delay (FID)** | < 100ms | Interaction responsiveness |
| **API Response Time (p95)** | < 200ms | Backend API latency |
| **Throughput** | 500 RPS | Requests per second sustained |
| **Uptime** | 99.9% | Monthly availability |

**Real User Monitoring (RUM):**

Implement **CloudWatch RUM** to capture real user performance data:
- Page load times by route
- API call latencies
- JavaScript errors
- User session replay (opt-in, privacy-compliant)
- Performance by geography, device, browser
- Business metrics (bounce rate, conversion rate)

**Synthetic Monitoring:**

**Pingdom/UptimeRobot**:
- HTTP checks every 1 minute from Sydney, Melbourne, Brisbane
- Alert if 3 consecutive failures
- Check homepage, API health endpoint, asset delivery

**Lighthouse CI**:
- Hourly performance audits from CI/CD
- Track performance trends over time
- Alert if scores drop below threshold

**Performance Budget:**

Enforce performance budgets in CI/CD:

| Resource Type | Budget | Enforcement |
|---------------|--------|-------------|
| **JavaScript** | 200 KB (gzipped) | Build fails if exceeded |
| **CSS** | 50 KB (gzipped) | Build fails if exceeded |
| **Images** | 1 MB per page | Warning if exceeded |
| **Fonts** | 100 KB (woff2) | Build fails if exceeded |
| **Total Page Weight** | 2 MB | Warning if exceeded |

### 5.2 Performance Optimization Techniques

**1. Edge Caching Strategy:**

Leverage CloudFront edge caching for maximum performance:

```
User Request → CloudFront Edge (Sydney)
                    │
                    ├─ Cache HIT → Return cached response (< 10ms)
                    │
                    └─ Cache MISS → Fetch from origin
                                        │
                                        └─ ECS Fargate (Sydney) → Contentful API
```

**Cache Key Design:**

```
Cache Key = URL + Query Params + Accept-Language Header

Examples:
- /services/metro-train?lang=en → Unique cache entry
- /services/metro-train?lang=zh → Separate cache entry
```

**Cache Warming:**

Proactively warm cache after content publish:
- Webhook from Contentful on publish event
- Lambda function fetches updated page
- Requests sent to CloudFront to populate edge cache
- Ensures first user gets cached response

**2. Image Optimization:**

All images optimized automatically:

- **Format Selection**: WebP for modern browsers, fallback to JPEG/PNG
- **Responsive Images**: Generate multiple sizes (320w, 640w, 1024w, 1920w)
- **Lazy Loading**: `loading="lazy"` attribute on below-the-fold images
- **Compression**: Lossy compression at 85% quality (visually lossless)
- **CDN Transformation**: Real-time image resizing via Contentful Images API

```html
<!-- Responsive image with WebP and lazy loading -->
<picture>
  <source
    type="image/webp"
    srcset="
      /image.webp?w=320 320w,
      /image.webp?w=640 640w,
      /image.webp?w=1024 1024w
    "
  />
  <img
    src="/image.jpg?w=640"
    srcset="
      /image.jpg?w=320 320w,
      /image.jpg?w=640 640w,
      /image.jpg?w=1024 1024w
    "
    sizes="(max-width: 640px) 100vw, 640px"
    alt="Sydney Metro train"
    loading="lazy"
  />
</picture>
```

**3. Code Splitting and Lazy Loading:**

Next.js automatic code splitting:
- Each page route is a separate bundle
- Dynamic imports for heavy components

```tsx
// Lazy load map component (only loads on demand)
const MapComponent = dynamic(() => import('./MapComponent'), {
  loading: () => <p>Loading map...</p>,
  ssr: false, // Don't render on server (client-only)
});

function StationPage() {
  return (
    <div>
      <h1>Station Details</h1>
      <MapComponent stationId={123} />
    </div>
  );
}
```

**4. Database Query Optimization:**

- **Connection Pooling**: PgBouncer for PostgreSQL connection pooling
- **Read Replicas**: RDS read replicas for read-heavy queries (analytics)
- **Query Caching**: Redis cache for frequently accessed data
- **Indexing**: Proper indexes on foreign keys and frequently queried columns
- **N+1 Query Prevention**: Use GraphQL DataLoader pattern to batch requests

**5. API Response Caching:**

**HTTP Caching Headers:**

```javascript
// Next.js API route with caching
export async function GET(request) {
  const data = await fetchContentFromContentful();

  return new Response(JSON.stringify(data), {
    headers: {
      'Content-Type': 'application/json',
      'Cache-Control': 'public, s-maxage=60, stale-while-revalidate=120',
    },
  });
}
```

**Redis Caching:**

```typescript
// Cache Contentful responses in Redis
async function getPageContent(slug: string) {
  const cacheKey = `page:${slug}`;

  // Check cache
  const cached = await redis.get(cacheKey);
  if (cached) {
    return JSON.parse(cached);
  }

  // Fetch from Contentful
  const content = await contentfulClient.getEntries({
    content_type: 'page',
    'fields.slug': slug,
  });

  // Store in cache (5 minutes TTL)
  await redis.setex(cacheKey, 300, JSON.stringify(content));

  return content;
}
```

### 5.3 Disaster Recovery and Business Continuity

**DR/BC Architecture:**

**Primary Region**: ap-southeast-2 (Sydney)
**DR Region**: ap-southeast-4 (Melbourne)

**Recovery Objectives:**

| Metric | Target | Justification |
|--------|--------|---------------|
| **RTO** (Recovery Time Objective) | ≤ 4 hours | Sydney Metro can tolerate brief downtime; staff can communicate outage |
| **RPO** (Recovery Point Objective) | ≤ 1 hour | Maximum acceptable data loss; content published in last hour may need republishing |

**DR Strategy by Component:**

| Component | DR Approach | Failover Mechanism |
|-----------|-------------|---------------------|
| **Contentful** | SaaS (multi-region by default) | Automatic (Contentful infrastructure) |
| **CloudFront** | Global edge network | Automatic (CloudFront routes around failures) |
| **ECS Fargate** | Active-passive (Melbourne standby) | Route 53 health checks + failover routing |
| **S3 Assets** | Cross-region replication (Sydney → Melbourne) | Automatic, continuous replication |
| **RDS Aurora** | Cross-region read replica | Manual promotion (15 minutes) |
| **OpenSearch** | Automated snapshots to S3 | Restore to new cluster (2-3 hours) |

**Failover Architecture:**

```
Normal State:
Users → CloudFront → Route 53 (Primary: Sydney) → ECS Sydney → Contentful

Failover State:
Users → CloudFront → Route 53 (Failover: Melbourne) → ECS Melbourne → Contentful
                                                                ↓
                                                          RDS Melbourne (promoted)
                                                          S3 Melbourne (replicated)
```

**Automated Failover Process:**

1. **Detection** (5 minutes):
   - Route 53 health checks fail (3 consecutive failures, 30s interval)
   - CloudWatch alarms trigger

2. **Notification** (Immediate):
   - SNS alerts to on-call engineer
   - PagerDuty incident created
   - Status page updated (status.sydneymetro.info)

3. **Automated Failover** (10 minutes):
   - Route 53 updates DNS to Melbourne origin
   - CloudFront edge caches continue serving stale content
   - ECS tasks in Melbourne scale up (if not already running)

4. **Manual Steps** (2-3 hours):
   - Promote RDS read replica to primary (if database affected)
   - Restore OpenSearch from snapshot (if affected)
   - Validate all systems operational in Melbourne

5. **Recovery** (Next business day):
   - Investigate and resolve root cause in Sydney
   - Failback to Sydney when stable
   - Post-incident review and runbook update

**Backup Strategy:**

| Data Type | Backup Frequency | Retention | Storage Location |
|-----------|------------------|-----------|------------------|
| **RDS Database** | Automated daily | 35 days | S3 (Sydney + Melbourne) |
| **S3 Assets** | Continuous replication | Indefinite | S3 Melbourne |
| **Contentful Content** | Daily export via Management API | 90 days | S3 Sydney |
| **Configuration** | Git repository | Indefinite | GitHub |
| **Secrets** | AWS Secrets Manager (auto-replicated) | N/A | Secrets Manager (cross-region) |

**Backup Testing:**

- **Monthly**: Restore RDS backup to test instance, validate integrity
- **Quarterly**: Full DR drill (failover to Melbourne, validate functionality)
- **Annually**: Simulated disaster scenario with full team participation

**Runbook Documentation:**

Detailed runbooks for common scenarios:
- DR Failover Procedure
- DR Failback Procedure
- Database Restoration
- Content Export/Import
- Incident Response

### 5.4 High Availability Architecture

**Multi-AZ Deployment:**

All critical components deployed across 3 Availability Zones:

```
ap-southeast-2a          ap-southeast-2b          ap-southeast-2c
│                        │                        │
├─ ECS Task 1            ├─ ECS Task 2            ├─ ECS Task 3
├─ NAT Gateway           ├─ NAT Gateway           ├─ NAT Gateway
├─ RDS Primary           ├─ RDS Standby           │
└─ OpenSearch Node 1     └─ OpenSearch Node 2     └─ OpenSearch Node 3
```

**Load Balancing:**

**Application Load Balancer (ALB):**
- Cross-AZ load balancing
- Health checks every 30 seconds (HTTP GET /health)
- Unhealthy threshold: 2 consecutive failures
- Healthy threshold: 2 consecutive successes
- Deregistration delay: 30 seconds (drain connections gracefully)
- Stickiness: Cookie-based (if needed for session affinity)

**Auto Scaling:**

**Target Tracking Scaling Policy:**
- Target CPU utilization: 70%
- Scale-out: Add 1 task if CPU > 70% for 2 minutes
- Scale-in: Remove 1 task if CPU < 50% for 5 minutes
- Min capacity: 2 tasks (HA requirement)
- Max capacity: 10 tasks

**Scheduled Scaling (optional):**
- Scale up during peak hours (6am-10am, 4pm-8pm weekdays)
- Scale down during off-peak hours (10pm-6am)

**Circuit Breaker Pattern:**

Implement circuit breakers for external dependencies (Contentful API, NSW Identity):

```typescript
import CircuitBreaker from 'opossum';

const contentfulBreaker = new CircuitBreaker(fetchContentful, {
  timeout: 5000, // 5s timeout
  errorThresholdPercentage: 50, // Open circuit if 50% requests fail
  resetTimeout: 30000, // Try again after 30s
});

contentfulBreaker.on('open', () => {
  // Fallback to cached content or show error page
  console.error('Circuit breaker opened for Contentful API');
});

async function getContent(slug) {
  try {
    return await contentfulBreaker.fire(slug);
  } catch (err) {
    // Serve stale content from cache
    return getCachedContent(slug);
  }
}
```

**Graceful Degradation:**

When dependencies fail, system degrades gracefully:
- Contentful unavailable → Serve cached content with staleness warning
- Search unavailable → Basic text search (database query)
- NSW Identity unavailable → Login disabled, public content still accessible
- Analytics unavailable → Skip tracking, no user impact

---

## 6. DevSecOps and CI/CD

### 6.1 CI/CD Pipeline Architecture

**Pipeline Overview:**

```
Developer → Git Push → GitHub
                         │
                         ▼
                    GitHub Actions
                         │
      ┌──────────────────┼──────────────────┐
      ▼                  ▼                  ▼
   Build            Security Tests      Quality Gates
   • npm install    • SAST (Semgrep)    • Unit tests (Jest)
   • npm build      • Dependency scan   • Integration tests
   • Docker build   • DAST (OWASP ZAP)  • E2E tests (Playwright)
                    • Container scan    • Accessibility tests
                                         • Code coverage (>80%)
                                         • Linting (ESLint)
                         │
                         ▼
                   Approval Gate
                    (Production)
                         │
                         ▼
                    AWS Deployment
                         │
      ┌──────────────────┼──────────────────┐
      ▼                  ▼                  ▼
   ECR Push         ECS Deploy         Post-Deploy
   • Tag image      • Update service   • Smoke tests
   • Scan image     • Health checks    • Performance tests
                    • Gradual rollout  • Notify team
```

**Environment Strategy:**

| Environment | Purpose | Branch | Deployment | Access |
|-------------|---------|--------|------------|--------|
| **Development** | Developer testing | `feature/*` | Automatic on push | Developers only |
| **Staging** | Integration testing, UAT | `develop` | Automatic on merge | Internal team |
| **Production** | Live public site | `main` | Manual approval required | Public |

### 6.2 Pipeline Configuration

**GitHub Actions Workflow:**

```yaml
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Lint
        run: npm run lint

      - name: Type check
        run: npm run type-check

      - name: Build
        run: npm run build
        env:
          NEXT_PUBLIC_CONTENTFUL_SPACE_ID: ${{ secrets.CONTENTFUL_SPACE_ID }}
          CONTENTFUL_ACCESS_TOKEN: ${{ secrets.CONTENTFUL_ACCESS_TOKEN }}

      - name: Upload build artifacts
        uses: actions/upload-artifact@v3
        with:
          name: build
          path: .next/

  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Unit tests
        run: npm run test:unit -- --coverage

      - name: Integration tests
        run: npm run test:integration

      - name: E2E tests
        run: npx playwright test

      - name: Upload coverage
        uses: codecov/codecov-action@v3

  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: SAST - Semgrep
        uses: returntocorp/semgrep-action@v1
        with:
          config: >-
            p/security-audit
            p/secrets
            p/javascript

      - name: Dependency scan
        run: |
          npm audit --audit-level=moderate
          npm run snyk-test

      - name: Container image scan
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: 'sydneymetro/cms:${{ github.sha }}'
          format: 'sarif'
          output: 'trivy-results.sarif'

      - name: Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: 'trivy-results.sarif'

  deploy-staging:
    runs-on: ubuntu-latest
    needs: [build, test, security]
    if: github.ref == 'refs/heads/develop'
    environment:
      name: staging
      url: https://staging.sydneymetro.nsw.gov.au
    steps:
      - uses: actions/checkout@v3

      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v2
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: ap-southeast-2

      - name: Login to ECR
        id: login-ecr
        uses: aws-actions/amazon-ecr-login@v1

      - name: Build and push Docker image
        env:
          ECR_REGISTRY: ${{ steps.login-ecr.outputs.registry }}
          ECR_REPOSITORY: sydneymetro-cms
          IMAGE_TAG: ${{ github.sha }}
        run: |
          docker build -t $ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG .
          docker push $ECR_REGISTRY/$ECR_REPOSITORY:$IMAGE_TAG

      - name: Deploy to ECS
        run: |
          aws ecs update-service \
            --cluster sydneymetro-staging \
            --service cms-service \
            --force-new-deployment

      - name: Wait for deployment
        run: |
          aws ecs wait services-stable \
            --cluster sydneymetro-staging \
            --services cms-service

      - name: Smoke tests
        run: |
          curl -f https://staging.sydneymetro.nsw.gov.au/health || exit 1

  deploy-production:
    runs-on: ubuntu-latest
    needs: [build, test, security]
    if: github.ref == 'refs/heads/main'
    environment:
      name: production
      url: https://www.sydneymetro.nsw.gov.au
    steps:
      # Similar to staging deployment, but with additional safeguards

      - name: Manual approval
        uses: trstringer/manual-approval@v1
        with:
          approvers: sre-team,tech-lead
          minimum-approvals: 2

      - name: Blue-green deployment
        run: |
          # Deploy to green environment
          # Run smoke tests
          # Switch traffic to green
          # Keep blue as rollback
          ./scripts/blue-green-deploy.sh

      - name: Notify team
        uses: 8398a7/action-slack@v3
        with:
          status: ${{ job.status }}
          text: 'Production deployment completed'
          webhook_url: ${{ secrets.SLACK_WEBHOOK }}
```

### 6.3 Deployment Strategy

**Blue-Green Deployment:**

For production, we use blue-green deployment to enable instant rollback:

```
Production Environment:
┌──────────────────────────────────────┐
│  Application Load Balancer           │
│  (Routes 100% traffic to active)     │
└──────────────┬───────────────────────┘
               │
       ┌───────┴───────┐
       ▼               ▼
┌─────────────┐ ┌─────────────┐
│  Blue       │ │  Green      │
│  (Active)   │ │  (Standby)  │
│             │ │             │
│  v1.2.3     │ │  v1.2.4     │
└─────────────┘ └─────────────┘

Deployment Process:
1. Deploy v1.2.4 to Green environment
2. Run smoke tests on Green
3. Switch ALB to route 100% traffic to Green
4. Monitor for errors (5 minutes)
5. If successful: Blue becomes standby
   If errors: Switch back to Blue (instant rollback)
```

**Canary Deployment (Alternative):**

For lower-risk deployments, canary strategy gradually shifts traffic:

```
1. Deploy new version to 10% of tasks
2. Monitor metrics (error rate, latency) for 15 minutes
3. If successful: Increase to 50%
4. Monitor for 15 minutes
5. If successful: Increase to 100%
6. If any stage fails: Rollback immediately
```

**Rollback Procedures:**

**Automatic Rollback Triggers:**
- Error rate > 5% for 2 minutes
- P95 latency > 1000ms for 5 minutes
- Health check failures > 50%

**Manual Rollback:**
```bash
# Rollback to previous version
./scripts/rollback.sh --version v1.2.3

# This script:
# 1. Updates ECS task definition to previous image tag
# 2. Triggers ECS service update
# 3. Monitors deployment progress
# 4. Validates health checks
```

### 6.4 Infrastructure as Code

**AWS CDK (TypeScript):**

All infrastructure defined in code for version control and reproducibility:

```typescript
// lib/sydneymetro-stack.ts
import * as cdk from 'aws-cdk-lib';
import * as ec2 from 'aws-cdk-lib/aws-ec2';
import * as ecs from 'aws-cdk-lib/aws-ecs';
import * as elbv2 from 'aws-cdk-lib/aws-elasticloadbalancingv2';

export class SydneyMetroStack extends cdk.Stack {
  constructor(scope: cdk.App, id: string, props?: cdk.StackProps) {
    super(scope, id, props);

    // VPC with 3 AZs
    const vpc = new ec2.Vpc(this, 'SydneyMetroVPC', {
      maxAzs: 3,
      natGateways: 3,
      subnetConfiguration: [
        {
          name: 'Public',
          subnetType: ec2.SubnetType.PUBLIC,
          cidrMask: 24,
        },
        {
          name: 'Private',
          subnetType: ec2.SubnetType.PRIVATE_WITH_EGRESS,
          cidrMask: 24,
        },
        {
          name: 'Data',
          subnetType: ec2.SubnetType.PRIVATE_ISOLATED,
          cidrMask: 24,
        },
      ],
    });

    // ECS Cluster
    const cluster = new ecs.Cluster(this, 'SydneyMetroCluster', {
      vpc,
      containerInsights: true,
    });

    // Fargate Task Definition
    const taskDefinition = new ecs.FargateTaskDefinition(this, 'TaskDef', {
      memoryLimitMiB: 4096,
      cpu: 2048,
    });

    const container = taskDefinition.addContainer('NextjsContainer', {
      image: ecs.ContainerImage.fromRegistry('sydneymetro/cms:latest'),
      logging: ecs.LogDrivers.awsLogs({ streamPrefix: 'sydneymetro' }),
      environment: {
        NODE_ENV: 'production',
        CONTENTFUL_SPACE_ID: process.env.CONTENTFUL_SPACE_ID,
      },
      secrets: {
        CONTENTFUL_ACCESS_TOKEN: ecs.Secret.fromSecretsManager(
          secretsmanager.Secret.fromSecretNameV2(this, 'ContentfulToken', 'contentful/access-token')
        ),
      },
    });

    container.addPortMappings({ containerPort: 3000 });

    // ALB
    const alb = new elbv2.ApplicationLoadBalancer(this, 'ALB', {
      vpc,
      internetFacing: true,
    });

    const listener = alb.addListener('Listener', {
      port: 443,
      certificates: [certificate],
    });

    // ECS Service
    const service = new ecs.FargateService(this, 'Service', {
      cluster,
      taskDefinition,
      desiredCount: 2,
      minHealthyPercent: 100,
      maxHealthyPercent: 200,
    });

    listener.addTargets('ECS', {
      port: 3000,
      targets: [service],
      healthCheck: {
        path: '/api/health',
        interval: cdk.Duration.seconds(30),
        timeout: cdk.Duration.seconds(5),
        healthyThresholdCount: 2,
        unhealthyThresholdCount: 2,
      },
    });

    // Auto Scaling
    const scaling = service.autoScaleTaskCount({ maxCapacity: 10 });
    scaling.scaleOnCpuUtilization('CpuScaling', {
      targetUtilizationPercent: 70,
    });
  }
}
```

**Environment Configuration:**

Separate CDK stacks for each environment:

```typescript
// bin/sydneymetro.ts
const app = new cdk.App();

new SydneyMetroStack(app, 'SydneyMetro-Dev', {
  env: { account: '123456789', region: 'ap-southeast-2' },
  stage: 'dev',
});

new SydneyMetroStack(app, 'SydneyMetro-Staging', {
  env: { account: '123456789', region: 'ap-southeast-2' },
  stage: 'staging',
});

new SydneyMetroStack(app, 'SydneyMetro-Prod', {
  env: { account: '987654321', region: 'ap-southeast-2' },
  stage: 'prod',
});
```

---

## 7. Technology Stack

### 7.1 Core Technologies

**Frontend:**

| Technology | Version | Purpose | Rationale |
|------------|---------|---------|-----------|
| **Next.js** | 14.x | React framework | SSR, ISR, SSG support; excellent performance; built-in optimization |
| **React** | 18.x | UI library | Industry standard; large ecosystem; concurrent rendering |
| **TypeScript** | 5.x | Type system | Type safety; improved developer experience; catch errors at compile-time |
| **Tailwind CSS** | 3.x | CSS framework | Utility-first styling; design system tokens; small bundle size |
| **React Hook Form** | 7.x | Form management | Performant; built-in validation; accessibility support |
| **Axios** | 1.x | HTTP client | Request/response interceptors; timeout handling; cancellation support |
| **React Query** | 5.x | Server state | Data fetching; caching; invalidation; optimistic updates |

**Backend:**

| Technology | Version | Purpose | Rationale |
|------------|---------|---------|-----------|
| **Node.js** | 20 LTS | Runtime | JavaScript/TypeScript ecosystem; non-blocking I/O; AWS Lambda support |
| **Contentful** | Enterprise | Headless CMS | Proven scale; excellent API; workflow engine; AU CDN presence |
| **PostgreSQL** | 15 (Aurora) | Relational database | ACID compliance; JSON support; full-text search; managed service |
| **Redis** | 7.x (ElastiCache) | Cache & session store | Sub-millisecond latency; pub/sub support; automatic failover |
| **OpenSearch** | 2.x | Full-text search | Elasticsearch-compatible; faceted search; aggregations; managed service |

**Infrastructure:**

| Technology | Purpose | Rationale |
|------------|---------|-----------|
| **AWS ECS Fargate** | Container orchestration | Serverless containers; no EC2 management; automatic scaling |
| **AWS CloudFront** | CDN | Global edge network; AWS integration; origin shield |
| **AWS WAF** | Web application firewall | OWASP Top 10 protection; managed rules; rate limiting |
| **AWS Secrets Manager** | Secret management | Automatic rotation; encryption; audit logging |
| **AWS CloudWatch** | Observability | Logs, metrics, traces; integrated with AWS services |
| **AWS X-Ray** | Distributed tracing | End-to-end request tracing; performance bottleneck identification |

**DevOps:**

| Technology | Purpose | Rationale |
|------------|---------|-----------|
| **GitHub Actions** | CI/CD | Native GitHub integration; matrix builds; self-hosted runners |
| **Docker** | Containerization | Consistent environments; portable; efficient resource usage |
| **AWS CDK** | Infrastructure as Code | Type-safe infrastructure; AWS best practices; synthesizes CloudFormation |
| **Terraform** (Alternative) | Infrastructure as Code | Multi-cloud support; large ecosystem; state management |

**Security:**

| Technology | Purpose | Rationale |
|------------|---------|-----------|
| **NextAuth.js** | Authentication | Next.js integration; OIDC support; session management |
| **Helmet.js** | Security headers | HSTS, CSP, X-Frame-Options; reduce attack surface |
| **OWASP ZAP** | DAST | Open-source; automated scanning; CI/CD integration |
| **Semgrep** | SAST | Fast; custom rules; low false positives |
| **Trivy** | Container scanning | CVE detection; OS and library vulnerabilities |
| **Snyk** | Dependency scanning | Real-time vulnerability database; fix recommendations |

**Testing:**

| Technology | Purpose | Rationale |
|------------|---------|-----------|
| **Jest** | Unit testing | Fast; snapshot testing; mocking support; React integration |
| **React Testing Library** | Component testing | User-centric tests; accessibility focus; maintainable |
| **Playwright** | E2E testing | Cross-browser; reliable; trace viewer; codegen |
| **axe-core** | Accessibility testing | Comprehensive WCAG checks; low false positives |
| **Lighthouse CI** | Performance testing | Core Web Vitals; budget enforcement; trend tracking |

### 7.2 Integration Architecture

**Contentful Integration:**

```typescript
// lib/contentful.ts
import { createClient } from 'contentful';

export const contentfulClient = createClient({
  space: process.env.CONTENTFUL_SPACE_ID,
  accessToken: process.env.CONTENTFUL_ACCESS_TOKEN,
  host: process.env.CONTENTFUL_HOST || 'cdn.contentful.com',
  // Use AU-specific endpoint for data residency
  environment: process.env.CONTENTFUL_ENVIRONMENT || 'master',
});

// Fetch page by slug with caching
export async function getPageBySlug(slug: string, locale = 'en-US') {
  const response = await contentfulClient.getEntries({
    content_type: 'page',
    'fields.slug': slug,
    locale,
    include: 2, // Include 2 levels of references
  });

  if (response.items.length === 0) {
    return null;
  }

  return response.items[0];
}
```

**NSW Identity Integration:**

```typescript
// lib/auth.ts
import { NextAuthOptions } from 'next-auth';
import { OAuthConfig } from 'next-auth/providers';

const NSWIdentityProvider: OAuthConfig = {
  id: 'nsw-identity',
  name: 'NSW Identity',
  type: 'oauth',
  wellKnown: process.env.NSW_IDENTITY_WELL_KNOWN_URL,
  authorization: {
    params: {
      scope: 'openid profile email',
      code_challenge_method: 'S256',
    },
  },
  clientId: process.env.NSW_IDENTITY_CLIENT_ID,
  clientSecret: process.env.NSW_IDENTITY_CLIENT_SECRET,
  profile(profile) {
    return {
      id: profile.sub,
      name: `${profile.given_name} ${profile.family_name}`,
      email: profile.email,
      roles: profile.groups || [],
    };
  },
};

export const authOptions: NextAuthOptions = {
  providers: [NSWIdentityProvider],
  session: { strategy: 'jwt', maxAge: 3600 },
  callbacks: {
    async jwt({ token, account, profile }) {
      if (account && profile) {
        token.accessToken = account.access_token;
        token.roles = profile.groups || [];
      }
      return token;
    },
    async session({ session, token }) {
      session.accessToken = token.accessToken;
      session.user.roles = token.roles;
      return session;
    },
  },
};
```

**Webhook Integration:**

Contentful webhooks trigger cache invalidation and notifications:

```typescript
// pages/api/webhooks/contentful.ts
import type { NextApiRequest, NextApiResponse } from 'next';
import { invalidateCache } from '@/lib/cache';
import { notifySlack } from '@/lib/notifications';

export default async function handler(
  req: NextApiRequest,
  res: NextApiResponse
) {
  if (req.method !== 'POST') {
    return res.status(405).json({ error: 'Method not allowed' });
  }

  // Verify webhook signature
  const signature = req.headers['x-contentful-signature'];
  if (!verifySignature(signature, req.body)) {
    return res.status(401).json({ error: 'Invalid signature' });
  }

  const event = req.body;

  // Handle different event types
  switch (event.sys.type) {
    case 'Entry':
      if (event.sys.publishedAt) {
        // Entry published
        await invalidateCache(event.sys.id);
        await notifySlack(`Content published: ${event.fields.title['en-US']}`);
      }
      break;

    case 'Asset':
      // Asset uploaded
      await invalidateCache(`asset-${event.sys.id}`);
      break;
  }

  res.status(200).json({ success: true });
}
```

### 7.3 Technology Decision Records

**ADR-001: Headless CMS Selection (Contentful vs. Strapi)**

**Context**: Sydney Metro requires a modern CMS with multi-language support, workflow management, and Australian data residency.

**Decision**: Select Contentful Enterprise over self-hosted Strapi.

**Rationale**:
- **Operational Efficiency**: Contentful is fully managed (99.99% SLA), eliminating infrastructure management
- **Security Posture**: SOC 2 Type II and ISO 27001 certified out-of-the-box
- **Data Residency**: AU-specific CDN endpoints meet requirements
- **Enterprise Support**: 24/7 support with SLA guarantees
- **Total Cost of Ownership**: Higher licensing offset by lower operations cost

**Consequences**:
- Vendor lock-in to Contentful (mitigated by content export capabilities)
- Higher per-month cost (~$3k/month vs. ~$1k/month for self-hosted)
- Faster time-to-market (no infrastructure setup)

---

**ADR-002: Frontend Framework Selection (Next.js vs. Gatsby vs. Remix)**

**Context**: Need React-based framework with SSR, SSG, and excellent performance.

**Decision**: Select Next.js 14.

**Rationale**:
- **Hybrid Rendering**: SSR, SSG, ISR support for different content types
- **Performance**: Built-in image optimization, code splitting, prefetching
- **Developer Experience**: Fast refresh, TypeScript support, excellent documentation
- **Ecosystem**: Largest community, extensive third-party integrations
- **Contentful Integration**: Official SDK and excellent documentation

**Alternatives Considered**:
- **Gatsby**: Great for SSG but poor SSR support; rebuild times slow for large sites
- **Remix**: Excellent SSR but less mature ecosystem; learning curve for team

**Consequences**:
- Need to manage server infrastructure (mitigated by ECS Fargate)
- Vendor preference for Vercel hosting (mitigated by self-hosting on AWS)

---

**ADR-003: Container Orchestration (ECS Fargate vs. EKS vs. App Runner)**

**Context**: Need to deploy containerized Next.js application with auto-scaling and multi-AZ support.

**Decision**: Select AWS ECS Fargate.

**Rationale**:
- **Simplicity**: No control plane to manage (vs. EKS)
- **Cost**: Pay only for running tasks, no EC2 instances
- **AWS Integration**: Native CloudWatch, X-Ray, Secrets Manager integration
- **Team Expertise**: Team familiar with ECS, not Kubernetes

**Alternatives Considered**:
- **EKS**: More complex, higher cost, overkill for single application
- **App Runner**: Less control over networking and security configuration

**Consequences**:
- ECS-specific knowledge required (not transferable to Kubernetes)
- Vendor lock-in to AWS

---

## Conclusion

This technical proposal outlines a comprehensive, modern, and secure solution for Sydney Metro's CMS modernization project. Our architecture leverages proven enterprise technologies, cloud-native design principles, and best practices in security, accessibility, and performance optimization.

**Key Differentiators:**

1. **Proven Technology Stack**: Contentful Enterprise, Next.js, AWS—all battle-tested at scale
2. **Security-First Approach**: Zero-trust architecture, NSW Identity integration, comprehensive testing
3. **Performance Excellence**: p95 < 500ms target through edge caching, SSR/ISR, and optimization
4. **Accessibility Leadership**: WCAG 2.1 AA compliance with automated and manual testing
5. **Operational Resilience**: Multi-AZ deployment, DR/BC with RTO ≤ 4h, RPO ≤ 1h
6. **DevSecOps Maturity**: Automated security scanning, infrastructure as code, blue-green deployment

HCL Technologies is committed to delivering a world-class content management platform that serves Sydney Metro's needs today and scales for tomorrow. Our team brings deep expertise in government digital services, cloud architecture, and accessibility, ensuring successful delivery and long-term sustainability of this critical platform.

We look forward to partnering with Sydney Metro on this transformational journey.

---

**Document Version**: 1.0
**Last Updated**: October 2025
**Classification**: Commercial in Confidence

**Prepared by:**
HCL Technologies
Digital Solutions Practice
Australia and New Zealand
