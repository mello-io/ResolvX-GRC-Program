# 🔍 ResolvX — Information Security Gap Analysis Report

> **Program:** GRC Compliance & Audit Readiness | **Phase:** 2 — Risk & Controls | **Version:** 1.0

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Phase](https://img.shields.io/badge/Phase-2%20Risk%20%26%20Controls-purple?style=flat-square)
![Frameworks](https://img.shields.io/badge/Frameworks-ISO%2027001%20%7C%20SOC%202%20%7C%20NIST%20CSF%202.0-blue?style=flat-square)
![Classification](https://img.shields.io/badge/Classification-Confidential-red?style=flat-square)

---

## Executive Summary

This Gap Analysis Report synthesises findings across all three framework mappings completed in Phase 2 of the ResolvX GRC Programme - ISO/IEC 27001:2022, SOC 2 Trust Services Criteria, and NIST CSF 2.0. It identifies where control gaps exist, quantifies the gaps by domain and severity, and produces the prioritised remediation roadmap that will drive Phases 3 through 5.

### Aggregate Gap Picture

| Framework | Total Controls / Criteria | Implemented | Partial | Not Done | Gap % |
|---|---|---|---|---|---|
| **ISO 27001:2022 Annex A** | 93 controls | 15 (16%) | 48 (52%) | 30 (32%) | **84%** need work |
| **SOC 2 TSC (Security + Availability + Privacy)** | 44 criteria | 6 (14%) | 25 (57%) | 13 (30%) | **87%** need work |
| **NIST CSF 2.0** | 103 subcategories | 20 (19%) | 39 (38%) | 44 (43%) | **81%** need work |

> **Note:** "Need work" includes both Partial (evidence gaps) and Not Done (not yet implemented). The high percentages reflect the reality of a programme at baseline — not a failing programme, but a programme that has correctly documented where it stands. A mature programme with inflated "Implemented" counts would be far more dangerous.

### The Three Critical Gap Clusters

Across all three frameworks, the same three control domains surface as critical gaps regardless of which lens is applied:

1. **Detection & Response** — No SIEM, no formalised IR Plan, incomplete alerting coverage
2. **Policy & Governance** — Policy suite not yet published; GOVERN framework requirements unmet
3. **Privacy & Compliance** — ROPA, DSR, and GDPR data mapping not completed

These three clusters account for the majority of Critical and High priority gaps across all frameworks and directly underpin the top commercial risk (SOC 2 certification) and top regulatory risk (GDPR enforcement).

---

## 1. ISO 27001:2022 Gap Analysis

### 1.1 Gap Summary by Domain

| Domain | Controls | Implemented | Partial | Not Done | Completion % |
|---|---|---|---|---|---|
| **5 Organizational** | 37 | 6 | 19 | 12 | 16% |
| **6 People** | 8 | 2 | 5 | 1 | 25% |
| **7 Physical** | 14 | 5 | 7 | 2 | 36% |
| **8 Technological** | 34 | 2 | 17 | 15 | 6% |
| **Total** | **93** | **15** | **48** | **30** | **16%** |

The **Technological domain (8)** has the lowest completion rate at 6% fully implemented, reflecting that while foundational technology controls exist, they are not yet fully documented or evidenced to audit standard. Physical (7) scores highest because ResolvX's cloud-native architecture means most physical controls are inherited from AWS.

### 1.2 Critical ISO 27001 Gaps

The following controls are rated Critical priority and have Not Started or Planned status:

| Control ID | Control Name | Gap | Risk Impact |
|---|---|---|---|
| **5.1** | Policies for information security | Policy suite not published | SOC 2 failure, audit rejection |
| **5.18** | Access rights | No quarterly access review | RSK-004, RSK-022 |
| **5.19** | Information security in supplier relationships | No TPRM programme | RSK-011–RSK-015 |
| **5.24** | Incident management planning | No IR Plan | RSK-001–RSK-005 |
| **5.26** | Response to incidents | No IR runbooks | RSK-001–RSK-005 |
| **5.34** | Privacy and protection of PII | No ROPA, no DSR process | RSK-017, RSK-019 |
| **8.2** | Privileged access rights | No formal PAM programme | RSK-008 |
| **8.3** | Information access restriction | No formal access control policy | RSK-004, RSK-008 |
| **8.13** | Information backup | Backup restoration not tested | RSK-001, RSK-007 |
| **8.15** | Logging | Application logging incomplete | RSK-010 |
| **8.16** | Monitoring activities | SIEM not deployed | RSK-010 |

### 1.3 ISO 27001 Remediation Priority

**Immediate (Q1 2026):** 5.1 (IS Policy), 8.15/8.16 (Logging/SIEM), 8.8 (Vulnerability management formalisation)

**Short-term (Q2 2026):** 5.18/5.19 (Access rights + TPRM), 8.2/8.3 (PAM + Access control policy), 5.34 (Privacy/ROPA)

**Medium-term (Q3 2026):** 5.24/5.26 (IR Plan + runbooks), 8.13 (Backup testing), 5.35 (Internal audit programme)

---

## 2. SOC 2 Trust Services Criteria Gap Analysis

### 2.1 Gap Summary by TSC Category

| TSC | Category | Criteria | Implemented | Partial | Not Done | Status |
|---|---|---|---|---|---|---|
| **CC1** | Control Environment | 5 | 1 | 4 | 0 | 🟠 Partial |
| **CC2** | Communication & Information | 3 | 0 | 2 | 1 | 🟠 Partial |
| **CC3** | Risk Assessment | 4 | 3 | 1 | 0 | 🟢 Strong |
| **CC4** | Monitoring Activities | 2 | 0 | 0 | 2 | 🔴 Gap |
| **CC5** | Control Activities | 3 | 0 | 1 | 2 | 🔴 Gap |
| **CC6** | Logical & Physical Access | 8 | 3 | 5 | 0 | 🟠 Partial |
| **CC7** | System Operations | 5 | 0 | 1 | 4 | 🔴 Gap |
| **CC8** | Change Management | 1 | 0 | 1 | 0 | 🟠 Partial |
| **CC9** | Risk Mitigation | 2 | 0 | 1 | 1 | 🟠 Partial |
| **A1** | Availability | 3 | 1 | 2 | 0 | 🟠 Partial |
| **P** | Privacy | 8 | 0 | 2 | 6 | 🔴 Gap |
| **Total** | | **44** | **6** | **25** | **13** | |

### 2.2 SOC 2 Audit Readiness Assessment

**CC3 Risk Assessment — Strongest Category**
ResolvX's Phase 2 risk assessment work (Risk Methodology, Risk Register, Threat Landscape) satisfies CC3.1, CC3.2, CC3.3, and CC3.4 at a level that would withstand Type II audit scrutiny. This is the programme's most mature domain and demonstrates that risk management has been taken seriously from day one.

**CC6 Logical & Physical Access — Foundational but Incomplete**
Okta SSO with MFA, AWS IAM RBAC, and EDR give ResolvX the core technical controls for CC6. The gap is documentation and process formalisation — Access Control Policy, quarterly access reviews, and formal deprovisioning SLA. These are Phase 3 deliverables.

**CC4, CC5, CC7 — The SOC 2 Audit Blockers**
These three categories are the most likely reasons a SOC 2 Type II audit would be qualified or delayed if initiated today:

- **CC4 Monitoring** — No internal audit programme, no formalised deficiency tracking
- **CC5 Control Activities** — Policy suite not published; technology controls not baseline-documented
- **CC7 System Operations** — No SIEM, no event triage process, no IR Plan; this category alone has 4 Not Started criteria

**Privacy (P) — Highest Risk Category for Enterprise Client Pipeline**
With 6 of 8 Privacy criteria Not Started, ResolvX has significant exposure to enterprise clients operating in regulated industries who will ask for evidence of privacy programme maturity. The entire P category is a Phase 3 priority.

### 2.3 Critical SOC 2 Gaps

| TSC ID | Criterion | Gap | Phase to Close |
|---|---|---|---|
| **CC4.1** | Ongoing evaluations | No internal audit programme | Phase 5 |
| **CC5.3** | Policy deployment | Policy suite not published | Phase 3 |
| **CC7.3** | Event evaluation | No event triage process | Phase 4 |
| **CC7.4** | Incident response | No IR Plan or runbooks | Phase 4 |
| **CC9.1** | Vendor risk programme | No TPRM programme | Phase 3 |
| **P1.1–P8.1** | Privacy (all criteria) | No ROPA, no DSR, no consent mgmt | Phase 3 |

---

## 3. NIST CSF 2.0 Gap Analysis

### 3.1 Gap Summary by Function

| Function | Subcategories | Implemented | Partial | Planned | Completion % |
|---|---|---|---|---|---|
| **GV — Govern** | 31 | 8 | 10 | 13 | 26% |
| **ID — Identify** | 18 | 7 | 6 | 5 | 39% |
| **PR — Protect** | 22 | 9 | 10 | 3 | 41% |
| **DE — Detect** | 11 | 1 | 6 | 4 | 9% |
| **RS — Respond** | 13 | 0 | 2 | 11 | 0% |
| **RC — Recover** | 8 | 0 | 3 | 5 | 0% |
| **Total** | **103** | **25** | **37** | **41** | **24%** |

### 3.2 Function-Level Analysis

**GV — Govern (26% complete)**
As the new function introduced in CSF 2.0, GOVERN represents the most forward-thinking component of the framework. ResolvX's Phase 1 work (Stakeholder Register, Objectives & Scope, Risk Methodology) satisfies GV.OC, GV.RR, and GV.RM at a level that few organisations can claim at programme inception. The primary GOVERN gaps are GV.PO (policy — Phase 3), GV.OV (oversight/internal audit — Phase 5), and GV.SC (supply chain risk programme — Phase 3).

**ID — Identify (39% complete)**
The strongest performing function relative to programme maturity. Risk assessment (ID.RA), asset management (ID.AM), and threat intelligence (ID.RA) are substantially covered through Phase 1 and 2 deliverables. Primary gap is ID.AM-07 (ROPA/data inventory for GDPR) and ID.IM (improvement process — Phase 5).

**PR — Protect (41% complete)**
The highest completion rate across all functions. MFA (PR.AA-03), encryption at rest and in transit (PR.DS-01/02), and environment separation (PR.PS) are fully implemented. Primary gaps are PR.AA-05 (formal access control policy), PR.AT (role-based training programme), and PR.DS-11 (backup restoration testing).

**DE — Detect (9% complete) — Critical Gap**
This is the most significant function-level gap in the programme. Only 1 of 11 subcategories is fully implemented. The absence of SIEM (DE.AE-03), formal event analysis (DE.AE-02), and incident declaration criteria (DE.AE-08) means ResolvX has limited ability to detect an attack that bypasses preventive controls. SIEM deployment is the single highest-leverage security investment in the roadmap.

**RS — Respond (0% complete) — Phase 4 Priority**
Zero subcategories fully implemented. The entire Respond function is Phase 4 work — IR Plan, runbooks (ransomware, phishing, data breach), tabletop exercises, and regulatory notification procedures. This is expected and planned, not a surprise finding.

**RC — Recover (0% complete) — Phase 4 Priority**
Same position as RS. BCP, DR plan, backup restoration testing, and recovery communication procedures are all Phase 4 deliverables. Technical recovery capability (multi-AZ, RDS backups) exists but is not yet formalised or tested.

### 3.3 NIST CSF 2.0 Target Profile

ResolvX's current profile is a **Tier 1 (Partial)** organisation moving toward **Tier 2 (Risk-Informed)**. The target upon completion of Phases 3–5 is **Tier 3 (Repeatable)** — documented, consistently applied, and regularly reviewed cybersecurity practices.

| Tier | Description | ResolvX Status |
|---|---|---|
| Tier 1 — Partial | Ad hoc, reactive practices | ← Current (Phases 1–2 complete) |
| Tier 2 — Risk-Informed | Risk-aware but not organisation-wide | ← Target by Phase 3 completion |
| Tier 3 — Repeatable | Defined, consistently applied, reviewed | ← Target by Phase 5 completion |
| Tier 4 — Adaptive | Continuously improving, threat-informed | Future — Phase 6+ / CCF programme |

---

## 4. Cross-Framework Gap Synthesis

### 4.1 The Control Gap Intersection

The following gaps are flagged as Critical by all three frameworks simultaneously. These represent the highest-priority remediation items in the programme because they drive risk exposure, audit failure risk, and compliance penalties at the same time.

| Gap Domain | ISO 27001 | SOC 2 TSC | NIST CSF 2.0 | Business Impact |
|---|---|---|---|---|
| **Information Security Policy Suite** | 5.1 Not Started | CC5.3 Not Started | GV.PO-01 Planned | SOC 2 audit blocker; no governance foundation |
| **SIEM / Monitoring** | 8.15, 8.16 Partial | CC7.1 Partial | DE.CM-01, DE.AE-03 Planned | Breach detection gap; dwell time risk |
| **Incident Response Plan** | 5.24, 5.26 Planned | CC7.3, CC7.4 Planned | RS.MA-01, RS.MI-01 Planned | No coordinated response to security events |
| **TPRM Programme** | 5.19 Planned | CC9.1 Planned | GV.SC-01, GV.SC-04 Planned | Vendor risk uncontrolled; SOC 2 CC9 gap |
| **Privacy Programme** | 5.34 Partial | P1–P8 Not Started | ID.AM-07 Planned | GDPR/CCPA enforcement risk; enterprise client friction |
| **Access Reviews (Quarterly)** | 5.18 Planned | CC6.3 Partial | PR.AA-05 Partial | Lateral movement risk; SOC 2 CC6 gap |
| **Internal Audit Programme** | 5.35 Planned | CC4.1 Planned | GV.OV-01 Planned | No independent assurance; SOC 2 CC4 gap |
| **Backup Testing** | 8.13 Partial | A1.2 Partial | PR.DS-11, RC.RP-03 Planned | Untested recovery = unknown RTO/RPO |

### 4.2 Gap Severity Matrix

| Priority | Count (Cross-Framework) | Phase to Close | Estimated Effort |
|---|---|---|---|
| **Critical** | 8 gap domains | Phase 3–4 | High — policy, tooling, process |
| **High** | 14 gap domains | Phase 3–5 | Medium — process formalisation |
| **Medium** | 11 gap domains | Phase 4–6 | Low-Medium — documentation |
| **Low** | 7 gap domains | Phase 6 | Low — monitoring and review |

---

## 5. Prioritised Remediation Roadmap

### Phase 3 — Policy & Vendor Framework (Target: Q2 2026)

Phase 3 addresses the governance and policy foundation that is required before evidence collection can begin for SOC 2. Without policies, there is nothing to audit against.

| Deliverable | Frameworks Addressed | Gap Domains Closed |
|---|---|---|
| Information Security Policy | ISO 5.1, SOC 2 CC5.3, NIST GV.PO | Governance foundation |
| Acceptable Use Policy | ISO 5.10, SOC 2 CC1.2, NIST GV.PO | User conduct framework |
| Access Control Policy | ISO 5.15/5.18, SOC 2 CC6.1, NIST PR.AA | Access review cadence |
| Data Classification Policy | ISO 5.12/5.13, SOC 2 CC6.1, NIST PR.DS | Data handling framework |
| Vendor Management Policy + TPRM | ISO 5.19, SOC 2 CC9.1, NIST GV.SC | Vendor risk programme |
| Privacy Programme (ROPA + DSR) | ISO 5.34, SOC 2 P1–P8, NIST ID.AM-07 | GDPR/CCPA compliance |

### Phase 4 — Incident Response & Detection (Target: Q3 2026)

Phase 4 closes the DE, RS, and RC function gaps in NIST CSF and the CC7 cluster in SOC 2.

| Deliverable | Frameworks Addressed | Gap Domains Closed |
|---|---|---|
| SIEM Deployment | ISO 8.15/8.16, SOC 2 CC7.1, NIST DE.CM | Detection gap |
| Incident Response Plan | ISO 5.24/5.26, SOC 2 CC7.3/CC7.4, NIST RS | Response framework |
| IR Runbooks (x3) | ISO 5.26, SOC 2 CC7.4, NIST RS.MA/RS.MI | Playbooks for top threats |
| Tabletop Exercise | ISO 5.27, SOC 2 CC7.5, NIST ID.IM | Tested response capability |
| BCP & DR Plan | ISO 5.29/5.30, SOC 2 A1.2, NIST RC | Recovery framework |
| Backup Restoration Test | ISO 8.13, SOC 2 A1.2, NIST RC.RP-03 | Verified RTO/RPO |

### Phase 5 — Audit Readiness & Evidence Collection (Target: Q4 2026)

Phase 5 converts completed controls into audit-ready evidence and closes monitoring/oversight gaps.

| Deliverable | Frameworks Addressed | Gap Domains Closed |
|---|---|---|
| Internal Audit Programme | ISO 5.35, SOC 2 CC4.1, NIST GV.OV | Independent assurance |
| Evidence Collection & Mapping | All three frameworks | SOC 2 Type II evidence package |
| Corrective Action Plan (CAP) | ISO 5.36, SOC 2 CC4.2, NIST ID.IM | Deficiency remediation |
| SOC 2 Readiness Assessment | SOC 2 all TSC | Pre-audit gap confirmation |
| Auditor Engagement | SOC 2 Type II | Certification pathway |

---

## 6. Gap Analysis Observations

### What This Analysis Reveals About the Programme

The gap percentages across all three frameworks — 84%, 87%, and 81% respectively — look alarming at first glance. They are not. They are the expected and honest profile of a programme completing its first formal baseline assessment. A programme that reported 60–70% implemented at this stage would either have inflated its ratings or would have been running an undocumented programme for years.

What the numbers actually tell us is more important than their face value:

**The 16% implemented across ISO 27001 represents the controls ResolvX already had in place before this programme began.** Okta MFA, MDM, EDR, environment separation, NDA programme, and background screening — these are not trivial. Many organisations beginning an ISO 27001 programme start with far less.

**The 52–57% partial across all frameworks is the most valuable data point.** It means ResolvX is not starting from scratch — it is formalising, documenting, and evidencing controls that largely already exist in some form. The effort required is documentation and process, not wholesale control implementation.

**The 30–43% Not Done is the programme roadmap.** Policy suite, IR Plan, SIEM, TPRM, and privacy programme — these are all Phases 3 and 4. They are planned, scoped, and owned.

### The Insight Across All Three Frameworks

One pattern emerges consistently regardless of which framework is applied: **ResolvX is technically ahead of where its documentation and processes suggest it is.** The controls are largely there. The evidence, policies, and formal processes are not. The programme's job from this point forward is to close that gap — to document what exists, test what's untested, and implement what's missing.

That is a programme in execution. That is the right position to be in at the end of Phase 2.

---

## 7. Document Control

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0 | 2026 | Derick G. Dmello — GRC Lead | Initial gap analysis — Phase 2 baseline across ISO 27001:2022, SOC 2 TSC, and NIST CSF 2.0 |

---

*ResolvX GRC Programme — Confidential — For Internal Distribution and Authorised External Reviewers Only — v1.0 — 2026*
*Frameworks: ISO/IEC 27001:2022 | AICPA SOC 2 Trust Services Criteria | NIST CSF 2.0 (February 2024)*
