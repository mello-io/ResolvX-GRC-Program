# 📊 ResolvX: Information Security Risk Summary Report

> **Program:** GRC Compliance & Audit Readiness | **Phase:** 2 (Risk & Controls) | **Version:** 2.0

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Phase](https://img.shields.io/badge/Phase-2%20Risk%20%26%20Controls-purple?style=flat-square)
![Classification](https://img.shields.io/badge/Classification-Confidential-red?style=flat-square)
![Audience](https://img.shields.io/badge/Audience-CISO%20%7C%20Leadership%20%7C%20Board-navy?style=flat-square)
![Methodology](https://img.shields.io/badge/Methodology-NIST%20SP%20800--30%20%7C%20FAIR-blue?style=flat-square)

---

## Executive Summary

This report presents ResolvX's current information security risk posture, updated July 2026 following delivery of the full 26-policy suite (POL-001–026), re-scoring of 19 of 25 risks against the controls those policies formalise, and a re-run internal audit. The original baseline assessment (Phase 2, early 2026) is preserved in Document Control below as historical record and this version reflects where the programme actually stands today.

**25 risks remain under active management** across five categories: Cyber Threat, Cloud & Infrastructure, Vendor & Third-Party, Compliance & Regulatory, and Human & Operational.

### Key Findings at a Glance

| Metric | Finding |
|---|---|
| **Total risks assessed** | 25 across 5 categories |
| **Critical risks (residual)** | 0 |
| **High risks (residual)** | 0, down from 8 at baseline |
| **Moderate risks (residual)** | 7, down from 11 |
| **Low risks (residual)** | 8 |
| **Very Low risks (residual)** | 10; up from 1, including 10 risks now formally Mitigated |
| **Risks fully Mitigated** | 10 of 25 |
| **Risks with treatment plans** | 25 / 25: all risks have documented treatment decisions |
| **Overall risk trajectory** | ⬇️ Improving: no risk sits above Moderate residual for the first time in the programme's history |

> **Assessment Date:** July 2026 | **Next Review:** December 2026 | **Risk Owner:** GRC Lead

---

## 1. Risk Posture Overview

### 1.1 Residual Risk Distribution: Then and Now

| Risk Level | Baseline (Early 2026) | Current (July 2026) | Delta |
|---|---|---|---|
| 🔴 **Critical** (20–25) | 0 | 0 | . |
| 🔴 **High** (12–19) | 8 | 0 | ⬇️ -8 |
| 🟠 **Moderate** (7–11) | 11 | 7 | ⬇️ -4 |
| 🟡 **Low** (4–6) | 5 | 8 | ⬆️ +3 |
| 🟢 **Very Low** (1–3) | 1 | 10 | ⬆️ +9 |

Every one of the original 8 High residual risks has moved to Moderate or lower. Ten risks are now formally Mitigated (closed via a named policy, a tested control, or both), not just reclassified on paper.

### 1.2 Risk Distribution by Category

| Category | Risks | Highest Residual Level | Primary Driver (Current) |
|---|---|---|---|
| 🛡️ **Cyber Threat** | 5 | 🟠 Moderate | Ransomware, API exploitation, supply chain; all formally governed, controls maturing |
| ☁️ **Cloud & Infrastructure** | 5 | 🟠 Moderate | S3 misconfiguration, IAM over-privilege; CIS baseline enforced, named tooling gaps remain |
| 🔗 **Vendor & Third-Party** | 5 | 🟠 Moderate | AWS concentration and Stripe/PCI scope; deliberately deferred, not overlooked |
| 📋 **Compliance & Regulatory** | 5 | 🟢 Very Low | SOC 2 now FULLY READY, GDPR framework formalised via POL-006/POL-016 |
| 👥 **Human & Operational** | 5 | 🟢 Very Low | Offboarding, change management, key-person risk all Mitigated |

---

## 2. Top Moderate Residual Risks

With no risk remaining above Moderate, these seven represent the programme's current highest-priority attention, not urgent escalations, but the risks worth continued investment.

### 🟠 RSK-001: Ransomware Attack
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Moderate), down from 12 |
| **What changed** | Immutable S3 backup vault deployed; ransomware tabletop exercise conducted and findings closed (POL-008, POL-009) |
| **Control Owner** | Head of Cloud Ops |
| **What remains** | Continued control maturity: backup restoration testing now quarterly per POL-009 |

### 🟠 RSK-003: API Vulnerability Exploitation
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Moderate), down from 10 |
| **What changed** | Continuous Snyk SAST/SCA scanning in CI/CD; 30-day patch SLA with auto-ticketing (POL-010) |
| **Control Owner** | DevSecOps Engineer |
| **What remains** | Annual penetration test still not formally scheduled |

### 🟠 RSK-005: Software Supply Chain Attack
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Moderate), down from 12 |
| **What changed** | SAST/SCA fully deployed in CI/CD; secure SDLC formalised (POL-018) |
| **Control Owner** | DevSecOps Engineer |
| **What remains** | Formal SBOM generation and code signing still on the roadmap |

### 🟠 RSK-006: AWS S3 Misconfiguration
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Moderate), down from 10 |
| **What changed** | CIS baseline enforced, public S3 access disabled by policy (POL-022) |
| **Control Owner** | Head of Cloud Ops |
| **What remains** | Monthly CSPM review not yet a standing cadence |

