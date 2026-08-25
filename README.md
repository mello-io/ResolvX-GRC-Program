# ResolvX - GRC Compliance & Audit Readiness Program

> **Program Owner:** Derick Dmello - GRC Lead, Risk & Compliance, ResolvX
> **Status:** ✅ Completed - Phase 6: Trust Center 
> **Frameworks:** ISO 27001:2022 · SOC 2 Type II · NIST CSF 2.0 · PCI-DSS V4.0
> **Last Updated:** July 2026

---

## 🏢 About ResolvX

**ResolvX** is a mid-size cloud-native SaaS fintech company providing AI-powered financial resolution and dispute management services to enterprise clients. With a growing customer base handling sensitive financial and PII data, ResolvX is pursuing formal security compliance certification to meet enterprise client requirements, regulatory obligations, and establish a trustworthy security posture.

**Industry:** Financial Technology (FinTech) / SaaS
**Size:** ~120 employees + ~15 contractors | 3 cloud environments (AWS)
**Data Types:** PII, Financial Records, Transaction Data
**Compliance Targets:** SOC 2 Type II, ISO 27001, PCI-DSS v4.0 (deferred)

---

## 🎯 Program Mission

This repository documents the full lifecycle of ResolvX's internal GRC program from baseline gap assessment through control implementation, audit readiness, and the establishment of a public-facing Trust Center. It is designed to demonstrate what a mature, program-owner-level GRC initiative looks like in practice.

---

## 📁 Repository Structure

```
resolvx-grc-program/
│
├── 00_program_foundation/
│   ├── objectives_scope_goals.md            # Program charter 
│   ├── program_roadmap.md                   # Phased roadmap
│   ├── company_profile.md                   # ResolvX background & asset inventory 
│   ├── stakeholder_register.md              # Roles, owners, accountabilities
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 01_risk_management/
│   ├── risk_register.xlsx                   # Full risk register with heat map (v1.1 - 25 risks, 0 High/Critical residual)
│   ├── risk_methodology.md                  # Scoring criteria and approach 
│   ├── risk_summary_report.md               # Executive risk summary 
│   ├── threat_landscape.md                  # Industry-specific threat context
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 02_compliance_framework/
│   ├── iso27001_control_matrix.xlsx         # Annex A 2022 control mapping (v1.1 - 77/93 Implemented)
│   ├── soc2_tsc_mapping.xlsx                # SOC 2 TSC CC1–CC9 mapping (v1.1 - 29/44 Implemented)
│   ├── nist_csf2_mapping.xlsx               # NIST CSF 2.0 function mapping (v1.1 - 82/103 Implemented)
│   ├── gap_analysis_report.md               # Consolidated gap analysis
│   ├── controls_owners_register.md          # Control ownership assignments
│   └── formal_artifact/                     # Document folder for formal deliverables
│
├── 03_policies_and_procedures/
│   ├── 01_information_security_policy.md
│   ├── 02_acceptable_use_policy.md
│   ├── 03_access_control_policy.md
│   ├── 04_data_classification_policy.md
│   ├── 05_vendor_management_policy.md
│   ├── 06_privacy_programme.md
│   ├── 07_logging_monitoring_policy.md              
│   ├── 08_bcp_dr_policy.md                          
│   ├── 09_backup_recovery_policy.md                 
│   ├── 10_patch_management_policy.md                
│   ├── 11_asset_management_policy.md                
│   ├── 12_password_policy.md                        
│   ├── 13_change_management_policy.md               
│   ├── 14_risk_management_policy.md                 
│   ├── 15_incident_management_policy.md             
│   ├── 16_breach_management_policy.md               
│   ├── 17_root_cause_analysis_policy.md             
│   ├── 18_secure_sdlc_policy.md                     
│   ├── 19_dlp_policy.md                             
│   ├── 20_data_destruction_policy.md                
│   ├── 21_cryptography_key_management_policy.md     
│   ├── 22_cyber_security_policy.md                  
│   ├── 23_hr_security_policy.md                     
│   ├── 24_physical_environmental_security_policy.md 
│   ├── 25_clean_desk_clear_screen_policy.md         
│   ├── 26_policy_exception_governance_policy.md
│   ├── policy_exception_register.xlsx                  # Register to map any policy exceptions
│   ├── authorized_software_list.xlsx                   # Corporate + production dependency inventory     
│   └── formal_artifact/                                # Document folder for formal deliverables
│
├── 04_vendor_risk/
│   ├── tprm_vendor_register.xlsx                       # Inventory of third parties
│   ├── tprm_vendor_security_questionnaire.xlsx         # Questionnaire form to assess vendors
│   ├── tprm_tier1_assessment_reports.xlsx              # Completed assessments for the 6 T1 critical vendors
│   ├── tprm_subprocessor_register.xlsx                 # GDPR Art. 28 sub-processor register
│   ├── vendor_risk_showcase.md                         # Vendor risk summary
|   ├── tprm_assessment_report.md                       # client & prospect showcase TPRM Report
│   └── formal_artifact/                                # Document folder for formal deliverables
│
├── 05_incident_response/
│   ├── ir_plan.md                                      # IR Plan (ISO 27035 aligned)
│   ├── ir_runbooks/
│   │   ├── runbook_phishing.md
│   │   ├── runbook_ransomware.md
│   │   └── runbook_data_breach.md
│   ├── tabletop_simulation_report.xlsx                 # Ransomware tabletop (IR-TTX-001)
│   ├── dr_failover_tabletop_test_report.xlsx           # Disaster Recovery tabletop (DR-TTX-001)
│   ├── incident_log_template.xlsx
│   ├── security_monitoring_report.xlsx                 # Primary/Secondary monitoring evidence
│   └── formal_artifact/                                # Document folder for formal deliverables
│
├── 06_audit_readiness/
│   ├── evidence_library/
│   │   └── README.md                                   # Highlight of evidence to prepare for audit assessment
│   ├── audit_readiness_showcase.md                     # Audit Readiness Summary
│   ├── internal_audit_checklist.xlsx                   # Control testing checklist
│   ├── corrective_action_plan.xlsx                     # CAP with owners and dates
│   └── formal_artifact/                                # Document folder for formal deliverables
│
├── 07_compliance_dashboard/
│   └── compliance_dashboard.xlsx                       # Control coverage & risk status                  
│
└── 08_trust_center/                         
    └── index.html                                      # Public-facing trust center

```

