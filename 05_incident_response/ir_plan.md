# 🚨 Incident Response Plan — ResolvX

> **IR-PLAN-001 · v1.1 · 2026-07-31 · Internal - Restricted**
> Owner: GRC Lead · Approver: CISO · Review: Annual + post every P1/P2

![NIST](https://img.shields.io/badge/NIST%20SP%20800--61%20Rev%202-Aligned-blue?style=flat-square)
![ISO](https://img.shields.io/badge/ISO%2027001%3A2022-A5.24–A5.28-blue?style=flat-square)
![SOC2](https://img.shields.io/badge/SOC%202-CC7.3%20CC7.4%20CC7.5-orange?style=flat-square)
![CSF](https://img.shields.io/badge/NIST%20CSF%202.0-RS%20Family-purple?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

---

## What This Plan Does

ResolvX is a fintech SaaS company processing financial dispute data for regulated institutions. A security incident here is not just a technical problem - it carries GDPR notification obligations, client SLA obligations, and reputational stakes with enterprise customers who trust us with their consumers' data.

This plan exists so that when something goes wrong, no one has to improvise. Every role knows what to do, every decision has a documented owner, and every regulatory clock is tracked from the moment we become aware.

---

## The Four Phases

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   PREPARATION  →  DETECTION & ANALYSIS  →  CONTAINMENT /        │
│                                            ERADICATION /        │
│         ↑              RECOVERY              ↑                  │
│         └──────  POST-INCIDENT ACTIVITY ─────┘                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```
<br>

| Phase | Key Output | NIST Ref |
|---|---|---|
| Preparation | IRT assembled; runbooks ready; backups tested; out-of-band comms live | s.3.1 |
| Detection & Analysis | Incident declared; severity assigned; scope determined | s.3.2 |
| Containment, Eradication & Recovery | Systems isolated; evidence preserved; clean restoration | s.3.3 |
| Post-Incident Activity | Lessons learned meeting; PIR filed; ISMS updated | s.3.4 |

---

## Severity Model

| Level | Label | One-Line Criteria | Response SLA |
|---|---|---|---|
| 🔴 P1 | Critical | Client data confirmed exfiltrated; ransomware in production; active attacker | **15 minutes** |
| 🟠 P2 | High | Suspected breach; malware contained; privileged account compromised | **1 hour** |
| 🟡 P3 | Medium | Single endpoint malware; phishing - no confirmed credential compromise | **4 hours** |
| 🟢 P4 | Low | Blocked phishing; failed brute force; alert requiring investigation | **Next business day** |

> Severity can be **escalated but never de-escalated** during an active incident.

---

## Incident Response Team

| Role | IRT Function |
|---|---|
| **GRC Lead** | Incident Commander - overall coordination, regulatory notifications, documentation |
| **Head of Cloud Ops** | Technical Lead - AWS containment, forensic preservation |
| **IT Admin** | Identity Response - Okta session revocation, Jamf endpoint isolation |
| **DevSecOps** | Application/Code Response - malware analysis, secrets rotation |
| **CISO** | Executive Escalation - P1/P2 notification, board/client communication authority |
| **Legal** | Regulatory - GDPR notification decisions, law enforcement liaison |
| **VP Engineering** | Recovery - service restoration prioritisation, engineering resources |
| **Head of HR** | Insider Incident Response - engaged for any incident suspected to involve personnel misconduct |

**P1 out-of-hours escalation path:**
```
#security-alerts (Slack auto-page) → GRC Lead (direct call) → [15 min no response] → CISO → CEO
```

**Out-of-band communication:** ResolvX maintains a Signal group as the default channel for security incident coordination, tested quarterly. Where an incident escalates into a declared BCP/DR activation, the Incident Commander explicitly hands off primary coordination to a separate phone bridge line — faster for infrastructure-level coordination than persistent chat. The switch is a decision, not an assumption.

---

## Regulatory Notification Obligations

> The 72-hour GDPR clock starts from the moment ResolvX becomes **aware of a probable breach** - not from confirmation.

| Obligation | Trigger | Deadline | Owner |
|---|---|---|---|
| GDPR - Irish DPC (Art. 33) | Personal data breach with risk to individuals | **72 hours** | GRC Lead + Legal |
| Data subject notification (Art. 34) | High risk to individuals' rights and freedoms | Without undue delay | Legal |
| Client notification (as data processor) | Breach affecting client data | Per DPA - typically 24-72 hrs | GRC Lead |
| Cyber insurer | P1/P2 incident | Per policy terms | GRC Lead |
| Law enforcement | Criminal activity suspected | Legal decision | Legal |

---

## Containment Quick Reference

| Incident Type | Immediate Action |
|---|---|
| Compromised account | Revoke all Okta sessions; disable account; rotate credentials |
| Malware on endpoint | Isolate via Jamf (do not power off); notify IT Admin |
| Ransomware | Isolate from network immediately; take EBS snapshots; do not terminate |
| Data exfiltration | Block destination IP/domain; revoke API keys; preserve network logs |
| Phishing campaign | Block sender domain; alert all staff; review for credential compromise |
| Compromised AWS account | Revoke IAM keys; isolate resources; notify Head of Cloud Ops |

---

## Evidence Handling

Per ISO A5.28 and NIST SP 800-61 s.3.3.2:

- Capture volatile data **before** any remediation - running processes, network connections, memory
- Take forensic disk images - not file system backups
- Every piece of evidence is labelled: incident ID, timestamp, collector, source system
- Chain of custody maintained throughout; Legal consulted before law enforcement sharing

**Retention:** P1/P2 - 3 years minimum · P3/P4 - 1 year minimum

---

## Recovery Time Objectives

| Severity | Critical Services RTO | Full Restoration RTO |
|---|---|---|
| P1 | 4 hours | 24 hours |
| P2 | 8 hours | 24 hours |
| P3 | - | 24 hours |
| P4 | - | 72 hours |

---

## Plan Testing Schedule

| Test Type | Frequency | Last Conducted | Next Due |
|---|---|---|---|
| Ransomware tabletop exercise | Annual | 2026-02-14 (Operation Locked Gate) | 2027-02 |
| DR/BCP failover tabletop exercise | Annual | 2026-07-30 (Operation Steady Ground) — 98% of Critical-tier RTO budget used | 2027-07 |
| Functional phishing drill | Annual | - | 2026-Q4 |
| Out-of-band contact list test | Quarterly | 2026-Q2 | 2026-Q3 |
| Backup restoration test | Quarterly | 2026-Q2 | 2026-Q3 |

---

## Templates & Appendices

Two appendices were added to the formal IR Plan to close gaps this showcase's original scope didn't cover:

- **Post-Incident Report Template** — the formal, leadership-facing write-up required for every P1/P2 within 5 business days of resolution (10 for P3). Distinct from the Incident Log, which is the raw working record during the incident itself.
- **Evidence/Chain-of-Custody Log** — the specific fields required by this plan's own Evidence Handling section (incident ID, date/time collected, collector, source system, hash). Exists as a template now; not yet exercised in a live incident or dedicated tabletop.

## Related Documents

| Document | Location |
|---|---|
| 📄 IR Plan (formal) | `05_incident_response/formal_artifact/IR-PLAN-001.pdf` |
| 🔴 Runbook - Phishing | `05_incident_response/ir_runbooks/runbook_phishing.md` |
| 🔴 Runbook - Ransomware | `05_incident_response/ir_runbooks/runbook_ransomware.md` |
| 🔴 Runbook - Data Breach | `05_incident_response/ir_runbooks/runbook_data_breach.md` |
| 📊 Ransomware Tabletop Report | `05_incident_response/tabletop_simulation_report.xlsx` |
| 📊 DR Failover Tabletop Report | `05_incident_response/dr_failover_tabletop_test_report.xlsx` |
| 📄 DR Failover Exercise Executive Summary | `05_incident_response/formal_artifact/DR_Failover_Exercise_Executive_Summary.pdf` |
| 📊 Security Monitoring Report | `05_incident_response/security_monitoring_report.xlsx` |
| 📋 Incident Log Template | `05_incident_response/incident_log_template.xlsx` |
| 🔒 Logging & Monitoring Policy | `03_policies_and_procedures/formal_artifact/pol-007_logging_monitoring_policy.pdf` |
| 🔒 BCP/DR Policy & Plan | `03_policies_and_procedures/formal_artifact/pol-008_bcp_dr_policy.pdf` |
| 🔒 Backup & Recovery Policy | `03_policies_and_procedures/formal_artifact/pol-009_backup_recovery_policy.pdf` |
| 🔒 Incident Management Policy | `03_policies_and_procedures/formal_artifact/pol-015_incident_management_policy.pdf` |
| 🔒 Breach Management Policy | `03_policies_and_procedures/formal_artifact/pol-016_breach_management_policy.pdf` |
| 🔒 Access Control Policy | `03_policies_and_procedures/formal_artifact/pol-003_access_control_policy.pdf` |
| 🔒 Privacy Programme | `03_policies_and_procedures/formal_artifact/pol-006_privacy_programme.pdf` |

---

*ResolvX GRC Program · Phase 4 - Incident Response · v1.1 · 2026-07-31*
