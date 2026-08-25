# 🛡️ TPRM Assessment Report — ResolvX

> **RPT-TPRM-001 · v1.0 · 2026-07-31 · Public — Client & Prospect Facing**
> Owner: GRC Lead · Methodology: Tiered TPRM (POL-005) · Review: Quarterly

![Classification](https://img.shields.io/badge/Classification-Public-brightgreen?style=flat-square)
![Audience](https://img.shields.io/badge/Audience-Clients%20%26%20Prospects-blue?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

---

## Why This Report Exists

When a prospective client evaluates ResolvX, they are doing exactly what ResolvX does to every vendor in its own supply chain — assessing a third party's access to sensitive data. This report is the client-facing companion to `vendor_risk_showcase.md`, built to answer both directions of that question in one place: **how ResolvX manages third-party risk, and how ResolvX itself would score if a prospect assessed it the same way.**

Unlike most of this repository, this document is intentionally public — designed to be shared during enterprise security reviews and sales cycles, not gated behind an NDA.

---

## At a Glance

| Direction | Result |
|---|---|
| **Downstream** — vendors ResolvX assesses | 14 vendors under management, 100% of Tier 1/Tier 2 formally assessed, 13/13 required DPAs executed |
| **Upstream** — ResolvX as a vendor to its clients | 26 policies covering every VSQ domain, SOC 2 Type II Fully Ready, ISO 27001 83% Implemented, 0 open audit nonconformities as of 2026-07-31 |

---

## Part A — How ResolvX Manages Third-Party Risk

Full detail lives in `vendor_risk_showcase.md` and the underlying registers. Summary:

- Every vendor tiered at onboarding by data sensitivity and operational centrality — not contract size or tenure
- Tier 1 vendors (AWS, Okta, GitHub, Google Workspace, Jamf, 1Password) formally assessed against a 9-domain Vendor Security Questionnaire and re-assessed annually
- All 6 Tier 1 vendors carry a current SOC 2 Type II report; where ISO 27001 certification is absent (Okta, Jamf, 1Password), that SOC 2 report is treated as offsetting evidence, explicitly noted rather than silently accepted
- Sub-processors disclosed under GDPR Article 28, with a 30-day advance notification commitment before any material change

---

## Part B — ResolvX as Your Third Party

If you assessed ResolvX the way ResolvX assesses its own vendors, here is how it would answer — organised by the same domains the VSQ uses.

| Domain | Current Posture |
|---|---|
| **Governance & Security Programme** | 26 formal, version-controlled policies (POL-001–026), each with a named owner and annual review cycle. ISMS approved at CISO level. |
| **Access Control & Identity** | MFA enforced for 100% of users via Okta SSO. Admin accounts require FIDO2 hardware keys. Quarterly access reviews. Same-day access revocation on termination. |
| **Data Protection & Encryption** | Four-tier data classification. AES-256 at rest, TLS 1.2+ in transit. DLP scope and roadmap formally documented, with any residual gap explicitly risk-accepted rather than hidden. |
| **Vulnerability Management** | Continuous SAST/SCA scanning via Snyk, auto-ticketed on High/Critical. SLA: Critical 7 days, High 30 days, Medium 60 days, Low 90 days. Zero High findings open past SLA as of 2026-07-31. |
| **Incident Response** | Documented IR Plan, 3 runbooks, universal reporting obligation, P1–P4 severity framework. Two tabletop exercises on record (ransomware, DR/BCP failover). |
| **Business Continuity** | RTO/RPO targets by asset criticality. Tested via a live DR failover exercise (2026-07-30) — 98% of Critical-tier RTO budget, data integrity independently verified. |
| **Personnel Security** | Tiered background screening. Mandatory security training at 100% completion. Formal disciplinary process; confidentiality obligations survive termination. |
| **Sub-processors & Supply Chain** | Same disclosure and 30-day notification standard covered in Part A — applied to what we tell you about ours. |

### Current Certification & Audit Status

| Framework | Status |
|---|---|
| ISO 27001:2022 | 83% Implemented |
| SOC 2 Type II | Fully Ready (98%) — auditor engagement in progress |
| NIST CSF 2.0 | 82/103 subcategories Implemented |
| Internal Audit (re-performed 2026-07-31) | 0 major nonconformities, 0 minor nonconformities (down from 5), 2 observations remain |

We show the gaps as readily as the certifications — a report with no open items would be less credible, not more. The two remaining observations: one is a documented, accepted risk (DLP tooling scope); the other is tracked for a dedicated verification exercise (evidence-handling, never yet tested live).

---

## What This Means For Prospective Clients

Your data is only as safe as the weakest vendor in our supply chain — and we know the same is true of us, in yours. Every claim in Part B is backed by the same kind of evidence we require from our own vendors: a real audit, a real policy, a real tested exercise.

---

## Full Report

> 📄 **[Download Full TPRM Assessment Report (.pdf)](./formal_artifact/tprm_assessment_report.pdf)**
> *Formal version with the complete Tier 1 assessment table, sub-processor data residency detail, and document control history.*

---

## Related Documents

| Document | Location |
|---|---|
| 🤝 Vendor Risk & TPRM Overview | `vendor_risk_showcase.md` |
| 🤝 Vendor Management Policy | `03_policies_and_procedures/05_vendor_management_policy.md` |
| 🔍 Audit Results | `06_audit_readiness/audit_readiness_showcase.md` |
| 🌐 Trust Center | Public — hosted via GitHub Pages |

---

*ResolvX GRC Program · Public — Client & Prospect Facing · 2026-07-31*
