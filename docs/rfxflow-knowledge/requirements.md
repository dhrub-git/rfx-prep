# Onboarding Inputs Report

This document lists all input fields used across the onboarding step forms (Step 1 — Step 7). Each step is a separate section and includes the field name (form key), label shown in the UI, input type, placeholders/options when present, and quick notes.

---

## Step 1 — Company Profile

- legalName — "Full Legal Name" — text input
- dba — "Doing Business As (DBA)" — text input
- ein — "Federal Tax ID (EIN)" — text input — placeholder: `XX-XXXXXXX`
- incDate — "Date of Incorporation" — date input
- corpType — "Corporate Structure" — select — options: `LLC`, `S-Corp`, `C-Corp`, `Partnership`
- disadvantagedCerts — "Minority/Disadvantaged Certs" — text input — placeholder: `e.g., MBE, WOSB`

Registrations & Licenses

- sam — "SAM Registration Status" — select — options: `Active`, `Inactive`, `N/A`
- cage — "CAGE Code" — text input
- duns — "DUNS Number" — text input
- gsa — "GSA Schedule Numbers" — text input

Operational

- coreServices — "Core Service Offerings" — textarea — placeholder: `Describe main services...`
- pmMethodology — "Project Management Methodology" — select — options: `Agile`, `Scrum`, `Waterfall`, `PMP/PMBOK`
- geoCoverage — "Geographic Coverage" — text input
- iso9001 — "ISO 9001 (Quality)" — select — options: `Certified`, `Not Certified`
- iso27001 — "ISO 27001 (InfoSec)" — select — options: `Certified`, `Not Certified`
- kpi — "Key Performance Indicators (KPIs)" — textarea — placeholder: `e.g., CSAT > 95%...`

Financial

- bondingSingle — "Single Project Bonding Limit ($)" — number input
- bondingAgg — "Aggregate Bonding Limit ($)" — number input
- banking — "Primary Banking Partners" — text input

Insurance

- genLiability — "General Liability Limit ($)" — number input
- profLiability — "Professional Liability ($)" — number input
- cyberLiability — "Cyber Liability ($)" — number input
- doLiability — "Directors & Officers Insurance ($)" — number input

Documents

- FileDropzone — files uploaded via component `FileDropzone` — used in a "Documents" tab

---

## Step 2 — Technical Capabilities

Infrastructure

- cloudAws — "AWS Partnership Level" — select — options: `None`, `Select`, `Advanced`, `Premier`
- cloudAzure — "Azure Partnership Level" — select — options: `None`, `Silver`, `Gold`, `Expert MSP`
- cloudGcp — "Google Cloud Services" — text input — placeholder: `e.g., Partner`

Security

- socCaps — "Security Operations Center (SOC)" — select — options: `In-house 24/7`, `Outsourced`, `Hybrid`
- secTools — "Security Architecture Summary" — textarea — placeholder: `e.g., Palo Alto, CrowdStrike, Splunk...`

Software / Platforms

- progLangs — "Programming Languages" — textarea — placeholder: `e.g., Java, Python, JavaScript/React...`
- cicdTools — "CI/CD & DevOps Tools" — text input — placeholder: `Jenkins, Azure DevOps, Docker...`
- dbExpertise — "Database Expertise" — text input — placeholder: `PostgreSQL, Oracle, MongoDB...`
- erpCrm — "Enterprise Software Platforms" — text input — placeholder: `Salesforce, SAP, Dynamics...`

Certifications & Partners

- certAws — "AWS Certified" — number input — placeholder: `25` (staff count) — valueAsNumber
- certAzure — "Azure Certified" — number input — placeholder: `30`
- certCissp — "CISSP Certified" — number input — placeholder: `10`
- certPmp — "PMP Certified" — number input — placeholder: `15`
- partners — "Strategic Technology Partnerships" — textarea — placeholder: `Microsoft Gold Partner, AWS Advanced Partner...`

Documents

- FileDropzone — files via `FileDropzone` component

---

## Step 3 — Past Performance

Project Example tab

