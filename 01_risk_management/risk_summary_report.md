# 📊 ResolvX — Information Security Risk Summary Report

> **Program:** GRC Compliance & Audit Readiness | **Phase:** 2 — Risk & Controls | **Version:** 1.0

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Phase](https://img.shields.io/badge/Phase-2%20Risk%20%26%20Controls-purple?style=flat-square)
![Classification](https://img.shields.io/badge/Classification-Confidential-red?style=flat-square)
![Audience](https://img.shields.io/badge/Audience-CISO%20%7C%20Leadership%20%7C%20Board-navy?style=flat-square)
![Methodology](https://img.shields.io/badge/Methodology-NIST%20SP%20800--30%20%7C%20FAIR-blue?style=flat-square)

---

## Executive Summary

ResolvX has completed its inaugural formal information security risk assessment as part of Phase 2 of the GRC Compliance & Audit Readiness Programme. This report presents the findings to organisational leadership, providing a clear view of ResolvX's current risk posture, the financial exposure associated with top risks, and the remediation priorities required to achieve target compliance certifications and protect client trust.

**25 risks were identified and assessed** across five categories: Cyber Threat, Cloud & Infrastructure, Vendor & Third-Party, Compliance & Regulatory, and Human & Operational. The assessment was conducted using the NIST SP 800-30 Rev. 1 methodology for qualitative scoring and the FAIR (Factor Analysis of Information Risk) model for financial quantification of high and critical risks.

### Key Findings at a Glance

| Metric | Finding |
|---|---|
| **Total risks assessed** | 25 across 5 categories |
| **Critical risks (residual)** | 0 — all critical inherent risks reduced through controls |
| **High risks (residual)** | 8 requiring treatment plans within 30 days |
| **Moderate risks (residual)** | 11 requiring treatment plans within 90 days |
| **Low / Very Low risks (residual)** | 6 — accepted or monitored |
| **Total FAIR ALE exposure** | $1.83M – $6.52M annualised across quantified risks |
| **Top single risk ALE** | RSK-001 Ransomware — $350K – $1.2M/year |
| **Risks with treatment plans** | 25 / 25 — all risks have documented treatment decisions |
| **Overall risk trajectory** | ⬇️ Improving — controls are reducing residual scores across all categories |

> **Assessment Date:** 2026 | **Next Review:** Q2 2026 | **Risk Owner:** GRC Lead

---

## 1. Risk Posture Overview

### 1.1 Inherent vs Residual Risk Distribution

The following table shows how ResolvX's current controls are shifting risk levels from inherent (before controls) to residual (after controls). This movement is the primary indicator of control programme effectiveness.

| Risk Level | Inherent Count | Residual Count | Delta |
|---|---|---|---|
| 🔴 **Critical** (20–25) | 8 | 0 | ⬇️ -8 |
| 🔴 **High** (12–19) | 10 | 8 | ⬇️ -2 |
| 🟠 **Moderate** (7–11) | 5 | 11 | ↑ +6 (risk correctly categorised after control credit) |
| 🟡 **Low** (4–6) | 2 | 5 | ↑ +3 |
| 🟢 **Very Low** (1–3) | 0 | 1 | ↑ +1 |

The shift of 8 Critical inherent risks to High or Moderate residual demonstrates that existing controls - Okta MFA, AWS GuardDuty, EDR, multi-AZ architecture, and GitHub branch protection - are providing meaningful risk reduction. However, **8 High residual risks remain** and represent the programme's immediate action priority.

### 1.2 Risk Distribution by Category

| Category | Risks | Highest Residual Level | Primary Driver |
|---|---|---|---|
| 🛡️ **Cyber Threat** | 5 | 🔴 High | Ransomware, phishing, API exploitation |
| ☁️ **Cloud & Infrastructure** | 5 | 🔴 High | IAM over-privilege, S3 misconfiguration |
| 🔗 **Vendor & Third-Party** | 5 | 🟠 Moderate | No formal TPRM programme |
| 📋 **Compliance & Regulatory** | 5 | 🔴 High | SOC 2 Type II not yet certified |
| 👥 **Human & Operational** | 5 | 🟠 Moderate | Offboarding gaps, BCP absence |

---

## 2. Top 8 High Residual Risks

These risks require formal treatment plans and active remediation. Each is assigned a named control owner and target completion date.

### 🔴 RSK-001 — Ransomware Attack
| Field | Detail |
|---|---|
| **Residual Score** | 12 (Likelihood 3 × Impact 4) |
| **Threat Source** | Organised cybercriminal group (RaaS) |
| **Core Vulnerability** | No immutable backup vault; tabletop simulation not conducted |
| **FAIR ALE** | $350,000 - $1,200,000 / year |
| **Control Owner** | Head of Cloud Ops |
| **Treatment** | Deploy AWS Backup vault lock; implement immutable S3 backups; conduct ransomware tabletop |
| **Target** | Q2 2026 |

### 🔴 RSK-003 — API Vulnerability Exploitation
| Field | Detail |
|---|---|
| **Residual Score** | 10 (Likelihood 2 × Impact 5) |
| **Threat Source** | External attacker : opportunistic/targeted |
| **Core Vulnerability** | Quarterly scanning insufficient; no penetration test completed |
| **FAIR ALE** | $280,000 – $950,000 / year |
| **Control Owner** | DevSecOps Engineer |
| **Treatment** | Weekly vulnerability scanning; establish 30-day CVE SLA; conduct annual penetration test |
| **Target** | Q1 2026 |

### 🔴 RSK-004 — Insider Threat / Data Exfiltration
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Likelihood 2 × Impact 4) |
| **Threat Source** | Malicious or negligent insider |
| **Core Vulnerability** | No DLP tooling; no UEBA; access reviews not quarterly |
| **FAIR ALE** | $150,000 – $600,000 / year |
| **Control Owner** | GRC Lead |
| **Treatment** | Implement DLP; deploy UEBA alerting; enforce quarterly access reviews |
| **Target** | Q3 2026 |

### 🔴 RSK-005 — Software Supply Chain Attack
| Field | Detail |
|---|---|
| **Residual Score** | 12 (Likelihood 3 × Impact 4) |
| **Threat Source** | Nation-state / sophisticated threat actor |
| **Core Vulnerability** | No SBOM; SAST not fully deployed; no software vetting process |
| **FAIR ALE** | $200,000 – $800,000 / year |
| **Control Owner** | DevSecOps Engineer |
| **Treatment** | Implement SBOM generation; enforce code signing; full SAST/SCA in CI/CD |
| **Target** | Q2 2026 |

### 🔴 RSK-006 — AWS S3 Misconfiguration
| Field | Detail |
|---|---|
| **Residual Score** | 10 (Likelihood 2 × Impact 5) |
| **Threat Source** | Internal — configuration error |
| **Core Vulnerability** | IaC not fully enforced; no monthly CSPM review |
| **FAIR ALE** | $180,000 – $750,000 / year |
| **Control Owner** | Head of Cloud Ops |
| **Treatment** | Implement Security Hub CIS checks; enforce IaC policy guardrails; monthly CSPM review |
| **Target** | Q1 2026 |

### 🔴 RSK-008 — IAM Over-Privilege
| Field | Detail |
|---|---|
| **Residual Score** | 12 (Likelihood 3 × Impact 4) |
| **Threat Source** | External attacker exploiting over-privileged roles post-compromise |
| **Core Vulnerability** | No formal PAM programme; IAM Access Analyzer not deployed |
| **FAIR ALE** | $130,000 – $520,000 / year |
| **Control Owner** | Head of Cloud Ops |
| **Treatment** | Full IAM access review; deploy IAM Access Analyzer; implement SCPs |
| **Target** | Q2 2026 |

### 🔴 RSK-016 — SOC 2 Type II Certification Failure
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Likelihood 2 × Impact 4) |
| **Threat Source** | Internal — programme execution risk |
| **Core Vulnerability** | Audit engagement not yet initiated; policies not yet published |
| **FAIR ALE** | $500,000+ in ARR pipeline risk |
| **Control Owner** | GRC Lead |
| **Treatment** | Execute GRC programme roadmap; engage auditor by Q3 2026; complete Phase 3 policy suite |
| **Target** | Q3 2026 |

### 🔴 RSK-017 — GDPR Violation
| Field | Detail |
|---|---|
| **Residual Score** | 8 (Likelihood 2 × Impact 4) |
| **Threat Source** | Internal process gap / data subject request failure |
| **Core Vulnerability** | No ROPA; no DSR process; GDPR data mapping incomplete |
| **FAIR ALE** | $200,000 – $2,000,000 / year |
| **Control Owner** | General Counsel |
| **Treatment** | Conduct GDPR data mapping; implement DSR process; complete ROPA |
| **Target** | Q2 2026 |

---

## 3. FAIR Quantitative Risk Analysis

FAIR analysis was applied to all risks scoring 12 or above (High/Critical) on the residual 5×5 matrix. The following table presents the full financial exposure picture.

### 3.1 Annualised Loss Expectancy (ALE) Summary

| Risk ID | Risk | Res. Level | ALE Low | ALE High | ALE Mid |
|---|---|---|---|---|---|
| RSK-001 | Ransomware attack | 🔴 High | $350,000 | $1,200,000 | $775,000 |
| RSK-002 | Phishing / credential theft | 🟠 Moderate | $95,000 | $420,000 | $257,500 |
| RSK-003 | API vulnerability exploitation | 🔴 High | $280,000 | $950,000 | $615,000 |
| RSK-004 | Insider threat / exfiltration | 🔴 High | $150,000 | $600,000 | $375,000 |
| RSK-005 | Supply chain attack | 🔴 High | $200,000 | $800,000 | $500,000 |
| RSK-006 | AWS S3 misconfiguration | 🔴 High | $180,000 | $750,000 | $465,000 |
| RSK-008 | IAM over-privilege | 🔴 High | $130,000 | $520,000 | $325,000 |
| RSK-012 | Stripe integration breach | 🟠 Moderate | $250,000 | $850,000 | $550,000 |
| RSK-016 | SOC 2 certification failure | 🔴 High | $500,000 | $1,500,000 | $1,000,000 |
| RSK-017 | GDPR violation | 🔴 High | $200,000 | $2,000,000 | $1,100,000 |
| **TOTAL** | **All quantified risks** | | **$2,335,000** | **$9,590,000** | **$5,962,500** |

> **Note:** ALE figures represent annualised probable loss ranges based on FAIR methodology. They are not predictions but probabilistic estimates informed by threat frequency, control effectiveness, and industry loss data. They should be used to prioritise investment decisions, not as precise forecasts.

### 3.2 FAIR Loss Decomposition — Top 3 Risks

**RSK-001 Ransomware — $775K Mid ALE**
- TEF: 2 events/year (industry average for fintech sector)
- Vulnerability: 35% (GuardDuty + EDR reduce but do not eliminate)
- LEF: 0.7 events/year
- Primary Loss: $180K (IR, recovery, notification)
- Secondary Loss: $930K (regulatory fines, legal, reputational, client churn)
- Loss Magnitude: $1,110K per event

**RSK-017 GDPR — $1,100K Mid ALE**
- TEF: 1.5 incidents/year (GDPR enforcement is active in financial services)
- Vulnerability: 45% (no ROPA, no DSR process = high exposure)
- LEF: 0.675 incidents/year
- Primary Loss: $120K (legal response, notification, remediation)
- Secondary Loss: $1,508K (regulatory fine up to 4% global revenue + litigation)
- Loss Magnitude: $1,628K per event

**RSK-016 SOC 2 Failure — $1,000K Mid ALE**
- This risk is unique — loss is primarily commercial, not incident-driven
- Each quarter of delay costs an estimated $125K in deferred enterprise ARR
- Full certification failure would cost $500K–$1.5M in lost pipeline within 12 months
- Treatment is programme execution, not a technical control

---

## 4. Risk Treatment Progress

### 4.1 Treatment Decision Summary

| Treatment | Count | % | Rationale |
|---|---|---|---|
| **Mitigate** | 21 | 84% | Primary response — implement or strengthen controls |
| **Transfer / Mitigate** | 1 | 4% | RSK-011 AWS concentration — cyber insurance + DR strategy |
| **Accept / Mitigate** | 1 | 4% | RSK-020 SLA breach — buffer SLAs + monitor |
| **Transfer** | 0 | 0% | No risks currently treated by transfer alone |
| **Accept** | 2 | 8% | RSK-023 key person risk (mitigated by documentation programme); RSK-015 SendGrid (low residual) |

### 4.2 Treatment Timeline

| Horizon | Risks | Focus Area |
|---|---|---|
| **Q1 2026 (Immediate)** | RSK-003, RSK-006, RSK-009, RSK-015 | API scanning, S3 posture, secrets mgmt, DMARC |
| **Q2 2026 (30–60 days)** | RSK-001, RSK-002, RSK-005, RSK-008, RSK-012, RSK-013, RSK-017 | Ransomware controls, phishing-resistant MFA, supply chain, IAM, GDPR |
| **Q3 2026 (60–90 days)** | RSK-004, RSK-016, RSK-018, RSK-019 | DLP/UEBA, SOC 2 audit engagement, PCI-DSS, CCPA |
| **Q4 2026 (Ongoing)** | RSK-007, RSK-011, RSK-020, RSK-023 | DR strategy, vendor concentration, SLA management, key person |

---

## 5. Risk Programme Observations

### What Is Working
The foundational security controls deployed at ResolvX - Okta SSO with MFA, AWS GuardDuty, EDR on all endpoints, GitHub branch protection, multi-AZ architecture, and Jamf MDM - are collectively reducing inherent risk scores meaningfully. No risks remain at Critical residual level. This is a strong foundation for a company at this stage.

### Where the Programme Must Focus
Three themes dominate the residual risk profile:

**1. Detection & Response Gap** : The absence of a SIEM, formalised IR Plan, and comprehensive alerting rules means that even well-protected systems have limited detection capability. An attacker who bypasses perimeter controls could operate undetected. SIEM deployment and IR Plan development (Phase 4) are the highest-leverage investments on the roadmap.

**2. Cloud Posture Discipline** : AWS misconfiguration (RSK-006), IAM over-privilege (RSK-008), and secrets management gaps (RSK-009) represent a cluster of addressable risks that stem from the same root cause: fast-moving engineering without fully mature DevSecOps controls. IaC enforcement and a cloud security posture management (CSPM) programme address all three.

**3. Compliance Programme Execution** : RSK-016 (SOC 2 failure) carries the highest single commercial risk in the portfolio. It is not a technical risk — it is a programme execution risk. Every week of delay on policy development (Phase 3), evidence collection (Phase 5), and auditor engagement reduces the probability of Q4 2026 certification. This risk is owned directly by the GRC Lead and CISO.

### Risk Appetite Alignment
ResolvX's stated risk appetite (Low for cybersecurity, Very Low for compliance) is consistent with the residual risk profile. The 8 High residual risks all have documented treatment plans with named owners and target dates. No risks are sitting unattended above the accepted tolerance threshold. The programme is operating within its own risk framework.

---

## 6. Recommended Board-Level Actions

The following three actions are recommended for leadership consideration:

**1. Approve security budget allocation for SIEM and CSPM tooling (Q1 2026)**
The detection gap is the most significant unmitigated risk cluster. AWS Security Hub + a SIEM solution (estimated $40K–$80K annually) would close RSK-010, RSK-007 (partial), and significantly reduce DE function gaps identified in the NIST CSF 2.0 mapping.

**2. Formally engage a SOC 2 auditor by Q3 2026**
RSK-016 requires a firm external commitment. Engaging an auditor creates a fixed deadline that drives Phase 3–5 execution and signals to enterprise clients that certification is on a defined timeline. Recommended auditors for SaaS fintech: Drata/Vanta-partnered firms, A-LIGN, Schellman.

**3. Initiate GDPR data mapping and DSR programme (Q2 2026)**
GDPR carries the highest potential ALE in the portfolio ($200K–$2M). With ResolvX processing EU financial data, the exposure is material. A focused 6-week GDPR remediation sprint (ROPA + DSR process + DPA review) would significantly reduce RSK-017 residual score and demonstrate regulatory maturity to European financial institution clients.

---

## 7. Document Control

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0 | 2026 | Derick G. Dmello : GRC Lead | Initial risk summary report — Phase 2 baseline assessment |

---

*ResolvX GRC Programme — Confidential — For Internal Distribution and Authorised External Reviewers Only — v1.0 — 2026*
*Methodology: NIST SP 800-30 Rev. 1 (Qualitative) | FAIR (Quantitative) | ISO/IEC 27001:2022*
