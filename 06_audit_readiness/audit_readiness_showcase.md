# 🔍 Audit Readiness — ResolvX

> **Phase 5 of 6 · Q1 2026 · Internal - Confidential**
> Lead Auditor: GRC Lead · Approver: CISO · Next Audit: Q1 2027

![ISO](https://img.shields.io/badge/ISO%2027001%3A2022-Clause%209.2-blue?style=flat-square)
![SOC2](https://img.shields.io/badge/SOC%202%20Type%20II-Substantially%20Ready-orange?style=flat-square)
![Audit](https://img.shields.io/badge/Audit%20Verdict-Satisfactory-brightgreen?style=flat-square)
![NC](https://img.shields.io/badge/Major%20NCs-0-brightgreen?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

---

## What This Phase Does

Phases 1-4 built the programme. Phase 5 tests it.

This phase performs ResolvX's first formal internal ISMS audit against ISO 27001:2022 Clause 9.2, tests all SOC 2 Trust Service Criteria controls, scores SOC 2 Type II readiness, and produces the corrective action plan that closes the remaining gaps before an external audit firm is engaged in H2 2026.

---

## Audit Snapshot

| Metric | Result |
|---|---|
| Controls Tested (ISO 27001) | 31 Annex A controls |
| Controls Tested (SOC 2 TSC) | 17 criteria across CC1-CC9 |
| Conformant | 37 |
| **Major Nonconformities** | **0** |
| Minor Nonconformities | 5 |
| Observations | 3 |
| Overall Verdict | **SATISFACTORY** |
| SOC 2 Readiness Rating | **SUBSTANTIALLY READY** |

---

## Minor Nonconformities

| ID | Control | Finding | CAP Action | Due |
|---|---|---|---|---|
| NC-001 | A5.12 - Data Classification | 2/10 sampled documents missing classification labels | F-001: Add labels to Workspace templates | 2026-04-15 |
| NC-002 | A5.17 / CC6.1 - MFA | Hardware FIDO2 keys not yet enforced for 8 admin accounts | F-002: Procure keys; update Okta policy | 2026-04-30 |
| NC-003 | A5.23 - SSO Coverage | 2 legacy SaaS tools not connected to Okta SSO | F-003: Configure SAML/OIDC integration | 2026-05-15 |
| NC-004 | A6.3 / CC2.2 - Training | Awareness training completion 93% - 8 employees overdue | F-004: Escalate to managers; automate LMS | 2026-04-01 |
| NC-005 | A8.8 / CC7.1 - Vuln Mgmt | 2 High severity Snyk findings open >30 days | F-005: Assign to sprint; Jira integration | 2026-03-31 |

> Zero major nonconformities. All 5 minor NCs are tracked in the CAP with owners and deadlines.

---

## Observations (Improvement Opportunities)

| ID | Control | Observation |
|---|---|---|
| OBS-001 | A5.9 - Asset Register | Inventory exists but not formalised as a standalone ISMS document with review cycle |
| OBS-002 | A5.28 - Evidence Handling | Procedures documented but not yet tested via a dedicated exercise inject |
| OBS-003 | A8.12 - DLP Coverage | DLP limited to Google Workspace rules - no dedicated DLP for S3/API/endpoint egress |

---

## Positive Findings

The following areas were rated Conformant with no gaps:

- **Policy Suite (A5.1)** - All 6 policies approved and current
- **Vendor Risk Management (A5.19 / CC9)** - Tier 1 assessments complete; DPAs in place for all data processors
- **Incident Response (A5.24-A5.27 / CC7.3-7.5)** - IR plan, 3 runbooks, tabletop exercise all complete and tested
- **Access Control (A5.15 / CC6.1-6.7)** - MFA 100% enforced; RBAC via Okta; quarterly access reviews evidenced
- **Privacy Programme (A5.34)** - ROPA, DSR process, GDPR breach notification all complete
- **Cryptography (A8.24)** - AES-256 at rest and TLS 1.3 in transit confirmed on all production systems
- **Monitoring and Logging (A8.15-A8.16)** - CloudTrail, Okta, and Datadog monitoring active; review cadence documented

---

## SOC 2 Type II Readiness by TSC Family

| TSC Family | Status | Gap Summary |
|---|---|---|
| CC1 - Control Environment | ✅ Ready | No gaps |
| CC2 - Communication | ⚠️ Partial | Training completion 93% (NC-004) |
| CC3 - Risk Assessment | ✅ Ready | No gaps |
| CC4 - Monitoring of Controls | ✅ Ready | No gaps |
| CC5 - Control Activities | ✅ Ready | No gaps |
| CC6 - Logical Access | ⚠️ Partial | Hardware key enforcement pending (NC-002) |
| CC7 - System Operations | ⚠️ Partial | Snyk High findings overdue (NC-005) |
| CC8 - Change Management | ✅ Ready | No gaps |
| CC9 - Risk Mitigation (Vendor) | ✅ Ready | No gaps |

---

## SOC 2 Type II Roadmap

```
Q2 2026 ──── Remediate all CAP actions ──── Select audit firm
    │
Jul 2026 ─── Pre-audit walkthrough with audit firm
    │
Aug 2026 ─── SOC 2 Type II observation period begins (6 months)
    │
Feb 2027 ─── Audit fieldwork
    │
Mar 2027 ─── SOC 2 Type II report issued
```

---

## Deliverables

| Document | Format | Purpose |
|---|---|---|
| 📊 `internal_audit_checklist.xlsx` | XLSX (2 sheets) | ISO 27001 + SOC 2 TSC control testing; 48 controls; finding per control |
| 📊 `corrective_action_plan.xlsx` | XLSX (register + dashboard) | 8 CAP actions with owners, due dates, verification methods; progress dashboard |
| 📄 `AUDIT-RPT-001.pdf` | PDF | Formal internal audit report for CISO and management review |
| 📄 `AUDIT-SOC2-001.pdf` | PDF | SOC 2 readiness scoring by TSC family; pre-audit checklist; Type II timeline |
| 📋 `evidence_library/README.md` | MD | Evidence library structure; naming standards; TSC-to-evidence mapping |

---

## Related Documents

| Document | Location |
|---|---|
| 📄 Audit Report (formal) | `06_audit_readiness/formal_artifact/audit_report.docx` |
| 📄 SOC 2 Readiness (formal) | `06_audit_readiness/formal_artifact/soc2_readiness_assessment.docx` |
| 📊 Audit Checklist | `06_audit_readiness/internal_audit_checklist.xlsx` |
| 📊 Corrective Action Plan | `06_audit_readiness/corrective_action_plan.xlsx` |
| 📂 Evidence Library | `06_audit_readiness/evidence_library/README.md` |
| 🔒 Policies (tested) | `03_policies_and_procedures/` |
| 🔴 IR Programme (tested) | `05_incident_response/` |
| 🤝 Vendor Risk (tested) | `04_vendor_risk/` |

---

*ResolvX GRC Program · Phase 5 - Audit Readiness · 2026*
