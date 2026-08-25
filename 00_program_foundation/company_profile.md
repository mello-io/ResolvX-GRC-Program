# 🏢 ResolvX: Company Profile & Asset Inventory

> **Program:** GRC Compliance & Audit Readiness | **Phase:** 1 - Foundation | **Version:** 1.1

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-blue?style=flat-square)
![Classification](https://img.shields.io/badge/Classification-Internal-yellow?style=flat-square)
![Owner](https://img.shields.io/badge/Owner-GRC%20Lead-lightgrey?style=flat-square)

---

## Overview

| Attribute | Detail |
|---|---|
| **Legal Name** | ResolvX Inc. |
| **Founded** | 2021 |
| **Headquarters** | New York, NY, United States |
| **Industry** | Financial Technology (FinTech) / SaaS |
| **Business Model** | B2B SaaS : subscription-based platform licensing |
| **Employees** | ~120 full-time + ~15 contractors |
| **Cloud Provider** | Amazon Web Services (AWS) : Primary |
| **Primary Region** | us-east-1 (N. Virginia) with DR in us-west-2 |

---

## Product & Service

### What ResolvX Does

ResolvX provides a **cloud-native, AI-powered dispute management platform** for financial institutions, payment processors, insurance providers, and e-commerce enterprises. The platform centralizes and automates the entire dispute lifecycle, from initial complaint intake through investigation, evidence collection, regulatory reporting, and case resolution.

Think of it like a hub for financial disputes: banks, credit unions, fintechs, and payment processors of any size plug into ResolvX and manage all dispute workflows through a single, compliance-aware interface, regardless of their vertical or internal infrastructure.

### Platform Capabilities

- 🤖 AI-assisted dispute intake, triage, and case creation
- 📁 Multi-channel evidence collection and document management
- ⏱️ Regulatory timeline tracking (Visa, Mastercard, Reg E, Reg Z)
- 🔗 Merchant communication and chargeback management portal
- 📊 Real-time reporting and full audit trail generation
- 🔌 API integrations with core banking systems, payment processors, and CRMs

### Client Verticals

| Vertical | Use Case | Data Handled |
|---|---|---|
| Retail Banks & Credit Unions | Consumer dispute management | PII, Transaction Data |
| Payment Processors | Chargeback workflow automation | Financial Records, PII |
| Insurance Providers | Claim dispute tracking | PII, Health-adjacent |
| E-Commerce Platforms | Seller-buyer arbitration | PII, Transaction Data |
| Neobanks & Fintechs | Embedded dispute resolution | PII, Financial Records |

---

## Organizational Structure

| Department | Head Count | Function |
|---|---|---|
| Engineering & Cloud Ops | 45 | Platform development, infrastructure, DevSecOps |
| Product | 12 | Roadmap, UX, compliance features |
| Customer Success | 18 | Onboarding, support, client relationships |
| Sales & Marketing | 15 | Enterprise sales, demand generation |
| Finance & Legal | 8 | Financial ops, contracts, regulatory counsel |
| HR & Operations | 7 | People ops, vendor management |
| GRC & Security | 5 | Security operations, compliance, risk management |
| Executive Team | 4 | CEO, CTO, CFO, CISO |

---

## Technology Asset Inventory

### ☁️ AWS Cloud Infrastructure

| Asset | Environment | Service | Data Classification | Criticality |
|---|---|---|---|---|
| Production VPC | Production | AWS VPC / EC2 / EKS | Confidential / PII | 🔴 Critical |
| Database Cluster | Production | Amazon RDS (PostgreSQL) | Confidential / PII / Financial | 🔴 Critical |
| Object Storage | Production | Amazon S3 | Confidential / PII | 🟠 High |
| Identity & Access | All | AWS IAM / AWS SSO | Internal | 🔴 Critical |
| Secrets Management | All | AWS Secrets Manager | Restricted | 🔴 Critical |
| CDN & API Gateway | Production | CloudFront / API GW | Public / Internal | 🟠 High |
| Logging & Monitoring | All | CloudWatch / CloudTrail | Internal | 🟠 High |
| Staging Environment | Staging | AWS EC2 / EKS | Internal / Test Data | 🟡 Medium |
| Dev Environment | Development | AWS EC2 | Internal / Synthetic | 🟢 Low |

### 💻 Corporate IT Assets

| Asset | Count | Management | Classification |
|---|---|---|---|
| MacBook Pro (Laptops) | ~120 | Jamf MDM | Internal |
| Microsoft 365 | ~135 licenses | M365 Admin Center | Internal / Confidential |
| GitHub Enterprise | ~60 seats | GitHub Org Admin | Internal / Restricted |
| Slack Business+ | ~135 seats | Slack Admin | Internal |
| Notion (Knowledge Base) | ~80 seats | Notion Admin | Internal |
| 1Password (Credentials) | ~135 seats | 1Password Teams | Restricted |

### 🔗 Third-Party Subprocessors

| Vendor | Service | Data Access | Tier |
|---|---|---|---|
| AWS | Cloud infrastructure (IaaS) | All system data (hosting provider) | 🔴 Tier 1: Critical |
| Okta | Identity & Access Management (SSO, MFA) | Employee identity & auth data | 🔴 Tier 1: Critical |
| GitHub (Microsoft) | Source code management, CI/CD | Source code, secrets risk | 🔴 Tier 1: Critical |
| Google Workspace | Email, Docs, Drive, Meet | Internal comms, some client comms | 🔴 Tier 1: Critical |
| Jamf | Mobile device management (endpoint) | Device inventory & compliance data | 🔴 Tier 1: Critical |
| 1Password | Enterprise credential management | Credential metadata (not plaintext) | 🔴 Tier 1: Critical |
| Slack (Salesforce) | Internal team messaging | Internal comms (Confidential/Internal) | 🟠 Tier 2: High |
| Jira / Confluence (Atlassian) | Issue tracking, internal wiki | Internal project data, some security docs | 🟠 Tier 2: High |
| Datadog | Monitoring & observability | System logs, performance metrics | 🟠 Tier 2: High |
| Snyk | SAST/SCA vulnerability scanning | Source code references, vulnerability data | 🟠 Tier 2: High |
| Rippling | HRIS & payroll processing | Employee PII, payroll, benefits data | 🟠 Tier 2: High |
| Stripe | Payment processing (subscription billing) | Payment card data (PCI DSS scope) | 🟠 Tier 2: High |
| Zoom | Video conferencing | Meeting metadata, limited comms content | 🟡 Tier 3: Medium |
| Notion | Internal knowledge base | Internal documentation (Internal tier) | 🟡 Tier 3: Medium |

---

## Data Classification

| Level | Definition | Examples | Controls |
|---|---|---|---|
| 🔴 **Restricted** | Highest sensitivity : regulatory obligation | Card data, auth secrets, encryption keys | Encryption, MFA, strict ACL, audit logging |
| 🟠 **Confidential** | Sensitive business or customer data | PII, financial records, dispute case files | Encryption at rest/transit, access control, DLP |
| 🟡 **Internal** | Operational data : not for public release | Employee records, source code, internal docs | Access control, need-to-know |
| 🟢 **Public** | Approved for external release | Marketing content, public API docs | Review and approval process |

---

## Regulatory & Compliance Obligations

| Regulation / Standard | Applicability | Driver |
|---|---|---|
| **SOC 2 Type II** | Service organization : enterprise client requirement | Commercial : client contracts |
| **PCI-DSS v4.0** | Cardholder data environment via Stripe | Regulatory : payment card brands |
| **ISO 27001:2022** | ISMS : global enterprise expectation | Commercial / Certification target |
| **NIST CSF 2.0** | Internal security program framework | Best practice / Risk management |
| **GLBA** | Financial data for US bank clients | Regulatory : US federal law |
| **CCPA** | California consumer PII | Regulatory : state law |
| **GDPR** | EU client data where applicable | Regulatory : EU law |

---

## Formal Artifact

> 📄 **[Download Full Company Profile (.pdf)](./formal_artifact/company_profile.pdf)**
> *Formal version with complete asset tables, signatures, and document control.*

---

*ResolvX GRC Program, Internal Use Only, v1.1, 2026*
