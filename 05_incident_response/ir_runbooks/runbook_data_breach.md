# Runbook: Data Breach Incident Response

**Runbook ID:** IR-RB-003 | **Version:** 1.0 | **Owner:** GRC Lead / Legal
**Incident Category:** Data Breach - Unauthorised Access, Exfiltration, or Accidental Disclosure
**Severity Range:** P1 - P3 depending on data classification, volume, and affected parties

---

## Quick Reference

| Step | Action | Owner | Time Target |
|---|---|---|---|
| 1 | Breach detected or reported - open incident log | Any / GRC Lead | T+0 |
| 2 | Stop the bleeding - contain the disclosure | IT Admin / Head of Cloud Ops | T+15 min |
| 3 | Identify what data was affected and how many individuals | GRC Lead + Head of Cloud Ops | T+2 hr |
| 4 | Determine GDPR notification obligation | GRC Lead + Legal | T+4 hr |
| 5 | Notify DPA if required (72-hour clock running) | GRC Lead + Legal | T+72 hr max |
| 6 | Notify affected clients if client data involved | GRC Lead + Account Manager | Per DPA |
| 7 | Eradicate root cause | Technical team | After containment |
| 8 | Notify affected data subjects if high risk | Legal | Without undue delay after DPA |
| 9 | Post-incident report and lessons learned | GRC Lead | T+5 business days |

---

## 1. Detection Triggers

This runbook is activated when any of the following occur:

- AWS GuardDuty, Macie, or CloudTrail detect unusual bulk data access or large outbound data transfers
- An employee reports accidentally sending client data to the wrong recipient
- A client or data subject reports receiving data belonging to another person
- A staff member reports finding ResolvX client data exposed in a public S3 bucket or repository
- An external security researcher or third party reports a data exposure
- A vendor notifies ResolvX of a breach affecting ResolvX data held in their systems
- GitHub secret scanning alerts on committed credentials or data
- Datadog alerts on anomalous database query volumes or API response sizes

---

## 2. Severity Determination

| Scenario | Data Classification | Severity |
|---|---|---|
| Accidental email disclosure - single record, Internal data | Internal | P4 |
| Accidental email disclosure - small number of records, Confidential | Confidential | P3 |
| Accidental disclosure of personal data - limited scope, low risk to individuals | Restricted (PII) | P3 |
| Confirmed exfiltration or exposure of personal data - medium scope | Restricted (PII) | P2 |
| Large-scale exfiltration of client PII or financial data | Restricted (PII + financial) | P1 |
| Public exposure of Restricted data (open S3 bucket, public repo) | Restricted | P1 |
| Vendor breach confirmed to have affected ResolvX client data | Restricted | P1 |

---

## 3. Containment Steps

### 3.1 Stop Active Disclosure

Head of Cloud Ops and IT Admin:

- If public S3 bucket: immediately set bucket ACL to private; remove public access block exception; audit bucket policy
- If API over-exposure: revoke the relevant API key or rotate; review API gateway logs for access scope
- If database misconfiguration: remove public access; review security group rules
- If accidental email: cannot be unsent - proceed to scope assessment; request deletion from recipient if internal
- If GitHub commit: remove from repo history using git filter-branch or BFG; rotate any exposed credentials immediately; check if commit was indexed by any public source
- If vendor breach: contact vendor immediately for scope confirmation; isolate integration if possible

### 3.2 Preserve Evidence

- Capture AWS CloudTrail logs for the relevant time window before any remediation
- Capture S3 access logs, API Gateway logs, or database audit logs as applicable
- Screenshot any public exposure before taking it down
- Record the timeline: when data was first potentially exposed, when detected, when contained
- Preserve all evidence per IR-PLAN-001 Section 5.3

---

## 4. Scope and Impact Assessment

### 4.1 What Data Was Affected

GRC Lead and Head of Cloud Ops must determine:

| Question | Why It Matters |
|---|---|
| What data classification? | Determines notification requirements and urgency |
| What categories of personal data? (names, financials, health, IDs) | Determines risk level to individuals |
| Approximately how many individuals affected? | Required for DPA notification |
| Is this data subject to a DPA with a client? | Triggers processor-to-controller notification obligation |
| Was the data accessed by an unauthorised party, or just exposed? | Affects severity and risk assessment |
| Is there evidence the data was exfiltrated, or was it just accessible? | Access logs may not capture all access |

### 4.2 Risk Assessment for GDPR Notification

Per GDPR Art. 33: notification to the supervisory authority is required unless the breach is **unlikely to result in a risk to the rights and freedoms of natural persons.**

Risk factors that increase likelihood of notification requirement:
- Special category data involved (health, ethnicity, biometrics, financial details)
- Large number of individuals affected
- Data accessible for extended period
- Evidence of malicious access (not just accidental exposure)
- Vulnerable individuals in the affected group (minors, financially distressed)
- Data could facilitate identity theft, fraud, or discrimination

