# ResolvX — GRC Compliance & Audit Readiness Program

> **Program Owner:** Derick Dmello — GRC Lead, Risk & Compliance, ResolvX  
> **Status:** 🔵 In Progress — Phase 6: Trust Center  
> **Frameworks:** ISO 27001:2022 · SOC 2 Type II · NIST CSF 2.0 · PCI-DSS v4.0  
> **Last Updated:** March 2026

---

## 🏢 About ResolvX

**ResolvX** is a mid-size cloud-native SaaS fintech company providing AI-powered financial resolution and dispute management services to enterprise clients. With a growing customer base handling sensitive financial and PII data, ResolvX is pursuing formal security compliance certification to meet enterprise client requirements, regulatory obligations, and establish a trustworthy security posture.

**Industry:** Financial Technology (FinTech) / SaaS  
**Size:** ~120 employees | 3 cloud environments (AWS)  
**Data Types:** PII, Financial Records, Transaction Data  
**Compliance Targets:** SOC 2 Type II, ISO 27001, PCI-DSS v4.0

---

## 🎯 Program Mission

This repository documents the full lifecycle of ResolvX's internal GRC program — from baseline gap assessment through control implementation, audit readiness, and the establishment of a public-facing Trust Center. It is designed to demonstrate what a mature, program-owner-level GRC initiative looks like in practice.

---

## 📁 Repository Structure

```
resolvx-grc-program/
│
├── 00_program_foundation/
│   ├── objectives_scope_goals.md            # Living document — program charter
│   ├── program_roadmap.md                   # Phased roadmap with milestones
│   ├── company_profile.md                   # ResolvX background & asset inventory
│   ├── stakeholder_register.md              # Roles, owners, accountabilities
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 01_risk_management/
│   ├── risk_register.xlsx                   # Full risk register with heat map
│   ├── risk_methodology.md                  # Scoring criteria and approach
│   ├── risk_summary_report.md               # Executive risk summary
│   ├── threat_landscape.md                  # Industry-specific threat context
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 02_compliance_framework/
│   ├── iso27001_control_matrix.xlsx         # Annex A 2022 control mapping
│   ├── soc2_criteria_mapping.xlsx           # SOC 2 TSC CC1–CC9 mapping
│   ├── nist_csf_mapping.xlsx                # NIST CSF 2.0 function mapping
│   ├── gap_analysis_report.md               # Consolidated gap analysis
│   ├── control_owners_register.md           # Control ownership assignments
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 03_policies_and_procedures/
│   ├── information_security_policy.md
│   ├── access_control_policy.md
│   ├── incident_response_policy.md
│   ├── data_classification_policy.md
│   ├── vendor_management_policy.md
│   ├── acceptable_use_policy.md
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 04_vendor_risk/
│   ├── vendor_register.xlsx                 # Inventory of third parties
│   ├── vendor_security_questionnaire.xlsx   # Questionnaire form to assess vendors
│   ├── tprm_tier1_assessment.xlsx           # Completed assessments for the 6 T1 critical vendors
│   └── tprm_sub-processor_register.xlsx     # How ResolvX amanges self and client data
│
├── 05_incident_response/
│   ├── ir_plan.md                           # IR plan (ISO 27035 aligned)
│   ├── ir_runbooks/
│   │   ├── runbook_phishing.md
│   │   ├── runbook_ransomware.md
│   │   └── runbook_data_breach.md
│   ├── tabletop_simulation_report.xlsx      # Tabletop exercise results
│   ├── incident_log_template.xlsx
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 06_audit_readiness/
│   ├── internal_audit_checklist.xlsx        # Control testing checklist
│   ├── evidence_library/                    # Screenshots, configs, logs
│   │   └── README.md
│   ├── audit_readiness_showcase.md          # Highlight of Audit Readiness program
│   ├── corrective_action_plan.xlsx          # CAP with owners and dates
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 07_compliance_dashboard/
│   └── compliance_dashboard.xlsx            # Control coverage & risk status
│
└── 08_trust_center/
    └── trust_center.html                    # Public-facing trust center

```

---

## 🗺️ Program Phases

| Phase | Focus | Status |
|-------|-------|--------|
| **Phase 1** | Foundation — Company profile, scope, risk methodology | ✅ Completed |
| **Phase 2** | Risk & Controls — Risk register, framework mapping, gap analysis | ✅ Completed |
| **Phase 3** | Policies & Vendor Risk — Policy library, vendor assessments | ✅ Completed |
| **Phase 4** | Incident Response — IR plan, runbooks, tabletop simulation | ✅ Completed |
| **Phase 5** | Audit Readiness — Internal audit, evidence collection, CAP | ✅ Completed |
| **Phase 6** | Trust Center — Dashboard, public trust narrative, certifications | 🔵 In Progress |

---

## 📄 Foundation Documents

| Document | Description |
|----------|-------------|
| [Objectives, Scope & Goals](./00_program_foundation/objectives_scope_goals.md) | Program charter defining what we're building and why |
| [Program Roadmap](./00_program_foundation/program_roadmap.md) | Phased plan with milestones and deliverables |

> Note : Detailed documenation can be found inside ` /00_program_foundation/formal_artifacts/ `.

---

## 🔗 Trust Center

The Trust Center is a production-ready, single-file HTML page designed for sharing with enterprise clients during security reviews. It covers ResolvX's full security posture, compliance status, data practices, and incident response commitments.

**Live:** [mello-io.github.io/ResolvX-GRC-Program](https://mello-io.github.io/ResolvX-GRC-Program/)

| Section | Content |
| --- | --- |
| Security Posture | 6 control domains: identity, cloud, endpoint, vulnerability management, monitoring, awareness |
| Compliance | ISO 27001:2022, SOC 2 Type II status, GDPR, NIST CSF 2.0, NIST SP 800-61 |
| Data Practices | EU data residency, encryption standards, retention, access controls, GDPR obligations, sub-processors |
| Incident Response | 5-stage response lifecycle · P1–P4 SLA table · client notification commitments |
| Vendor Security | TPRM programme summary · 6 key vendors with certification and DPA status |


---

*This program is a self-directed GRC portfolio project simulating a real-world compliance initiative. All company information is fictional and created for educational and portfolio purposes.*
