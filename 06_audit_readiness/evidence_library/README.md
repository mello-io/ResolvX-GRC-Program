# Evidence Library

**Owner:** GRC Lead - Derick G. Dmello | **Classification:** Internal - Confidential <br>
**Purpose:** Structured repository of audit evidence supporting ResolvX's ISMS and SOC 2 Type II readiness

> This directory is the auditor-facing evidence store. Every control tested in `internal_audit_checklist.xlsx` should have at least one piece of evidence linked or stored here. Evidence is organised by control domain to allow an external auditor to navigate directly to relevant artefacts.

---

## Directory Structure

```
evidence_library/
│
├── README.md                          
│
├── 01_governance/
│   ├── policy_approval_signatures/    ← CISO/CEO approval records for POL-001 to POL-006
│   ├── controls_owners_register/      ← Current controls ownership matrix
│   └── board_meeting_minutes/         ← IS agenda items from management reviews
│
├── 02_risk_management/
│   ├── risk_register/                 ← Current risk register (Phase 2)
│   ├── risk_assessment_methodology/   ← Scoring criteria document
│   └── risk_treatment_plan/           ← Treatment decisions and status
│
├── 03_access_control/
│   ├── okta_mfa_enforcement/          ← Screenshots: Okta MFA policy showing 100% enforcement
│   ├── access_review_records/         ← Quarterly access review exports (Q4 2025, Q1 2026)
│   ├── rbac_configuration/            ← Okta group-to-role mapping screenshots
│   ├── jml_process/                   ← Joiner/Mover/Leaver deprovisioning records (5 sample leavers)
│   └── privileged_access/             ← AWS IAM admin role config; root MFA enforcement
│
├── 04_vulnerability_management/
│   ├── snyk_reports/                  ← Monthly Snyk scan exports (Q1 2026)
│   ├── patch_sla_compliance/          ← Tracking sheet showing patch SLA status per finding
│   ├── pen_test_reports/              ← Annual penetration test report (when conducted)
│   └── guardduty_findings/            ← AWS GuardDuty findings summary Q1 2026
│
├── 05_incident_response/
│   ├── ir_plan_approval/              ← Signed IR-PLAN-001 v1.0
│   ├── tabletop_exercise/             ← Tabletop report (Feb 2026) and action item closure evidence
│   ├── incident_log/                  ← Sanitised incident log (Q1 2026) - no active incidents
│   └── runbook_versions/              ← Signed-off runbook versions (IR-RB-001/002/003)
│
├── 06_vendor_risk/
│   ├── vendor_register/               ← Current vendor register with DPA status
│   ├── tier1_assessments/             ← Completed assessments for 6 Tier 1 vendors
│   ├── dpa_copies/                    ← Executed DPAs for all data-processing vendors (Legal holds originals)
│   └── sub_processor_register/        ← Current sub-processor register
│
├── 07_privacy/
│   ├── ropa/                          ← Record of Processing Activities (controller + processor)
│   ├── dsr_log/                       ← Data Subject Request log (anonymised)
│   ├── breach_register/               ← Breach register (no entries Q1 2026)
│   └── gdpr_notification_templates/   ← Pre-drafted Art. 33/34 templates
│
├── 08_training_and_awareness/
│   ├── training_completion_records/   ← LMS export: completion by employee (Q1 2026)
│   ├── phishing_simulation_results/   ← Most recent phishing simulation report
│   └── awareness_materials/           ← Security awareness content/curriculum
│
├── 09_monitoring_and_logging/
│   ├── cloudtrail_config/             ← CloudTrail enabled in all regions - screenshot
│   ├── datadog_alerts/                ← Datadog alert configuration export
│   ├── okta_audit_logs/               ← Okta audit log retention settings screenshot
│   └── log_review_records/            ← Weekly log review records (Head of Cloud Ops)
│
├── 10_change_management/
│   ├── github_branch_protection/      ← Branch protection rules screenshot (all repos)
│   ├── pr_approval_samples/           ← Sample of 3 merged PRs showing review and approval
│   └── deployment_pipeline/           ← GitHub Actions workflow configuration
│
├── 11_cryptography/
│   ├── aws_kms_config/                ← KMS key configuration screenshot
│   ├── tls_verification/              ← SSL Labs or equivalent TLS 1.3 verification for public endpoints
│   └── s3_encryption_config/          ← S3 bucket encryption settings screenshot
│
├── 12_physical_security/
│   ├── aws_soc2_physical/             ← Relevant section of AWS SOC 2 Type II report (physical controls)
│   └── office_access_controls/        ← Badge access policy/configuration evidence
│
└── 13_audit_artefacts/
    ├── internal_audit_checklist.xlsx  ← Completed audit checklist (AUDIT-CL-001)
    ├── audit_report.docx              ← Internal audit report (AUDIT-RPT-001)
    ├── corrective_action_plan.xlsx    ← CAP register (AUDIT-CAP-001)
    └── soc2_readiness_assessment.docx ← SOC 2 readiness scoring (AUDIT-SOC2-001)
```