The GRC Lead and Legal make the notification decision jointly. When in doubt: notify.

---

## 5. GDPR Notification Process

### 5.1 The 72-Hour Clock

The clock starts from the moment ResolvX becomes **aware of a probable breach** - not from confirmation or full scope assessment.

If a full assessment cannot be completed within 72 hours, notify the DPA with the information available and supplement with additional information as it becomes available. GDPR Art. 33(4) explicitly permits phased notification.

### 5.2 Notification to Supervisory Authority (Art. 33)

Primary DPA: Irish Data Protection Commission (DPC) - www.dataprotection.ie

Required content per Art. 33(3):
- Nature of the breach (including categories and approximate number of data subjects and records)
- Name and contact details of the GRC Lead (DPO-equivalent)
- Likely consequences of the breach
- Measures taken or proposed to address the breach and mitigate its effects

Submit via the DPC online notification form. GRC Lead files; Legal reviews before submission.

### 5.3 ResolvX as Data Processor - Client Notification

When ResolvX is processing data on behalf of a client (data controller) and a breach affects that client's data:

1. Notify the relevant client (controller) without undue delay - contract SLA applies (typically 24-72 hours)
2. Provide: incident summary; data categories affected; preliminary root cause; immediate actions taken; next steps; GRC Lead contact
3. Do NOT notify the data subjects directly - that is the controller's obligation
4. Assist the controller in fulfilling their notification obligations

Account Manager coordinates the notification with GRC Lead drafting the content and CISO approving before sending.

### 5.4 Data Subject Notification (Art. 34)

Required when the breach is likely to result in a **high risk** to individuals' rights and freedoms (higher threshold than DPA notification).

High risk indicators: financial data enabling fraud; identity theft enablement; safety risks; significant distress.

Content required: plain language description; likely consequences; contact point; measures taken.

Legal leads on drafting and timing. Coordinate with client (controller) if ResolvX is acting as processor.

---

## 6. Eradication

- Remediate the root cause of the breach (misconfigured access control, compromised credential, vulnerable endpoint)
- Verify the exposure point is closed and cannot be re-exploited
- Audit similar configurations across all systems for the same class of vulnerability
- If credentials were exposed: rotate all potentially compromised credentials
- If code contained sensitive data: audit all repositories for similar issues using automated scanning

---

## 7. Recovery and Monitoring

- Restore normal operations after root cause is remediated and verified
- Implement enhanced monitoring on affected systems for 30 days post-incident
- Verify data integrity: confirm no data was modified or deleted during the incident
- Review and if necessary update access controls on systems similar to those involved

---

## 8. Special Scenarios

### 8.1 Accidental Email to Wrong Recipient (Internal Data)

1. Contact the recipient immediately and request deletion
2. If recipient is external: Legal to draft a formal request for deletion and confirmation
3. Document the incident; assess whether personal data was included
4. If personal data: follow GDPR assessment steps in Section 4.2

### 8.2 Public GitHub Repository with Sensitive Data

1. GRC Lead and DevSecOps - make repository private immediately
2. Rotate any committed credentials immediately regardless of how old the commit is
3. Assess: was the repo indexed by search engines or GitHub code search? (Check Google cache, GitHub search)
4. Remove sensitive data from git history using BFG Repo-Cleaner
5. Assess whether exposed credentials were used by any unauthorised party (check AWS CloudTrail, Okta logs)

### 8.3 Third-Party / Vendor Breach

1. Confirm scope with vendor: what data was affected, what time period, what evidence of access
2. Request vendor's incident report and breach notification
3. Map vendor's affected data to ResolvX's data classification
4. Proceed with GDPR assessment and notification as if ResolvX were the breached party
5. Review vendor's DPA for indemnification obligations
6. Document for vendor risk register: update vendor assessment and consider tier re-evaluation

---

## 9. Post-Incident Actions

- Lessons learned meeting within 5 business days (P1/P2); 10 business days (P3)
- Post-incident report required for P1/P2
- Update breach register (POL-006 Part A.9)
- Update risk register with revised data breach risk rating
- Review and if necessary strengthen data handling controls: access restrictions, DLP, S3 bucket policies, secrets management
- If vendor involved: update vendor risk register and consider re-assessment

---

## 10. Key Contacts

| Role | Responsibility |
|---|---|
| GRC Lead | Incident Commander; GDPR notification decision; DPA notification filing; client notification coordination |
| Legal | Data subject notification decision; DPA correspondence; law enforcement decision; vendor DPA review |
| Head of Cloud Ops | Technical containment; AWS log preservation; scope assessment |
| IT Admin | Endpoint/account containment; email forensics |
| Account Manager | Client notification delivery (content from GRC Lead) |
| CISO | P1/P2 approval; external communications sign-off |

---

*ResolvX GRC Program - IR-RB-003 - v1.0 - 2026 - Internal - Restricted*
