# Runbook: Ransomware Incident Response

**Runbook ID:** IR-RB-002 | **Version:** 1.0 | **Owner:** GRC Lead / Head of Cloud Ops
**Incident Category:** Malware - Ransomware / Destructive Malware
**Severity:** P1 by default - downgrade only if confirmed fully isolated with zero spread risk

---

## CRITICAL - Read First

Ransomware is a P1 incident from the moment of suspicion. Do NOT wait for confirmation before acting.

**Do NOT:**
- Pay the ransom without Legal and CISO approval - payment does not guarantee decryption and may violate sanctions regulations
- Attempt to decrypt files yourself before the incident is contained
- Reconnect an isolated system to the network to "check if it is working"
- Delete ransom notes or encrypted files - these are evidence and may be needed for decryption
- Discuss the incident on corporate email or Slack if those systems may be compromised - use Signal

**Call the GRC Lead immediately. If unreachable: call CISO. If unreachable: call CEO.**

---

## Quick Reference

| Step | Action | Owner | Time Target |
|---|---|---|---|
| 1 | Detect - alert received or ransom note found | Any staff / monitoring | T+0 |
| 2 | ISOLATE affected systems from network | IT Admin / Head of Cloud Ops | T+0 to T+15 min |
| 3 | Notify GRC Lead and CISO | First responder | T+0 |
| 4 | Assemble full IRT | GRC Lead | T+15 min |
| 5 | Scope assessment - identify blast radius | Head of Cloud Ops + IT Admin | T+1 hr |
| 6 | Preserve evidence - snapshots and logs | Head of Cloud Ops | T+1 hr |
| 7 | Identify patient zero and infection vector | DevSecOps + Head of Cloud Ops | T+2 hr |
| 8 | Assess backup integrity | Head of Cloud Ops | T+2 hr |
| 9 | GDPR and client notification assessment | GRC Lead + Legal | T+4 hr |
| 10 | Begin eradication and recovery from clean backup | Head of Cloud Ops | After containment confirmed |
| 11 | Post-incident review | GRC Lead | T+5 business days |

---

## 1. Detection Triggers

This runbook is activated when any of the following occur:

- A ransom note or encrypted file extension (e.g. .locked, .encrypted, .XXXXX) is discovered on any system
- AWS GuardDuty or EDR agent alerts on ransomware-associated behaviour (mass file encryption, shadow copy deletion, rapid file modification)
- Datadog alerts on unusual I/O patterns, CPU spikes, or storage encryption activity
- Staff report files are inaccessible or have unknown extensions
- S3 buckets show unexpected bulk object modification or deletion activity
- A system becomes unreachable and recovery console shows encrypted volumes

---

## 2. Immediate Isolation (First 15 Minutes)

Time is the most critical factor. Every minute of delay allows the ransomware to encrypt more data.

### 2.1 Endpoint Isolation

IT Admin actions (can be performed remotely via Jamf):

1. Identify the affected endpoint(s) by hostname and user
2. Use Jamf to immediately disable network access on the affected device
3. Do NOT power off the device - volatile memory may contain decryption keys or attacker artefacts
4. If remote isolation is not possible: physically disconnect the ethernet cable; disable Wi-Fi via hardware switch if available
5. Notify the device user not to touch the machine

### 2.2 AWS Isolation

Head of Cloud Ops actions:

1. Identify affected EC2 instances, Lambda functions, or services from GuardDuty/CloudTrail alerts
2. Immediately modify the security group of affected EC2 instances to deny all inbound and outbound traffic (isolate in place - do NOT terminate)
3. Revoke IAM roles associated with affected instances to prevent lateral movement
4. Check S3 bucket policies and CloudTrail for any bucket encryption or deletion activity
5. Enable AWS Macie if not already active to identify data exposure scope
6. Take EBS snapshots of affected instances immediately - before any other action on those instances

### 2.3 Network-Level Isolation

Head of Cloud Ops actions:

1. Review VPC flow logs for lateral movement indicators (unusual inter-service traffic, unexpected outbound connections)
2. Block identified C2 (command and control) IP addresses at the VPC level
3. If active exfiltration is detected: isolate the affected VPC segment from the internet gateway

---

## 3. IRT Assembly and Initial Briefing

The GRC Lead convenes the full IRT within 15 minutes. Initial briefing agenda:
- What systems are confirmed affected
- What is the suspected encryption scope
- Is spread still active or is it contained
- Are backups intact and accessible
- Is client data potentially involved
- What external notifications may be required and on what timeline

---

## 4. Scope and Impact Assessment

### 4.1 Technical Scope

Head of Cloud Ops and DevSecOps determine:
- Which systems are encrypted (confirmed)
- Which systems are potentially infected but not yet encrypting (suspected)
- Whether any data was exfiltrated before encryption (double-extortion check: look for large outbound data transfers in VPC flow logs and CloudTrail in the 24-48 hours prior to encryption)
- The ransomware family if identifiable (submit hash to VirusTotal, ID Ransomware)
- The likely initial access vector (phishing, exposed RDP, vulnerable service, supply chain)

