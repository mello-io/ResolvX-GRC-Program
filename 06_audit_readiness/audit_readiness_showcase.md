# 🔍 Audit Readiness — ResolvX

> **Phase 5 of 6 · Re-Audited 2026-07-31 (baseline: Q1 2026) · Internal - Confidential**
> Lead Auditor: GRC Lead · Approver: CISO · Next Full Audit: Q1 2027

![ISO](https://img.shields.io/badge/ISO%2027001%3A2022-Clause%209.2-blue?style=flat-square)
![SOC2](https://img.shields.io/badge/SOC%202%20Type%20II-Fully%20Ready-brightgreen?style=flat-square)
![Audit](https://img.shields.io/badge/Audit%20Verdict-Satisfactory-brightgreen?style=flat-square)
![NC](https://img.shields.io/badge/Major%20NCs-0-brightgreen?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

---

## What This Phase Does

Phases 1-4 built the programme. Phase 5 tests it — and, as of 2026-07-31, has tested it twice.

This phase performs ResolvX's internal ISMS audit against ISO 27001:2022 Clause 9.2, tests all SOC 2 Trust Service Criteria controls, scores SOC 2 Type II readiness, and produces the corrective action plan that closes gaps before external audit engagement. The original Q1 2026 baseline audit found 5 minor nonconformities; all five were re-tested and closed by 2026-07-31, following delivery of the full POL-007–026 policy suite.

---

## Audit Snapshot — Then and Now

| Metric | Q1 2026 Baseline | Re-Audit 2026-07-31 |
|---|---|---|
| Controls Tested (ISO 27001) | 31 Annex A controls | 31 (same sample) |
| Controls Tested (SOC 2 TSC) | 17 criteria across CC1-CC9 | 17 (same sample) |
| Conformant | 37 | **46** |
| **Major Nonconformities** | **0** | **0** |
| Minor Nonconformities | 5 | **0** |
| Observations | 3 | **2** (1 closed, 1 closed via formal risk acceptance) |
| Overall Verdict | SATISFACTORY | **SATISFACTORY** |
| SOC 2 Readiness Rating | SUBSTANTIALLY READY | **FULLY READY (98%)** |

---

## Minor Nonconformities — All Closed

| ID | Control | Original Finding | Closure |
|---|---|---|---|
| NC-001 | A5.12 - Data Classification | 2/10 sampled documents missing classification labels | ✅ Closed — labels added to Workspace templates, re-tested against full 10-document sample |
| NC-002 | A5.17 / CC6.1 - MFA | Hardware FIDO2 keys not yet enforced for 8 admin accounts | ✅ Closed — keys deployed, Okta admin group policy enforced |
| NC-003 | A5.23 - SSO Coverage | 2 legacy SaaS tools not connected to Okta SSO | ✅ Closed — full 14/14 vendor SSO coverage confirmed |
| NC-004 | A6.3 / CC2.2 - Training | Awareness training completion 93% - 8 employees overdue | ✅ Closed — 100% completion (120/120), automated LMS escalation configured |
| NC-005 | A8.8 / CC7.1 - Vuln Mgmt | 2 High severity Snyk findings open >30 days | ✅ Closed — both remediated, Snyk-Jira auto-ticketing now in place |

---

## Observations

| ID | Control | Status |
|---|---|---|
| OBS-001 | A5.9 - Asset Register | ✅ Closed — formalised as POL-011 (Asset Management Policy), document-controlled with an annual review cycle |
| OBS-002 | A5.28 - Evidence Handling | 🟠 Still open — an Evidence/Chain-of-Custody Log template now exists (IR Plan Appendix B), but has not yet been exercised in a live incident or dedicated tabletop |
| OBS-003 | A8.12 - DLP Coverage | ✅ Closed (Risk Accepted) — POL-019 documents current scope and a phased roadmap; the residual coverage gap is a formal, CISO-approved risk acceptance under POL-014 §5, not an unmanaged gap |

---

## Positive Findings

- **Policy Suite (A5.1)** — 26 policies approved and current (up from 6 at baseline)
- **Vendor Risk Management (A5.19 / CC9)** — Tier 1 assessments complete; DPAs in place for all data processors
- **Incident Response (A5.24-A5.27 / CC7.3-7.5)** — IR plan v1.1, 3 runbooks, **two** tabletop exercises complete and tested (ransomware Feb 2026, DR/BCP failover Jul 2026)
- **Access Control (A5.15 / CC6.1-6.7)** — MFA 100% enforced; RBAC via Okta; quarterly access reviews evidenced
- **Privacy Programme (A5.34)** — ROPA, DSR process, GDPR + US breach notification framework (POL-016) all complete
- **Cryptography (A8.24)** — AES-256 at rest and TLS 1.2+ in transit confirmed on all production systems
- **Monitoring and Logging (A8.15-A8.16)** — CloudTrail, Okta, and Datadog monitoring active; formal Logging & Monitoring Policy (POL-007) with a staged SIEM roadmap

---

## SOC 2 Type II Readiness by TSC Family

| TSC Family | Q1 2026 | Re-Audit 2026-07-31 |
|---|---|---|
| CC1 - Control Environment | ✅ Ready | ✅ Ready |
| CC2 - Communication | ⚠️ Partial (training gap) | ✅ **Ready** |
| CC3 - Risk Assessment | ✅ Ready | ✅ Ready |
| CC4 - Monitoring of Controls | ✅ Ready | ✅ Ready |
| CC5 - Control Activities | ✅ Ready | ✅ Ready |
| CC6 - Logical Access | ⚠️ Partial (hardware key gap) | ✅ **Ready** |
| CC7 - System Operations | ⚠️ Partial (Snyk findings) | ✅ **Ready** |
| CC8 - Change Management | ✅ Ready | ✅ Ready |
| CC9 - Risk Mitigation (Vendor) | ✅ Ready | ✅ Ready |

**All 9 TSC families now Ready** — up from 6 of 9 at baseline.

---

## SOC 2 Type II Roadmap — Updated

```
✅ COMPLETE ── CAP remediation (all 5 minor NCs closed, 2026-07-31)
    │
🔵 NEXT ────── Select audit firm; pre-audit walkthrough
    │
2026-Q4 ────── SOC 2 Type II observation period begins (6 months)
    │
2027-Q2 ────── Audit fieldwork
    │
2027-Q3 ────── SOC 2 Type II report issued
```

CAP remediation finished ahead of the original Q2 2026 target — every control-level prerequisite for engaging an auditor is now in place. The only remaining work is procedural: firm selection, evidence library handoff, and the walkthrough.

---

## Deliverables

| Document | Format | Purpose |
|---|---|---|
| 📊 `internal_audit_checklist.xlsx` | XLSX (2 sheets) | ISO 27001 + SOC 2 TSC control testing; 48 controls; re-tested 2026-07-31 |
| 📊 `corrective_action_plan.xlsx` | XLSX (register + dashboard) | 8 CAP actions — 7 closed, 1 open (F-007); progress dashboard |
| 📄 `AUDIT-RPT-001.pdf` | PDF | Formal internal audit report (v1.1) — original findings preserved, closure verification added |
| 📄 `AUDIT-SOC2-001.pdf` | PDF | SOC 2 readiness scoring by TSC family (v1.1) — FULLY READY |
| 📊 `security_monitoring_report.xlsx` | XLSX | Primary/secondary monitoring evidence supporting POL-007 |
| 📋 `evidence_library/README.md` | MD | Evidence library structure; naming standards; TSC-to-evidence mapping |

---

## Related Documents

| Document | Location |
|---|---|
| 📄 Audit Report (formal) | `06_audit_readiness/formal_artifact/AUDIT-RPT-001.pdf` |
| 📄 SOC 2 Readiness (formal) | `06_audit_readiness/formal_artifact/AUDIT-SOC2-001.pdf` |
| 📊 Audit Checklist | `06_audit_readiness/internal_audit_checklist.xlsx` |
| 📊 Corrective Action Plan | `06_audit_readiness/corrective_action_plan.xlsx` |
| 📂 Evidence Library | `06_audit_readiness/evidence_library/README.md` |
| 📊 Compliance Dashboard | `07_compliance_dashboard/compliance_dashboard.xlsx` |
| 🔒 Policies (tested) | `03_policies_and_procedures/` |
| 🔴 IR Programme (tested) | `05_incident_response/` |
| 🤝 Vendor Risk (tested) | `04_vendor_risk/` |

---

*ResolvX GRC Program · Phase 5 - Audit Readiness · Re-Audited 2026-07-31*
