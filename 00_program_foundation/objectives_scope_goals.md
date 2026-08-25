# 🎯 ResolvX: Objectives, Scope & Goals

> **Program:** GRC Compliance & Audit Readiness | **Phase:** 1 (Foundation) | **Version:** 1.1

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-blue?style=flat-square)
![Classification](https://img.shields.io/badge/Classification-Internal-yellow?style=flat-square)
![Owner](https://img.shields.io/badge/Owner-GRC%20Lead-lightgrey?style=flat-square)

---

## Executive Summary

ResolvX is a cloud-native SaaS fintech company providing AI-powered dispute management services to enterprise financial clients. As the business scales and onboards regulated institutions, a formal and defensible security compliance posture is both a commercial and regulatory necessity.

This document is the formal charter for the ResolvX GRC program. It defines the purpose, scope, target frameworks, and measurable goals that govern all compliance and risk management activities, from baseline through to audit readiness and Trust Center launch.

---

## Program Objectives

### 1️⃣ Establish a Risk-Aware Culture
- Implement a structured, repeatable risk management process aligned to ISO 31000 and NIST RMF
- Ensure all business units understand their risk responsibilities through defined control ownership
- Maintain a live risk register that reflects the current threat landscape

### 2️⃣ Achieve Compliance Certification
- Attain **SOC 2 Type II** certification within 18 months of program initiation
- Align controls with **ISO 27001:2022** Annex A in preparation for future certification
- Ensure **PCI-DSS v4.0** compliance for all cardholder data environments

### 3️⃣ Build Audit-Ready Evidence Practices
- Establish a structured evidence library supporting all major framework requirements
- Conduct quarterly internal audits to validate control effectiveness
- Maintain continuous compliance monitoring through a live compliance dashboard

### 4️⃣ Launch a Public Trust Center
- Publish a customer-facing Trust Center documenting security posture, certifications, and privacy practices
- Provide near-real-time compliance status visibility to enterprise prospects and clients

---

## Scope

### ✅ In Scope

| Scope Item | Description | Applicable Frameworks |
|---|---|---|
| AWS Cloud Infrastructure | 3 environments: Production, Staging, Dev (us-east-1) | ISO 27001, SOC 2, NIST CSF |
| SaaS Application | ResolvX core platform (dispute resolution app) | SOC 2, PCI-DSS |
| Corporate IT | Laptops, M365, SaaS tools (Slack, Notion, GitHub) | ISO 27001, NIST CSF |
| Data Processing | PII, financial records, client dispute data | PCI-DSS, SOC 2, ISO 27001 |
| Third-Party Vendors | AWS, Okta, GitHub, Google Workspace, Jamf, 1Password (Tier 1: see `tprm_vendor_register.xlsx`) | ISO 27001, SOC 2 |
| Personnel | All full-time employees and contractors with system access | ISO 27001, SOC 2 |

### ❌ Out of Scope
- Physical office security (leased facility, landlord responsibility)
- Personal devices not enrolled in MDM
- Acquired subsidiaries pending integration assessment

---

## Target Compliance Frameworks

| Framework | Version | Purpose | Target Date & Status |
|---|---|---|---|
| **SOC 2 Type II** | AICPA TSC 2017 | Primary certification (enterprise client requirement) | Q4 2026: ✅ ON TRACK, ahead of schedule (readiness assessment: FULLY READY as of 2026-07-31, auditor engagement pending) |
| **ISO 27001** | 2022 Edition | ISMS baseline (controls and risk management) | Q2 2027: ✅ ON TRACK (77/93 controls Implemented as of 2026-07-31) |
| **NIST CSF** | 2.0 (2024) | Internal security program structure and maturity | Ongoing |
| **PCI-DSS** | v4.0 | Payment card data protection | Q3 2026: ⚠️ Deliberately deferred, no PCI-DSS work completed this cycle; revised target needed once scope is resumed |

---

## Goals & Success Metrics

| Goal | Success Metric | Target Phase & Status |
|---|---|---|
| Complete baseline risk assessment | Risk register with 15+ risks, scored and mitigated | Phase 2: ✅ ACHIEVED: 25 risks registered (target: 15+) |
| Map all controls to frameworks | 90%+ control coverage across SOC 2 TSC and ISO 27001 | Phase 2: ✅ ACHIEVED: 100% of ISO Annex A and SOC 2 TSC controls mapped |
| Develop full policy library | 8+ policies authored, approved, and version-controlled | Phase 3: ✅ EXCEEDED: 26 policies (POL-001–026) authored, approved, version-controlled |
| Complete vendor assessments | 100% of Tier 1 vendors assessed and scored | Phase 3: ✅ ACHIEVED: 6/6 Tier 1 vendors assessed (`tprm_vendor_register.xlsx`) |
| IR plan tested | Tabletop simulation completed with documented findings | Phase 4: ✅ ACHIEVED: ransomware tabletop (IR-TTX-001) + DR failover tabletop (2026-07-30), findings documented and closed |
| Internal audit completed | Audit report with CAP issued and tracked | Phase 5: ✅ ACHIEVED: audit re-run 2026-07-31, CAP tracked, 7/8 findings closed |
| Trust Center live | Public page with certs, controls, and privacy summary | Phase 6: ✅ ACHIEVED: dashboard and Trust Center both delivered, hosted via GitHub Pages |

---

## Roles & Responsibilities

| Role | Responsibility |
|---|---|
| 🎯 **GRC Lead** *(Program Owner)* | Program strategy, roadmap, policy development, audit liaison |
| 🛡️ **CISO / VP Engineering** | Executive sponsor (approves policies, escalation point) |
| ☁️ **IT / Cloud Operations** | Control implementation, evidence collection, infrastructure security |
| ⚖️ **Legal & Privacy** | Regulatory compliance, data protection, contract reviews |
| 👤 **HR** | Security awareness, personnel security controls |
| 🏢 **Department Heads** | Control owners within their business units |

---

## Formal Artifact

> 📄 **[Download Full Program Charter (.pdf)](./formal_artifact/objectives_scope_goals.pdf)**
> *Formal version with complete scope tables, approval signatures, and document control history.*

---

*ResolvX GRC Program, Internal Use Only, v1.1, 2026*