---

## Evidence Standards

All evidence stored in this library must meet the following standards:

| Requirement | Standard |
|---|---|
| **File format** | PDF preferred; screenshots as PNG; exports as CSV/XLSX |
| **Naming convention** | `YYYY-MM-DD_control-ref_description.ext` (e.g. `2026-01-15_CC6.1_okta-mfa-enforcement.png`) |
| **Date visible** | All screenshots must show the date captured - use OS date/time in screenshot |
| **Source visible** | System name and URL/path must be visible in screenshots |
| **Version controlled** | Replace rather than delete previous evidence; archive superseded files with date suffix |
| **Retention** | Minimum 5 years for SOC 2 audit evidence; 3 years for general ISMS evidence |
| **Access control** | Access restricted to GRC Lead, CISO, and named auditors - do not share publicly |

---

## Evidence Mapping to SOC 2 TSC

| TSC Criteria | Primary Evidence Location | Secondary Evidence |
|---|---|---|
| CC1.1 - Control Environment | `01_governance/policy_approval_signatures/` | `08_training_and_awareness/` |
| CC1.3 - Organisational Structure | `01_governance/controls_owners_register/` | - |
| CC2.2 - Internal Communication | `08_training_and_awareness/training_completion_records/` | `01_governance/` |
| CC3.1-3.2 - Risk Assessment | `02_risk_management/` | - |
| CC4.1 - Monitoring | `09_monitoring_and_logging/` | `04_vulnerability_management/` |
| CC5.1 - Control Activities | `13_audit_artefacts/internal_audit_checklist.xlsx` | All domains |
| CC6.1 - Logical Access | `03_access_control/okta_mfa_enforcement/` | `03_access_control/rbac_configuration/` |
| CC6.2 - Provisioning | `03_access_control/jml_process/` | - |
| CC6.3 - Access Removal | `03_access_control/access_review_records/` | `03_access_control/jml_process/` |
| CC6.6-6.7 - External/Transit | `11_cryptography/tls_verification/` | `09_monitoring_and_logging/` |
| CC6.8 - Malware | `04_vulnerability_management/` | `09_monitoring_and_logging/guardduty_findings/` |
| CC7.1 - Vulnerability Mgmt | `04_vulnerability_management/snyk_reports/` | `04_vulnerability_management/patch_sla_compliance/` |
| CC7.2 - Monitoring | `09_monitoring_and_logging/` | - |
| CC7.3-7.5 - Incident Response | `05_incident_response/` | - |
| CC8.1 - Change Management | `10_change_management/` | - |
| CC9.1-9.2 - Vendor Risk | `06_vendor_risk/` | - |

---

## Collection Cadence

| Evidence Type | Collection Frequency | Responsible |
|---|---|---|
| Access review exports | Quarterly | IT Admin |
| Snyk vulnerability reports | Monthly | DevSecOps |
| GuardDuty findings summary | Monthly | Head of Cloud Ops |
| Training completion report | Quarterly | GRC Lead |
| Log review records | Weekly (retained monthly) | Head of Cloud Ops |
| Vendor register updates | On change (30-day notice) | GRC Lead |
| Policy approval records | On approval or annual review | GRC Lead |
| Incident log | Ongoing; quarterly archive | GRC Lead |

---

## For External Auditors

During a SOC 2 Type II audit, the GRC Lead will provide auditors with read-only access to this evidence library via a shared secure folder. The following naming shortcuts apply:

- **"Policy evidence"** - see `01_governance/policy_approval_signatures/`
- **"Access control evidence"** - see `03_access_control/`
- **"Incident response evidence"** - see `05_incident_response/`
- **"Vendor assessment evidence"** - see `06_vendor_risk/tier1_assessments/`
- **"Monitoring evidence"** - see `09_monitoring_and_logging/`

Requests for additional evidence should be directed to: **GRC Lead - Derick G. Dmello**

---

*ResolvX GRC Program - Phase 5: Audit Readiness - Evidence Library - 2026*
