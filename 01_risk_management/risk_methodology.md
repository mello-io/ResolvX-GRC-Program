# ⚖️ ResolvX — Risk Assessment Methodology

> **Program:** GRC Compliance & Audit Readiness | **Phase:** 2 — Risk & Controls | **Version:** 1.0

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Phase](https://img.shields.io/badge/Phase-2%20Risk%20%26%20Controls-purple?style=flat-square)
![Standard](https://img.shields.io/badge/Standard-NIST%20SP%20800--30%20%7C%20ISO%2027001%20%7C%20FAIR-blue?style=flat-square)
![Classification](https://img.shields.io/badge/Classification-Internal-yellow?style=flat-square)
![Owner](https://img.shields.io/badge/Owner-GRC%20Lead-lightgrey?style=flat-square)

---

## Purpose

This document defines how ResolvX identifies, analyzes, evaluates, and treats information security risks. It establishes the rules of the game; before any risk is scored, this methodology defines what the scores mean, how they are derived, and what happens as a result.

A consistent, repeatable methodology ensures that risk assessments remain comparable over time, defensible to auditors, and actionable for the business.

---

## Governing Standards

| Standard | Role in This Methodology |
|---|---|
| **NIST SP 800-30 Rev. 1** | Core risk assessment process - threat identification, likelihood and impact scales, risk determination |
| **ISO/IEC 27001:2022** | ISMS risk management requirements - Clause 6.1.2 (risk assessment), Clause 6.1.3 (risk treatment) |
| **ISO 31000:2018** | Risk management principles and framework |
| **FAIR (Factor Analysis of Information Risk)** | Quantitative model for top-tier risks - produces probable financial loss ranges |

---

## Risk Assessment Process

ResolvX follows the four-step risk assessment lifecycle defined in NIST SP 800-30:

```
PREPARE → CONDUCT → COMMUNICATE → MAINTAIN
```

| Step | Activities |
|---|---|
| **1. Prepare** | Define scope, identify assets, establish threat sources, select methodology |
| **2. Conduct** | Identify threats & vulnerabilities, determine likelihood & impact, calculate risk score |
| **3. Communicate** | Produce risk register, brief stakeholders, escalate high/critical risks |
| **4. Maintain** | Review register quarterly, update on material changes, track treatment status |

---

## Model 1 - Qualitative: 5×5 Risk Matrix

Used for **all risks** in the risk register. Produces a risk score from 1 – 25 that maps to a risk level.

### Likelihood Scale
*(Source: NIST SP 800-30 Rev. 1, Appendix G)*

| Score | Level | Adversarial Definition | Non-Adversarial Definition |
|---|---|---|---|
| **5** | Very High | Adversary is almost certain to initiate the threat event | Occurs more than 100 times per year |
| **4** | High | Adversary is highly likely to initiate the threat event | Occurs between 10–100 times per year |
| **3** | Moderate | Adversary is somewhat likely to initiate the threat event | Occurs between 1–10 times per year |
| **2** | Low | Adversary is unlikely to initiate the threat event | Occurs less than once per year |
| **1** | Very Low | Adversary is highly unlikely to initiate the threat event | Occurs less than once every 10 years |

### Impact Scale
*(Source: NIST SP 800-30 Rev. 1, Appendix H — tailored for ResolvX)*

| Score | Level | Definition | ResolvX Examples |
|---|---|---|---|
| **5** | Very High | Catastrophic damage : existential threat to operations | Mass PII breach, complete platform outage, loss of SOC 2 certification |
| **4** | High | Severe damage : major disruption to operations or reputation | Significant data loss, regulatory fine >$500K, major client churn |
| **3** | Moderate | Significant damage : notable disruption but recoverable | Partial data exposure, service degradation, audit finding |
| **2** | Low | Minor damage : limited operational or reputational impact | Single user account compromise, minor SLA breach |
| **1** | Very Low | Negligible : minimal impact, fully recoverable | Policy violation with no data exposure |

### Risk Score Matrix

> **Risk Score = Likelihood × Impact**

|  | **Impact 1** | **Impact 2** | **Impact 3** | **Impact 4** | **Impact 5** |
|---|---|---|---|---|---|
| **Likelihood 5** | 5 🟡 | 10 🟠 | 15 🔴 | 20 🔴 | 25 🔴 |
| **Likelihood 4** | 4 🟢 | 8 🟡 | 12 🟠 | 16 🔴 | 20 🔴 |
| **Likelihood 3** | 3 🟢 | 6 🟡 | 9 🟡 | 12 🟠 | 15 🔴 |
| **Likelihood 2** | 2 🟢 | 4 🟢 | 6 🟡 | 8 🟡 | 10 🟠 |
| **Likelihood 1** | 1 🟢 | 2 🟢 | 3 🟢 | 4 🟢 | 5 🟡 |

### Risk Level Thresholds

| Score Range | Risk Level | Action Required |
|---|---|---|
| 20–25 | 🔴 **Critical** | Immediate escalation to CISO. Treatment plan within 72 hours. |
| 12–19 | 🔴 **High** | Escalate to GRC Lead. Treatment plan within 30 days. |
| 7–11 | 🟠 **Moderate** | Assigned to control owner. Treatment plan within 90 days. |
| 4–6 | 🟡 **Low** | Monitor and review quarterly. Accept or treat at discretion. |
| 1–3 | 🟢 **Very Low** | Accept risk. Document rationale. Review annually. |

---

## Model 2 — Quantitative: FAIR Analysis

Used for **Critical and High risks** identified through the 5×5 model. FAIR (Factor Analysis of Information Risk) produces a **probable financial loss range**. Translating risk into language that executives and boards understand.

### FAIR Model Structure

```
RISK = Loss Event Frequency (LEF) × Loss Magnitude (LM)
         │                                    │
         ├─ Threat Event Frequency (TEF)      ├─ Primary Loss
         └─ Vulnerability (Vuln)              └─ Secondary Loss
                                                  ├─ Regulatory fines
                                                  ├─ Legal liability
                                                  ├─ Reputational damage
                                                  └─ Response costs
```

### FAIR Key Terms

| Term | Definition |
|---|---|
| **Threat Event Frequency (TEF)** | How often a threat agent acts against an asset (per year) |
| **Vulnerability (Vuln)** | Probability that a threat event results in a loss event (0–100%) |
| **Loss Event Frequency (LEF)** | TEF × Vulnerability — how often a loss actually occurs |
| **Primary Loss** | Direct financial impact — incident response, recovery, data restoration |
| **Secondary Loss** | Downstream impact — fines, litigation, reputational loss, client churn |
| **Loss Magnitude (LM)** | Primary Loss + Secondary Loss |
| **Risk (Annualized)** | LEF × LM — expressed as annualized loss expectancy (ALE) in $ |

### FAIR Loss Categories for ResolvX

| Loss Category | Examples at ResolvX | Estimation Basis |
|---|---|---|
| **Productivity Loss** | Engineering hours diverted to incident response | Fully loaded hourly rate × hours |
| **Response Costs** | Forensics, legal counsel, breach notification | Vendor contracts + legal rates |
| **Replacement Costs** | Data recovery, system rebuild | Cloud spend + labor |
| **Regulatory Fines** | NYDFS, CCPA, GDPR penalties | Published fine schedules |
| **Legal Liability** | Client lawsuits, contractual penalties | Contract terms + litigation estimates |
| **Reputational Loss** | Client churn, delayed sales cycles | ARR × churn rate estimates |

### When FAIR Analysis Is Applied

FAIR is triggered for any risk scoring **12 or above** (High or Critical) in the 5×5 model. The output is documented in the risk register under the **"FAIR ALE ($)"** column and expanded in the Risk Summary Report.

---

## Risk Appetite & Tolerance

| Category | Appetite Statement |
|---|---|
| **Cybersecurity** | Low — ResolvX maintains a low tolerance for risks that could result in client data exposure or platform unavailability |
| **Compliance** | Very Low — Zero tolerance for regulatory violations that could revoke our right to operate |
| **Vendor Risk** | Moderate — Acceptable where compensating controls exist and vendor SOC 2 reports are available |
| **Operational** | Moderate — Acceptable for non-critical internal processes with defined recovery procedures |
| **Reputational** | Very Low — ResolvX's value proposition is trust; reputational risk is treated as critical |

### Risk Tolerance Thresholds

| Risk Level | Tolerance |
|---|---|
| 🔴 Critical (20–25) | **Zero tolerance** — must be treated immediately |
| 🔴 High (12–19) | **Low tolerance** — treatment required within 30 days |
| 🟠 Moderate (7–11) | **Moderate tolerance** — treatment planned within 90 days |
| 🟡 Low (4–6) | **Acceptable** — monitor and treat at discretion |
| 🟢 Very Low (1–3) | **Accepted** — documented and reviewed annually |

---

## Risk Treatment Options

For each identified risk, one of four treatment decisions is made:

| Treatment | Definition | When Used |
|---|---|---|
| **Mitigate** | Implement controls to reduce likelihood or impact | Primary response for High and Critical risks |
| **Transfer** | Shift risk to a third party (cyber insurance, contractual liability) | Where financial exposure is the primary concern |
| **Accept** | Formally acknowledge and accept the risk | Low/Very Low risks or where treatment cost exceeds risk cost |
| **Avoid** | Eliminate the activity or asset generating the risk | Where risk cannot be reduced to acceptable levels |

---

## Risk Register Fields

Every risk in the ResolvX risk register captures the following:

| Field | Description |
|---|---|
| **Risk ID** | Unique identifier (e.g., RSK-001) |
| **Category** | Cyber / Cloud & Infrastructure / Vendor / Compliance |
| **Risk Description** | Clear statement of the risk scenario |
| **Threat Source** | Who or what initiates the threat |
| **Affected Assets** | Systems, data, or processes impacted |
| **Inherent Likelihood** | Score 1–5 (before controls) |
| **Inherent Impact** | Score 1–5 (before controls) |
| **Inherent Risk Score** | Likelihood × Impact |
| **Current Controls** | Controls already in place |
| **Residual Likelihood** | Score 1–5 (after controls) |
| **Residual Impact** | Score 1–5 (after controls) |
| **Residual Risk Score** | Post-control risk level |
| **Risk Level** | Very Low / Low / Moderate / High / Critical |
| **FAIR ALE ($)** | Annualized loss expectancy for High/Critical risks |
| **Treatment Decision** | Mitigate / Transfer / Accept / Avoid |
| **Treatment Actions** | Specific remediation steps |
| **Control Owner** | Responsible party |
| **Target Date** | Remediation deadline |
| **Status** | Open / In Progress / Closed |
| **ISO 27001 Ref** | Relevant Annex A control(s) |
| **SOC 2 TSC Ref** | Relevant Trust Services Criteria |

---

## Review & Maintenance Cycle

| Trigger | Action |
|---|---|
| **Quarterly** | Full risk register review — update scores, treatment status, and control effectiveness |
| **Material change** | New system, vendor, regulation, or product feature — assess new risks within 30 days |
| **Post-incident** | Re-assess affected risks following any security incident |
| **Pre-audit** | Full refresh before any SOC 2 or ISO 27001 audit engagement |
| **Annual** | Comprehensive reassessment — review risk appetite, methodology, and threat landscape |

---

## Formal Artifact

> 📄 **[Download Full Risk Methodology (.pdf)](./formal_artifact/risk_methodology.pdf)**
> *Formal version with complete scoring tables, approval signatures, and document control history.*

---

*ResolvX GRC Program — Internal Use Only — v1.0 — 2026*