---

## 🗺️ Program Phases

| Phase | Focus | Status |
|-------|-------|--------|
| **Phase 1** | Foundation: Company profile, scope, risk methodology | ✅ Complete |
| **Phase 2** | Risk & Controls: Risk register, framework mapping, gap analysis | ✅ Complete |
| **Phase 3** | Policies & Vendor Risk: Policy library, vendor assessments | ✅ Complete |
| **Phase 4** | Incident Response: IR plan, runbooks, tabletop simulation | ✅ Complete |
| **Phase 5** | Audit Readiness: Internal audit, evidence collection, CAP | ✅ Complete |
| **Phase 6** | Compliance Dashboard & Trust Center | ✅ Complete |

---

## 📄 Foundation Documents

| Document | Description |
|----------|-------------|
| [Objectives, Scope & Goals](./00_program_foundation/objectives_scope_goals.md) | Program charter defining what we're building and why |
| [Program Roadmap](./00_program_foundation/program_roadmap.md) | Phased plan with milestones and deliverables |
| [Company Profile](./00_program_foundation/company_profile.md) | Company background, tech stack, and asset inventory |
| [Stakeholder Register](./00_program_foundation/stakeholder_register.md) | Roles, control ownership, and escalation path |

> Note: Detailed formal documentation (PDF) can be found inside `/00_program_foundation/formal_artifact/`.

---

## 🔗 Trust Center

The Trust Center is a production-ready, single-file HTML page designed for sharing with enterprise clients during security reviews. It covers ResolvX's full security posture, compliance status, data practices, and incident response commitments.

**Live:** [mello-io.github.io/ResolvX-GRC-Program](https://mello-io.github.io/ResolvX-GRC-Program/)

| Section | Content |
| --- | --- |
| Security Posture | Control domains across identity, cloud, endpoint, vulnerability management, monitoring, awareness which is backed by 26 policies |
| Compliance | ISO 27001:2022 (83% Implemented), SOC 2 Type II (FULLY READY), NIST CSF 2.0, GDPR |
| Data Practices | EU data residency, encryption standards, retention, access controls, sub-processor register (14 vendors) |
| Incident Response | IR lifecycle, P1–P4 SLA table, 2 tested tabletop exercises, client notification commitments |
| Vendor Security | TPRM programme summary, 6 Tier 1 vendors with certification and DPA status |

---

*This program is a self-directed GRC portfolio project simulating a real-world compliance initiative. All company information is fictional and created for educational and portfolio purposes.*
