# 🤝 Vendor Risk & TPRM — ResolvX

> **POL-005 · v1.0 · 2026 · Internal — Confidential**
> Owner: GRC Lead · Approver: CISO · Review: Annual + event-triggered

![ISO](https://img.shields.io/badge/ISO%2027001%3A2022-A5.19–A5.23-blue?style=flat-square)
![SOC2](https://img.shields.io/badge/SOC%202-CC9.1%20CC9.2-orange?style=flat-square)
![NIST](https://img.shields.io/badge/NIST%20CSF%202.0-GV.SC--01–10-purple?style=flat-square)
![NIST800](https://img.shields.io/badge/NIST%20800--53B-SR--1%20to%20SR--12-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

---

## What This Phase Does

Third parties represent one of the most significant and least directly controllable risk surfaces in any organisation's security posture. A vendor with access to ResolvX client data, financial records, or production infrastructure can introduce risk that no internal control can fully compensate for.

This phase establishes ResolvX's Third-Party Risk Management (TPRM) framework — a structured, tiered approach to assessing, contracting, monitoring, and offboarding vendors. Every vendor that touches ResolvX data or systems is classified, assessed, and subject to ongoing review.

---

## TPRM Snapshot

| Metric | Result |
|---|---|
| Total Vendors in Register | 18 |
| Tier 1 — Critical | 6 |
| Tier 2 — High | 5 |
| Tier 3 — Medium | 4 |
| Tier 4 — Low | 3 |
| Tier 1 Assessments Complete | 6 / 6 |
| DPAs Executed (data processors) | 100% |
| SOC 2 Type II confirmed (Tier 1) | 6 / 6 |
| Outstanding Assessment Actions | 0 |

---

## Vendor Risk Tier Model

| Tier | Risk Level | Criteria | Review Frequency |
|---|---|---|---|
| **Tier 1 — Critical** | Very High | Access to Restricted data; core infrastructure; single point of failure | Annual + event-triggered |
| **Tier 2 — High** | High | Access to Confidential data; significant BCP dependency; material sub-processors | Annual |
| **Tier 3 — Medium** | Medium | Internal data access only; limited dependency; replaceable within 30 days | Biennial or on renewal |
| **Tier 4 — Low** | Low | No data access; no integration; commodity services | Lightweight onboarding check |

Tier assignment is made by the GRC Lead at onboarding and reviewed annually.

---

## Tier 1 — Critical Vendor Assessment Results

| Vendor | Service | Data Accessed | SOC 2 Type II | DPA | Assessment Outcome |
|---|---|---|---|---|---|
| **Amazon Web Services** | Cloud infrastructure (IaaS) | All system data | ✅ Confirmed | ✅ AWS DPA | Pass — no material gaps |
| **Okta** | Identity Provider (SSO + MFA) | Employee identity data | ✅ Confirmed | ✅ DPA | Pass — no material gaps |
| **GitHub (Microsoft)** | Source code management | Source code, secrets risk | ✅ Confirmed | ✅ DPA | Pass — secrets scanning enforced |
| **Google Workspace** | Email, docs, collaboration | Internal + client comms | ✅ Confirmed | ✅ DPA | Pass — data residency confirmed |
| **Jamf** | MDM — device management | Device inventory, compliance | ✅ Confirmed | ✅ DPA | Pass — no material gaps |
| **1Password** | Credential management | Credential metadata | ✅ Confirmed | ✅ DPA | Pass — no material gaps |

> All six Tier 1 vendors hold current SOC 2 Type II reports reviewed by the GRC Lead. DPAs are executed for all vendors processing personal data on ResolvX's behalf.

---

## Vendor Security Questionnaire (VSQ)

The VSQ is the primary assessment tool for Tier 1 and Tier 2 vendors. Completed at onboarding and at each reassessment. Nine domains scored and documented in the Vendor Register:

| Domain | Key Assessment Areas |
|---|---|
| **Governance** | Formal security programme, named owner, annual risk assessments |
| **Access Control** | MFA enforcement, access reviews, principle of least privilege |
| **Data Protection** | Encryption at rest/transit, data residency, retention and disposal |
| **Vulnerability Management** | Patching cadence, penetration testing, vulnerability disclosure |
| **Incident Response** | Documented IR plan, breach notification timeline, incident history |
| **Business Continuity** | RTO/RPO targets, DR test results, uptime SLA |
| **Compliance** | SOC 2, ISO 27001, PCI DSS certifications; regulatory obligations |
| **Sub-processors** | Sub-processor disclosure, security requirements flowing downstream |
| **Personnel Security** | Background checks, security awareness training for staff with data access |

---

## Sub-Processor Register

ResolvX maintains a sub-processor register covering all vendors that process personal data on its behalf as a data processor (GDPR Article 28). Key controls:

- Sub-processors are disclosed to enterprise clients via the Trust Center
- Material new sub-processors require prior client notification and a 30-day objection window
- All sub-processors must have executed DPAs with ResolvX
- Sub-processor register is reviewed quarterly by the GRC Lead

---

## Contractual Security Requirements

All Tier 1 and Tier 2 contracts, and any contract involving personal data access, include the following minimum provisions:

| Clause | Requirement |
|---|---|
| **Security obligations** | Vendor maintains an ISMS appropriate to engagement risk |
| **Incident notification** | 72-hour notification of any confirmed or suspected incident affecting ResolvX data |
| **Data handling** | Processing permitted only for defined contractual purposes |
| **Sub-processor disclosure** | Prior consent required before adding material new sub-processors |
| **Audit rights** | ResolvX may request independent audit report (e.g., SOC 2 Type II) at any time |
| **Data return / deletion** | All ResolvX data returned or deleted within 30 days of termination with written confirmation |
| **Change notification** | Material changes to security posture, ownership, or certifications must be notified |
| **DPA (where applicable)** | GDPR Article 28-compliant DPA executed before personal data processing commences |

---

## Framework Mapping

| Control Reference | Area | Status |
|---|---|---|
| ISO A5.19 | Information security in supplier relationships | ✅ Implemented |
| ISO A5.20 | Addressing security within supplier agreements | ✅ Implemented |
| ISO A5.21 | Managing security in the ICT supply chain | ✅ Implemented |
| ISO A5.22 | Monitoring, review and change management of supplier services | ✅ Implemented |
| ISO A5.23 | Security for use of cloud services | ✅ Implemented |
| SOC 2 CC9.1 | Vendor risk management programme | ✅ Implemented |
| SOC 2 CC9.2 | Vendor monitoring and reassessment | ✅ Implemented |
| NIST CSF GV.SC-01–10 | Cybersecurity supply chain risk management | ✅ Implemented |

---

## Ongoing Monitoring Schedule

| Activity | Tier | Frequency | Owner |
|---|---|---|---|
| Full VSQ reassessment | Tier 1 | Annual | GRC Lead |
| SOC 2 / audit report review | Tier 1 & 2 | Annual | GRC Lead |
| Access log review | Tier 1 | Quarterly | IT Admin |
| Vendor Register review | All | Quarterly | GRC Lead |
| Event-triggered reassessment | All | On breach / ownership change | GRC Lead |
| Sub-processor register review | All | Quarterly | GRC Lead + Legal |

---

## Deliverables

| Document | Format | Purpose |
|---|---|---|
| 📊 `tprm_vendor_register.xlsx` | XLSX | Full vendor register — tier, data types, assessment status, contract dates, DPA status |
| 📊 `tprm_tier1_assessment_reports.xlsx` | XLSX | Scored VSQ responses for all 6 Tier 1 vendors; findings and treatment decisions |
| 📊 `tprm_vendor_security_questionnaire.xlsx` | XLSX | Blank VSQ template used for all Tier 1 and Tier 2 assessments |
| 📊 `tprm_subprocessor_register.xlsx` | XLSX | Sub-processor register — vendor, data processed, DPA status, client disclosure |
| 📄 POL-005 | DOCX | Vendor Management Policy — full TPRM framework, lifecycle, contractual requirements |

---

## Related Documents

| Document | Location |
|---|---|
| 🤝 Vendor Management Policy | `03_policies_and_procedures/05_vendor_management_policy.md` |
| 🔒 Access Control Policy | `03_policies_and_procedures/03_access_control_policy.md` |
| 🔒 Privacy Programme | `03_policies_and_procedures/06_privacy_programme.md` |
| 🔍 Audit Results — CC9 | `06_audit_readiness/audit_readiness_showcase.md` |
| 🌐 Sub-processor List (public) | Trust Center |

---

*ResolvX GRC Program · Phase 3 — Vendor Risk · 2026*
