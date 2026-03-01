# Runbook: Phishing Incident Response

**Runbook ID:** IR-RB-001 | **Version:** 1.0 | **Owner:** GRC Lead
**Incident Category:** Social Engineering - Phishing / Spear Phishing / BEC
**Severity Range:** P2 - P4 (escalates to P1 if credentials confirmed compromised and client data accessed)

---

## Quick Reference

| Step | Action | Owner | Time Target |
|---|---|---|---|
| 1 | Report received - open incident log | Any staff / GRC Lead | T+0 |
| 2 | Preserve email evidence | IT Admin | T+15 min |
| 3 | Determine if user clicked / entered credentials | IT Admin + GRC Lead | T+30 min |
| 4 | If credentials entered: revoke sessions immediately | IT Admin | T+30 min |
| 5 | Scope - identify other recipients | IT Admin + GRC Lead | T+1 hr |
| 6 | Block sender domain / IOCs | IT Admin | T+1 hr |
| 7 | Staff alert if campaign confirmed | Incident Commander | T+2 hr |
| 8 | Assess for data breach | GRC Lead | T+4 hr |
| 9 | Post-incident review | GRC Lead | T+5 business days |

---

## 1. Detection Triggers

This runbook is activated when any of the following occur:

- A staff member reports a suspicious email via #security-alerts or directly to GRC Lead
- Okta threat intelligence flags a login from an impossible travel location or new device after a phishing link click
- Google Workspace or M365 anti-phishing rules quarantine a high-confidence phishing email
- A staff member reports entering credentials on a suspicious site
- IT Admin detects an account logging in from an unusual IP immediately following a phishing alert
- External party (e.g. client, partner) reports receiving a phishing email purportedly from a ResolvX address

---

## 2. Initial Triage (First Responder)

**Do not click any links. Do not forward the email to colleagues. Do not reply to the sender.**

Collect the following information immediately:

- Full email headers (in Gmail: three-dot menu > Show Original)
- Screenshot of the email body
- URL(s) in the email - record but do not visit
- Name(s) of recipients who received the email
- Whether any recipient clicked a link
- Whether any recipient entered credentials or other data
- Time the email was received

Record all of the above in the Incident Log (IR-LOG-001) and notify the GRC Lead immediately.

---

## 3. Severity Determination

| Scenario | Severity |
|---|---|
| Email received and reported - no clicks, no credential entry | P4 |
| Email clicked - redirected to phishing site - no credential entry confirmed | P3 |
| Credentials entered on phishing site - no system access detected | P2 |
| Credentials entered - unauthorised login detected | P2 escalating |
| Credentials entered - client data or production systems accessed | P1 |
| Business Email Compromise (BEC) - financial transaction requested | P2 |
| CEO / executive impersonation targeting finance team | P2 |

---

## 4. Containment Steps

### 4.1 Preserve Evidence (IT Admin - within 15 minutes)

- Export the phishing email with full headers from Google Workspace Admin console
- Record sender address, reply-to address, originating IP, and all embedded URLs
- Submit URLs to VirusTotal for analysis - record results
- Do NOT delete the email from affected mailboxes until evidence is captured
- Preserve Okta authentication logs for all potentially affected accounts for the relevant time window

### 4.2 Credential Revocation (IT Admin - within 30 minutes if credentials entered)

If any staff member confirms entering credentials on a phishing site:

1. Immediately revoke all active Okta sessions for the affected account
2. Force password reset via Okta admin console
3. Verify MFA devices on the account - revoke all and re-enrol if any doubt
4. Check Okta audit log for any logins from unfamiliar IP addresses or devices in the past 24 hours
5. If privileged account affected: escalate to P2 immediately and notify CISO

### 4.3 Block Sender and Indicators (IT Admin - within 1 hour)

- Add sender domain(s) to Google Workspace/M365 blocked sender list
- Block phishing URL(s) at DNS level via corporate DNS filtering
- If impersonating a legitimate domain: assess whether DMARC/DKIM/SPF spoofing was used; report to relevant domain registrar if applicable
- Share IOCs (sender domains, URLs, subject lines) with Slack #security-alerts for awareness

### 4.4 Scope Assessment (GRC Lead - within 1 hour)

- Search Google Workspace Admin for all recipients of the phishing email
- Query Okta logs for any authentication events from affected accounts in the relevant window
- Determine if the email was part of a broader campaign (similar emails to other staff)
- Check if any automated forwarding rules were added to affected mailboxes
- Check if any OAuth applications were granted access from affected accounts

---

## 5. Eradication Steps

- Remove the phishing email from all affected mailboxes using Google Workspace Admin bulk delete
- Revoke any OAuth app permissions granted during the incident window for affected accounts
- Remove any email forwarding rules created by the attacker
- If any malware was delivered via attachment: follow Runbook IR-RB-002 for endpoint response
- Rotate any API keys or service account credentials accessible from affected accounts

---

## 6. Recovery Steps

- Re-enable affected accounts after credential rotation and MFA re-enrolment are confirmed
- Monitor affected accounts closely for 48 hours post-recovery via Okta audit logs
- Verify no new forwarding rules, OAuth grants, or calendar invites from the incident window remain
- Confirm with affected staff member that account behaviour is normal

---

## 7. Communication

### 7.1 Internal Staff Alert (if campaign confirmed - multiple recipients)

Send via IT Admin from a verified clean account:

> **SECURITY ALERT - Action Required**
> We have identified a phishing email campaign targeting ResolvX staff. Subject line: [SUBJECT].
> Sender address: [SENDER].
> If you received this email: do not click any links. Do not reply.
> If you clicked a link or entered any credentials: contact IT Admin immediately at [CONTACT].
> If you are unsure: contact IT Admin before taking any action.

### 7.2 CISO Notification

Required for: P1/P2; any confirmed credential compromise; any BEC or financial fraud attempt.

### 7.3 Client Notification

Required if: phishing email was sent from a compromised ResolvX email account to clients; or if client data was accessed following credential compromise. Refer to POL-006 Section A.9 and IR-PLAN-001 Section 5.2.

---

## 8. Post-Incident Actions

- Document full timeline in Incident Log and close when recovery is confirmed
- Lessons learned meeting within 5 business days for P1/P2; within 10 days for P3
- Consider whether targeted phishing awareness training is warranted for affected team(s)
- Review whether any technical controls (e.g. stricter email filtering, additional MFA enforcement) would have prevented or reduced impact
- Update phishing simulation templates to include characteristics of the observed attack
- Share sanitised IOCs with sector ISAC or threat intelligence sharing partners if applicable

---

## 9. Key Contacts

| Role | Responsibility in this runbook |
|---|---|
| GRC Lead | Incident Commander; GDPR assessment; client notification decision |
| IT Admin | Account revocation; email forensics; IOC blocking |
| Head of Cloud Ops | If AWS resources accessed following credential compromise |
| Legal | If financial fraud occurred; if law enforcement engagement considered |
| CISO | P1/P2 escalation; client communication approval |

---

*ResolvX GRC Program - IR-RB-001 - v1.0 - 2026 - Internal - Restricted*