### 4.2 Data Impact

GRC Lead and Head of Cloud Ops determine:
- Which data classifications were present on affected systems (Restricted, Confidential, Internal)
- Whether any client PII or financial data is on affected systems
- Whether encrypted data is also exfiltrated - this is a data breach regardless of encryption

If client data is confirmed or suspected on affected systems: start the GDPR 72-hour notification clock. Do not wait for full forensic confirmation.

### 4.3 Backup Assessment

Head of Cloud Ops:
- Verify AWS backup integrity: check that S3 backups have not been encrypted or deleted
- Check whether any backups were mounted on infected systems (if so, they may be compromised)
- Identify the most recent clean backup point (before infection began)
- Confirm backup restoration is feasible within RTO

---

## 5. Communication

### 5.1 Internal

- IRT: Signal group (do not use corporate email or Slack if any risk those are compromised)
- CISO: immediate direct call
- CEO: notified by CISO once initial scope is known
- Staff: notify of service disruption without confirming ransomware publicly until communication strategy is agreed

### 5.2 External Notifications

| Party | Trigger | Timeline | Owner |
|---|---|---|---|
| GDPR supervisory authority (Irish DPC) | Personal data on affected systems | 72 hours from awareness | GRC Lead + Legal |
| Affected data subjects | High risk to individuals | Without undue delay after DPA notification | Legal |
| Affected clients (as data processor) | Client data on affected systems | Per DPA - typically 24-72 hours | GRC Lead + Account Manager |
| Cyber insurer | P1 incident | Per policy - typically within 72 hours | GRC Lead |
| Law enforcement (Garda, FBI if US nexus) | Criminal ransomware attack | Legal decision | Legal |
| AWS | If AWS infrastructure is the attack vector | Immediately | Head of Cloud Ops |

### 5.3 Ransom Demand

If a ransom demand is received:
- Do NOT respond to the attacker without Legal approval
- Do NOT pay without Legal and CISO sign-off and sanctions check (paying certain groups may violate OFAC regulations)
- Screenshot and preserve the ransom note in full
- Legal to assess whether cyber insurer covers ransom payment
- Decision framework: can data be recovered from clean backups? If yes: do not pay. If no clean backup exists: Legal leads decision with CISO and CEO.

---

## 6. Eradication

After containment is confirmed and backups are verified:

1. Identify patient zero (initial infection point) via CloudTrail, Okta logs, EDR telemetry
2. Identify all persistence mechanisms installed by the ransomware (scheduled tasks, cron jobs, registry keys, Lambda triggers)
3. Remove all malicious artefacts from any system that can be cleaned rather than rebuilt
4. Patch or remediate the initial access vulnerability before reconnecting any system
5. Rotate ALL credentials organisation-wide - assume all stored credentials are compromised in a P1 ransomware event
6. Rotate API keys, AWS IAM keys, Okta admin credentials, GitHub tokens

---

## 7. Recovery

**Principle: rebuild from clean image or restore from verified clean backup. Never recover in-place on a potentially infected system.**

Recovery sequence:
1. Restore from the identified clean backup point to isolated recovery environment
2. Validate data integrity before reconnecting to production
3. Apply all security patches to restored systems before reconnecting
4. Re-establish MFA on all accounts before restoring user access
5. Reconnect systems in stages - not all at once - monitoring for re-infection at each stage
6. Validate business functionality at each stage before proceeding
7. Declare recovery complete only when all critical services are verified functional and 48-hour post-recovery monitoring shows no anomalies

---

## 8. Post-Incident Actions

- Lessons learned meeting within 5 business days (P1 mandatory)
- Post-incident report: executive summary + full technical timeline + root cause + remediation plan
- Update risk register: adjust likelihood and impact of ransomware risk based on incident
- Review and if necessary implement additional controls: network segmentation, immutable backups, privileged access tightening, EDR coverage expansion
- Brief all staff on the incident (sanitised version) as part of awareness improvement
- Consider engaging external forensic firm to validate eradication completeness

---

## 9. Key Contacts

| Role | Responsibility |
|---|---|
| GRC Lead | Incident Commander; regulatory notifications; post-incident report |
| Head of Cloud Ops | AWS isolation; backup assessment; technical recovery |
| IT Admin | Endpoint isolation; credential rotation; Okta response |
| DevSecOps | Malware analysis; patient zero identification; secrets rotation |
| CISO | Executive escalation; client communication approval; ransom decision |
| Legal | Regulatory notifications; law enforcement; ransom payment decision |

---

*ResolvX GRC Program - IR-RB-002 - v1.0 - 2026 - Internal - Restricted*