### 🟠 RSK-008: IAM Over-Privilege
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Moderate), down from 12 |
| **What changed** | Least-privilege baseline formalised, PAM requirements defined (POL-022, POL-003 §7) |
| **Control Owner** | Head of Cloud Ops |
| **What remains** | Full IAM Access Analyzer deployment and SCPs still pending |

### 🟠 RSK-011: AWS Vendor Concentration
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Moderate), unchanged |
| **What changed** | Shared-responsibility model documented; no technical mitigation attempted this cycle |
| **Control Owner** | GRC Lead |
| **What remains** | Multi-cloud evaluation is a strategic decision, not a control gap; deliberately not pursued yet |

### 🟠 RSK-012: Stripe Integration Breach (PCI Scope)
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Moderate), unchanged |
| **What changed** | Nothing: deliberately deferred |
| **Control Owner** | GRC Lead |
| **What remains** | PCI-DSS v4.0 scope is pending dedicated engagement (see `objectives_scope_goals.md`) |

---

## 3. FAIR Quantitative Risk Analysis

**Methodology note:** FAIR analysis was originally triggered for risks scoring 12+ (High/Critical). With no risk currently scoring above 11, that threshold no longer selects anything, so this section now covers the 7 Moderate risks instead, to preserve executive visibility into financial exposure even as the underlying risk levels have improved.

| Risk ID | Risk | Res. Level | ALE Low | ALE High | ALE Mid |
|---|---|---|---|---|---|
| RSK-001 | Ransomware attack | 🟠 Moderate | $140,000 | $520,000 | $330,000 |
| RSK-003 | API vulnerability exploitation | 🟠 Moderate | $120,000 | $400,000 | $260,000 |
| RSK-005 | Supply chain attack | 🟠 Moderate | $90,000 | $340,000 | $215,000 |
| RSK-006 | AWS S3 misconfiguration | 🟠 Moderate | $80,000 | $320,000 | $200,000 |
| RSK-008 | IAM over-privilege | 🟠 Moderate | $60,000 | $230,000 | $145,000 |
| RSK-011 | AWS vendor concentration | 🟠 Moderate | $70,000 | $280,000 | $175,000 |
| RSK-012 | Stripe integration breach (PCI) | 🟠 Moderate | $250,000 | $850,000 | $550,000 |
| **TOTAL** | **All quantified risks** | | **$810,000** | **$2,940,000** | **$1,875,000** |

> **Note:** ALE figures represent annualised probable loss ranges, reduced from the baseline assessment in proportion to the control improvements each risk saw. RSK-012 (Stripe/PCI) is unchanged since no PCI-DSS work was undertaken this cycle so it remains the largest single exposure in the portfolio precisely because it was deliberately deferred, not because it was overlooked.

---

## 4. Risk Treatment Progress

### 4.1 Risks Fully Mitigated This Cycle (10 of 25)