- projName — "Project Name" — text input
- projCustomer — "Customer" — text input
- projValue — "Project Value ($)" — number input
- projDuration — "Duration (Months)" — number input
- projTech — "Technology Platforms Used" — textarea
- schedulePerf — "Schedule Performance" — text input — placeholder: `e.g., 99% on-time`
- budgetPerf — "Budget Performance" — text input — placeholder: `e.g., 2% under budget`
- projSummary — "Executive Summary" — textarea

Reference Example tab

- refName — "Full Name" — text input
- refTitle — "Title & Company" — text input
- refEmail — "Email" — email input
- refPhone — "Phone" — tel input
- refWillingness — "Willingness to Serve" — select — options: `Yes, anytime`, `Yes, with notice`, `Written only`
- refTalkingPoints — "Key Talking Points" — textarea — placeholder: `e.g., 'Met all deadlines'...`

Documents

- FileDropzone — files via `FileDropzone`

---

## Step 4 — Human Resources

Personnel & Structure

- headcount — "Current Headcount" — number input
- retention — "Annual Retention Rate (%)" — number input
- serviceLines — "Business Units / Service Lines" — text input — placeholder: `Cloud Services...`

Key Personnel Example

- keyName — "Name" — text input
- keyExp — "Years of Experience" — number input
- keyClearance — "Security Clearance" — select — options: `None`, `Public Trust`, `Secret`, `Top Secret`
- keySummary — "Professional Summary" — textarea

Training & Development

- onboarding — "New Hire Onboarding Program?" — select — options: `Yes`, `No`
- certSupport — "Certification Support Program?" — select — options: `Yes`, `No`
- mentorship — "Mentorship Program?" — select — options: `Yes`, `No`
- knowledgeMgmt — "Knowledge Management System" — text input — placeholder: `e.g., Confluence`

Documents

- FileDropzone — files via `FileDropzone`

---

## Step 5 — Commercial & Compliance

Pricing

- rateSenior — "Senior Staff Rate ($/hr)" — text input — placeholder: `e.g., 125-165`
- rateMid — "Mid-level Staff Rate ($/hr)" — text input — placeholder: `e.g., 95-125`
- rateOverhead — "Overhead Rate (%)" — number input
- rateProfit — "Target Profit Margin (%)" — number input

Contracting / Terms

- paymentTerms — "Standard Payment Terms" — select — options: `Net 30`, `Net 45`, `Net 60`
- ipTerms — "Intellectual Property Rights" — text input — placeholder: `e.g., Client owns work product`
- liability — "Limitation of Liability" — text input — placeholder: `e.g., Capped at contract value`

Compliance

- farCompliant — "FAR Compliant?" — select — options: `Yes`, `No`, `N/A`
- hipaaCompliant — "HIPAA Compliant?" — select — options: `Yes`, `No`, `N/A`
- fedramp — "FedRAMP Authorization" — select — options: `Yes`, `No`, `N/A`
- gdpr — "GDPR Compliant?" — select — options: `Yes`, `No`, `N/A`

Organizational Certifications

- cmmiLevel — "CMMI Level" — select — options: `N/A`, `1`, `2`, `3`, `4`, `5`
- soc2 — "SOC 2 Type II Compliance?" — select — options: `Yes`, `No`

Documents

- FileDropzone — files via `FileDropzone`

---

## Step 6 — Risk, Data & Lifecycle

Risk & Continuity

- riskMethodology — "Risk Assessment Methodology" — textarea — placeholder: `Describe your process for identifying, assessing, and mitigating risks...`

BC/DR

- bcdrPlan — "BC/DR Plan Status" — select — options: `Tested`, `Documented`, `In Development`
- drTestDate — "Last Full-Scale DR Test" — date input
- rto — "RTO for Critical Systems (Hours)" — number input — placeholder: `4`
- rpo — "RPO for Critical Systems (Minutes)" — number input — placeholder: `15`

Data & Lifecycle

- dataStewards — "Data Steward Roles Defined?" — select — options: `Yes`, `No`
- mdmStrategy — "Master Data Management (MDM) Strategy" — text input — placeholder: `e.g., Centralized`
- retention — "Standard Data Retention Policy" — text input — placeholder: `e.g., 7 years for project data`
- storagePrimary — "Primary Data Storage Technology" — text input — placeholder: `e.g., AWS S3, SharePoint`

Documents

- FileDropzone — files via `FileDropzone`

---
