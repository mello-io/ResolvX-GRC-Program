# 👥 ResolvX: Stakeholder & Control Owner Register

> **Program:** GRC Compliance & Audit Readiness | **Phase:** 1 (Foundation) | **Version:** 1.1

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-blue?style=flat-square)
![Classification](https://img.shields.io/badge/Classification-Internal-yellow?style=flat-square)
![Owner](https://img.shields.io/badge/Owner-GRC%20Lead-lightgrey?style=flat-square)

---

## Purpose

Clear ownership is the backbone of a compliance program. Without it, controls go untested, evidence goes uncollected, and audits fail. This register defines every key stakeholder in the ResolvX GRC program, their responsibilities, and the control domains they are accountable for.

Every control in the ResolvX control matrix maps back to an owner defined here.

---

## RACI Model

| Role | Definition |
|---|---|
| **R: Responsible** | Does the work: implements or operates the control |
| **A: Accountable** | Owns the outcome: signs off, escalation point |
| **C: Consulted** | Provides input or expertise before decisions are made |
| **I: Informed** | Kept up to date on progress and outcomes |

---

## Program Stakeholder Register

| Role | Department | RACI | Primary Responsibilities |
|---|---|---|---|
| 🎯 **GRC Lead** *(Program Owner)* | GRC & Security | A / R | Program strategy, policy development, framework mapping, audit liaison, Trust Center ownership |
| 🛡️ **CISO** | GRC & Security | A | Executive sponsor, policy approvals, escalation authority, board reporting |
| ⚙️ **CTO** | Engineering | C / I | Technology risk decisions, architecture review, security engineering alignment |
| 🔧 **VP Engineering** | Engineering | R / C | Cloud security controls, DevSecOps implementation, infrastructure hardening |
| ☁️ **Head of Cloud Operations** | Engineering | R | AWS environment controls, patch management, logging, backup, access provisioning |
| 📦 **Head of Product** | Product | C / I | Product security requirements, privacy-by-design, feature compliance review |
| ⚖️ **General Counsel / Legal** | Legal | C / A | Regulatory compliance, DPAs, contract security clauses, GDPR/CCPA |
| 👤 **Head of HR** | HR & Operations | R / C | Personnel security, security awareness training, background checks, offboarding |
| 💰 **Head of Finance** | Finance | C / I | Financial data controls, vendor payment risk |
| 🤝 **Customer Success Lead** | Customer Success | I | Client trust communications, SOC 2 report sharing, security questionnaires |
| 🖥️ **IT Administrator** | GRC & Security | R | Endpoint management (Jamf), M365 admin, identity admin, MFA enforcement |
| 🔐 **DevSecOps Engineer** | Engineering | R | SAST/DAST tooling, secrets scanning, vulnerability management, CI/CD security |

---

## Control Domain Ownership

| Control Domain | ISO 27001 Ref | SOC 2 TSC | Primary Owner | Secondary |
|---|---|---|---|---|
| Information Security Policies | A.5 | CC1.1, CC1.2 | GRC Lead | CISO |
| Organization of Information Security | A.5 | CC1.3, CC1.4 | GRC Lead | CISO |
| Human Resource Security | A.6 | CC1.1, CC1.4 | Head of HR | GRC Lead |
| Asset Management | A.5 | CC6.1 | GRC Lead | Head of Cloud Ops |
| Access Control | A.5, A.8 | CC6.1–CC6.3 | IT Administrator | Head of Cloud Ops |
| Cryptography | A.8 | CC6.7 | Head of Cloud Ops | DevSecOps Engineer |
| Physical & Environmental Security | A.7 | CC6.4 | IT Admin | CISO |
| Operations Security | A.8 | CC7.1, CC7.2 | Head of Cloud Ops | DevSecOps Engineer |
| Communications Security | A.8 | CC6.6, CC6.7 | Head of Cloud Ops | IT Administrator |
| System Acquisition & Development | A.8 | CC8.1 | DevSecOps Engineer | VP Engineering |
| Supplier Relationships (TPRM) | A.5 | CC9.1, CC9.2 | GRC Lead | General Counsel |
| Incident Management | A.5, A.6 | CC7.3–CC7.5 | GRC Lead | Head of Cloud Ops |
| Business Continuity | A.5 | A1.1–A1.3 | VP Engineering | Head of Cloud Ops |
| Compliance & Audit | A.5 | CC4.1, CC4.2 | GRC Lead | CISO |
| Risk Management | A.5, A.8 | CC3.1–CC3.3 | GRC Lead | CISO |
| Change Management | A.8 | CC8.1 | VP Engineering | DevSecOps Engineer |
| Logging & Monitoring | A.8 | CC7.1, CC7.2 | Head of Cloud Ops | DevSecOps Engineer |
| Vulnerability Management | A.8 | CC7.1 | DevSecOps Engineer | Head of Cloud Ops |
| Data Privacy & Protection | A.5, A.8 | P1–P8 | General Counsel | GRC Lead |
| Security Awareness & Training | A.6 | CC1.4, CC2.2 | Head of HR | GRC Lead |

---

## Escalation Path

| Level | Trigger | Escalate To | Timeframe |
|---|---|---|---|
| 🟢 **Level 1: Operational** | Control deficiency identified during testing | GRC Lead | Within 5 business days |
| 🟡 **Level 2: Program** | High-severity gap or failed audit finding | CISO | Within 48 hours |
| 🔴 **Level 3: Executive** | Critical risk, breach, or regulatory notification | CTO / CEO / Legal | Immediately |
| ⚫ **Level 4: Board** | Material incident or significant compliance failure | Board of Directors | Within 72 hours of L3 |

---

## Formal Artifact

> 📄 **[Download Full Stakeholder Register (.pdf)](./formal_artifact/stakeholder_register.pdf)**
> *Formal version with complete RACI assignments, approval signatures, and document control.*

---

*ResolvX GRC Program, Internal Use Only, v1.1, 2026*