| Risk ID | Risk | Closed Via |
|---|---|---|
| RSK-009 | Secrets management gaps | POL-012, POL-010, POL-021 |
| RSK-010 | Logging & monitoring gaps | POL-007 |
| RSK-013 | Okta break-glass credential handling | POL-012 §5 |
| RSK-014 | Vendor security posture | POL-005 |
| RSK-016 | SOC 2 certification risk | POL-001–026 + POL-016: FULLY READY, auditor engagement pending |
| RSK-017 | GDPR violation | POL-006 + POL-016 |
| RSK-022 | Offboarding gaps | POL-023 §8: same-day revocation |
| RSK-023 | Key-person dependency | Entire 26-policy suite formalises what was previously undocumented knowledge |
| RSK-024 | Change management gaps | POL-013 |
| RSK-025 | BCP/DR absence | POL-008, POL-009 + DR Failover Tabletop Test Report |

### 4.2 Treatment Timeline: Remaining Work

| Horizon | Risks | Focus Area |
|---|---|---|
| **In progress** | RSK-001, RSK-003, RSK-005, RSK-006, RSK-008 | Continued control maturity: CSPM cadence, IAM Access Analyzer, penetration testing, SBOM |
| **Deliberately deferred** | RSK-012, RSK-018 | PCI-DSS v4.0 scope: defered for now |
| **Untouched, low priority** | RSK-011, RSK-015, RSK-019, RSK-020 | AWS concentration (strategic), email spoofing, CCPA intake, SLA/commercial |

---

## 5. Risk Programme Observations

### What Changed
The three themes flagged as the programme's focus areas in the baseline assessment (detection & response, cloud posture discipline, and compliance programme execution) are the same three themes that drove nearly all of this cycle's improvement. POL-007 (Logging & Monitoring) closed the detection gap. POL-022 (Cyber Security) and POL-013 (Change Management) closed the cloud posture cluster. The full policy suite plus the re-run internal audit closed the compliance execution risk. This wasn't a coincidence: the policy build was sequenced specifically to hit the risk register's own priority order.

### Where the Programme Should Focus Next
The 7 remaining Moderate risks split into two genuinely different categories: five (RSK-001, 003, 005, 006, 008) are control-maturity work already in progress with named next steps. Two (RSK-011, RSK-012) are **not gaps**: they're risks the programme has looked at and deliberately not acted on yet, for defensible reasons (AWS concentration is a strategic multi-cloud decision, not a quick fix; PCI-DSS is explicitly Step 3 scope). Treating these two identically to the first five would misrepresent the programme's actual priorities.

### Risk Appetite Alignment
ResolvX's stated risk appetite (Low for cybersecurity, Very Low for compliance) is now more fully realised than at baseline; compliance risk in particular moved from the highest-exposure category to the lowest. No risk sits unattended above its documented treatment plan.

---

## 6. Board-Level Actions: Status

| Original Recommendation | Status |
|---|---|
| Approve security budget for SIEM/CSPM tooling (Q1 2026) | ✅ Delivered: POL-007 formalises logging/monitoring with a staged SIEM roadmap |
| Formally engage a SOC 2 auditor by Q3 2026 | 🟠 In progress: readiness is FULLY READY as of July 2026; auditor selection is the next concrete step |
| Initiate GDPR data mapping and DSR programme (Q2 2026) | ✅ Delivered: POL-006 + POL-016 |
| **New recommendation** | Engage a PCI-DSS QSA or advisory firm to scope RSK-012 and RSK-018, the single largest remaining exposure in the portfolio, currently unaddressed by design rather than oversight |

---

## 7. Document Control

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0 | 2026 | Derick G. Dmello, GRC Lead | Initial risk summary report: Phase 2 baseline assessment |
| 2.0 | July 2026 | Derick G. Dmello, GRC Lead | Full re-derivation against the delivered 26-policy suite and re-run internal audit. 8 High residual risks closed to Moderate or lower; 10 risks formally Mitigated; FAIR threshold adjusted to reflect the improved risk profile |

---

## Formal Artifact

> 📄 **[Download Full Risk Summary Report (.pdf)](./formal_artifact/risk_summary_report.pdf)**
> *Formal version with complete risk tables, FAIR decomposition, approval signatures, and document control history.*

---

*ResolvX GRC Programme, Confidential, For Internal Distribution and Authorised External Reviewers Only, v2.0, 2026*
*Methodology: NIST SP 800-30 Rev. 1 (Qualitative) | FAIR (Quantitative) | ISO/IEC 27001:2022*
