# 🌐 ResolvX — Threat Landscape Analysis

> **Program:** GRC Compliance & Audit Readiness | **Phase:** 2 — Risk & Controls | **Version:** 1.0

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Phase](https://img.shields.io/badge/Phase-2%20Risk%20%26%20Controls-purple?style=flat-square)
![Standard](https://img.shields.io/badge/Standard-NIST%20SP%20800--30%20Appendix%20D%20%26%20E-blue?style=flat-square)
![Industry](https://img.shields.io/badge/Industry-FinTech%20%7C%20SaaS%20%7C%20Service%20Organization-orange?style=flat-square)
![Owner](https://img.shields.io/badge/Owner-GRC%20Lead-lightgrey?style=flat-square)

---

## Purpose

This document provides the threat intelligence context that underpins ResolvX's risk register. Risk scores don't exist in a vacuum, they are calibrated against the real threat environment that ResolvX operates in as a cloud-native fintech SaaS service organisation handling sensitive financial and PII data on behalf of enterprise clients.

The threat landscape is structured using the **NIST SP 800-30 Rev. 1 Threat Source Taxonomy** (Appendix D), which classifies threat sources as Adversarial, Accidental, Structural, and Environmental. Each category is then contextualised for ResolvX's specific industry, technology stack, and client exposure.

> **This document should be reviewed and updated at least annually, or following any material change to ResolvX's technology environment, client base, or regulatory landscape.**

---

## ResolvX Threat Context

ResolvX occupies a uniquely high-value position in the threat landscape. As a service organisation that processes dispute resolution workflows for financial institutions, ResolvX sits at the intersection of several threat vectors simultaneously:

| Threat Driver | ResolvX Exposure |
|---|---|
| **High-value data** | PII, financial records, dispute case files, attractive to financially motivated threat actors |
| **Service organisation model** | Breaching ResolvX means accessing data across all client organisations simultaneously |
| **Regulatory scrutiny** | Fintech sector faces active enforcement from NYDFS, CFPB, and EU regulators |
| **Cloud-native architecture** | AWS-hosted environments are actively targeted via misconfiguration and credential attacks |
| **Third-party dependencies** | Stripe, Okta, and SendGrid integrations extend the attack surface beyond ResolvX's direct control |
| **Enterprise client pipeline** | SOC 2 audit targets and enterprise sales cycles create reputational risk from any incident |

---

## Threat Source Taxonomy
*Source: NIST SP 800-30 Rev. 1, Appendix D, Table D-2 — tailored for ResolvX*

### 1️⃣ Adversarial Threat Sources

Adversarial threats are initiated by individuals, groups, or nation-states that deliberately seek to exploit ResolvX's systems, data, or processes. They are characterised by **Capability, Intent, and Targeting**.

#### 🔴 Organised Cybercriminal Groups (Ransomware-as-a-Service)

| Attribute | Assessment |
|---|---|
| **Capability** | High : RaaS groups operate with enterprise-grade tooling, double-extortion models, and dedicated negotiation teams |
| **Intent** | Financial : maximise ransom payment and/or data sale value |
| **Targeting** | Active : fintech and financial services are top-5 targeted sectors globally |
| **Primary TTPs** | Phishing for initial access → lateral movement → data exfiltration → encryption deployment |
| **Relevance to ResolvX** | **High** : dispute case files and PII databases represent high-value exfiltration targets |
| **Risk Register** | RSK-001 (Ransomware), RSK-002 (Phishing) |

#### 🔴 External Attackers (Opportunistic & Targeted)

| Attribute | Assessment |
|---|---|
| **Capability** | Variable : ranges from script kiddies using public exploits to sophisticated APT groups |
| **Intent** | Financial gain, data theft, competitive intelligence, or disruption |
| **Targeting** | Opportunistic via automated scanning; targeted via sector-specific campaigns |
| **Primary TTPs** | API exploitation, credential stuffing, SQL injection, cloud misconfiguration abuse |
| **Relevance to ResolvX** | **High** : public-facing API Gateway and cloud infrastructure are continuously scanned |
| **Risk Register** | RSK-003 (API exploitation), RSK-006 (S3 misconfiguration), RSK-008 (IAM abuse) |

#### 🟠 Malicious Insiders

| Attribute | Assessment |
|---|---|
| **Capability** | High : privileged access to systems, data, and processes without detection controls |
| **Intent** | Financial gain, grievance, corporate espionage, or coercion by external actor |
| **Targeting** | Specific : targets high-value data (dispute files, client PII, financial records) |
| **Primary TTPs** | Unauthorised data download, credential sharing, sabotage, policy bypass |
| **Relevance to ResolvX** | **Moderate-High** : small team size creates elevated individual access risk |
| **Risk Register** | RSK-004 (Insider threat), RSK-022 (Offboarding gaps) |

#### 🟠 Nation-State / Advanced Persistent Threat (APT) Actors

| Attribute | Assessment |
|---|---|
| **Capability** | Very High : sophisticated, well-resourced, long-dwell-time operations |
| **Intent** | Intelligence collection, financial system disruption, supply chain compromise |
| **Targeting** | Selective : primarily targets critical financial infrastructure and their service providers |
| **Primary TTPs** | Supply chain attacks, zero-day exploitation, living-off-the-land techniques |
| **Relevance to ResolvX** | **Moderate** : indirect risk as a supplier to financial institutions |
| **Risk Register** | RSK-005 (Supply chain attack) |

#### 🟡 Competitors / Corporate Espionage

| Attribute | Assessment |
|---|---|
| **Capability** | Moderate : varies by competitor; typically targets IP and client lists |
| **Intent** | Competitive advantage : client data, pricing, product roadmap |
| **Targeting** | Selective : targets sales pipeline, product data, and enterprise client relationships |
| **Relevance to ResolvX** | **Low-Moderate** : growing market creates competitive pressure |
| **Risk Register** | RSK-004 (Insider threat - contractor risk) |

---

### 2️⃣ Accidental Threat Sources

Accidental threats arise from human error, unintentional actions by employees or administrators that create security or compliance exposure. These are among the most common causes of data breaches in cloud-native organisations.

#### 🟠 Developer / Engineer Error

| Attribute | Assessment |
|---|---|
| **Typical Events** | Hardcoded credentials in source code, publicly exposed S3 buckets, insecure API endpoints, over-privileged IAM roles |
| **Frequency** | High : cloud environments create many opportunities for misconfiguration |
| **Relevance to ResolvX** | **High** : fast-moving engineering team in a cloud-native environment without mature DevSecOps controls |
| **Risk Register** | RSK-006 (S3 misconfiguration), RSK-008 (IAM over-privilege), RSK-009 (Secrets management) |

#### 🟠 End User Error

| Attribute | Assessment |
|---|---|
| **Typical Events** | Clicking phishing links, sending data to wrong recipients, misconfiguring access permissions, weak password practices |
| **Frequency** | Moderate-High : without regular training, error rates remain elevated |
| **Relevance to ResolvX** | **High** : all employees handle internal systems; Customer Success handles client communications |
| **Risk Register** | RSK-002 (Phishing), RSK-021 (Security awareness gap) |

#### 🟡 Administrative / Process Error

| Attribute | Assessment |
|---|---|
| **Typical Events** | Failed offboarding leaving active accounts, change control bypass, missed patch cycles |
| **Frequency** | Moderate : more common in growth-stage companies without formalised processes |
| **Relevance to ResolvX** | **Moderate** : offboarding and change management gaps identified in risk register |
| **Risk Register** | RSK-022 (Offboarding), RSK-024 (Change management) |

---

### 3️⃣ Structural Threat Sources

Structural threats arise from failures of technology, software, or infrastructure components — not caused by humans, but by the inherent fragility of systems under load, over time, or at scale.

#### 🟠 Cloud Infrastructure Failure (AWS)

| Attribute | Assessment |
|---|---|
| **Typical Events** | AWS regional outage, availability zone failure, RDS instance failure, EKS node group disruption |
| **Historical Precedent** | AWS us-east-1 has experienced multiple notable outages (2021, 2022) impacting major SaaS platforms |
| **Relevance to ResolvX** | **Moderate-High** : 100% AWS dependency in single primary region |
| **Risk Register** | RSK-007 (AWS outage / SLA breach), RSK-020 (SLA breach) |

#### 🟡 Software Vulnerability (Third-Party Dependencies)

| Attribute | Assessment |
|---|---|
| **Typical Events** | Unpatched CVEs in open-source libraries, container base images, or infrastructure components |
| **Frequency** | Continuous : new CVEs published daily against common frameworks |
| **Relevance to ResolvX** | **Moderate-High** : modern Node.js/Python applications carry large dependency trees |
| **Risk Register** | RSK-003 (API vulnerability), RSK-005 (Supply chain / dependency attack) |

#### 🟡 Logging & Monitoring Gaps

| Attribute | Assessment |
|---|---|
| **Typical Events** | Incomplete log coverage creates blind spots; delayed alerting extends breach dwell time |
| **Relevance to ResolvX** | **Moderate** : current CloudTrail and CloudWatch coverage insufficient for comprehensive detection |
| **Risk Register** | RSK-010 (Logging and monitoring gaps) |

---

### 4️⃣ Environmental Threat Sources

Environmental threats are external to ResolvX and largely outside its direct control — natural events, infrastructure failures, and regulatory changes that affect operations.

#### 🟡 Natural Disaster / Physical Infrastructure Failure

| Attribute | Assessment |
|---|---|
| **Typical Events** | Data centre power failure, physical disaster affecting AWS us-east-1 (N. Virginia) region |
| **Frequency** | Low : major regional failures are rare but not impossible |
| **Relevance to ResolvX** | **Low-Moderate** : mitigated by AWS multi-AZ but no active DR in secondary region |
| **Risk Register** | RSK-007 (AWS outage), RSK-025 (BCP absence) |

#### 🟠 Regulatory & Legal Environment Change

| Attribute | Assessment |
|---|---|
| **Typical Events** | New privacy regulation, NYDFS amendment, FTC enforcement action, CFPB rule change affecting fintech |
| **Frequency** | Moderate : regulatory landscape for fintech is actively evolving |
| **Relevance to ResolvX** | **High** : serving regulated financial institutions means downstream regulatory changes directly affect ResolvX's compliance posture |
| **Risk Register** | RSK-016 (SOC 2 failure), RSK-017 (GDPR), RSK-018 (PCI-DSS), RSK-019 (CCPA) |

#### 🟡 Vendor / Supply Chain Disruption

| Attribute | Assessment |
|---|---|
| **Typical Events** | Key vendor (Stripe, Okta) ceases operations, changes pricing/terms materially, or suffers a major incident |
| **Frequency** | Low : Tier 1 vendors are generally stable, but vendor incidents do occur (Okta 2022/2023) |
| **Relevance to ResolvX** | **Moderate** : high dependency on a small number of critical vendors |
| **Risk Register** | RSK-011 (AWS concentration), RSK-012 (Stripe), RSK-013 (Okta) |

---

## Fintech Industry Threat Intelligence Context

The following summarises key threat trends specific to the financial technology sector that informed ResolvX's risk register prioritisation.

### Top Attack Vectors Targeting FinTech SaaS (2024–2026)

| Rank | Attack Vector | ResolvX Exposure | Risk IDs |
|---|---|---|---|
| 1 | **API abuse & exploitation** | High : core product is API-driven | RSK-003 |
| 2 | **Credential theft & account takeover** | High : Okta SSO is single auth layer | RSK-002, RSK-013 |
| 3 | **Ransomware (double extortion)** | High : high-value data = high ransom potential | RSK-001 |
| 4 | **Cloud misconfiguration** | High : AWS-native, fast-moving engineering | RSK-006, RSK-008, RSK-009 |
| 5 | **Supply chain compromise** | Moderate : third-party dependencies and SaaS vendors | RSK-005, RSK-012 |
| 6 | **Insider threat** | Moderate : small team, high data access | RSK-004 |
| 7 | **Social engineering (BEC)** | Moderate : financial context makes BEC lucrative | RSK-002 |
| 8 | **Regulatory non-compliance** | High : fintech regulatory environment actively enforced | RSK-016–RSK-020 |

### Key Industry Events Informing This Assessment

| Event | Relevance to ResolvX |
|---|---|
| **Okta support system breach (2023)** | Validated RSK-013 — identity provider incidents have cascading downstream impact on all dependent organisations |
| **MOVEit supply chain attack (2023)** | Validated RSK-005 — third-party software vulnerabilities can expose hundreds of organisations simultaneously |
| **AWS us-east-1 outages (2021–2022)** | Validated RSK-007 — single-region cloud dependencies create material availability risk |
| **NYDFS enforcement actions (2023–2024)** | Validated RSK-016–RSK-020 — regulators actively enforcing cybersecurity requirements against fintech service providers |
| **Cl0p ransomware fintech targeting (2023–2024)** | Validated RSK-001 — organised RaaS groups specifically targeting financial data custodians |

---

## Threat Landscape to Risk Register Mapping

| Threat Source | Type | Risk IDs | Residual Level |
|---|---|---|---|
| Organised cybercriminal / RaaS | Adversarial | RSK-001, RSK-002 | 🔴 High / 🟠 Moderate |
| External attacker : opportunistic | Adversarial | RSK-003, RSK-006, RSK-008 | 🔴 High / 🟠 Moderate |
| Malicious insider | Adversarial | RSK-004, RSK-022 | 🟠 Moderate |
| Nation-state / APT | Adversarial | RSK-005 | 🔴 High |
| Developer / engineer error | Accidental | RSK-006, RSK-009, RSK-010 | 🟠 Moderate |
| End user error | Accidental | RSK-002, RSK-021 | 🟠 Moderate |
| Administrative process error | Accidental | RSK-022, RSK-024 | 🟠 Moderate |
| AWS infrastructure failure | Structural | RSK-007, RSK-020 | 🟡 Low |
| Software vulnerability | Structural | RSK-003, RSK-005 | 🔴 High |
| Regulatory environment change | Environmental | RSK-016–RSK-020 | 🔴 High / 🟠 Moderate |
| Vendor disruption | Environmental | RSK-011, RSK-012, RSK-013 | 🟠 Moderate |

---

## Threat Landscape Review Cycle

| Trigger | Action |
|---|---|
| **Annual** | Full threat landscape review : update threat actor profiles, industry intelligence, and risk register alignment |
| **Post-incident** | Re-evaluate threat source capability and intent ratings following any security incident |
| **New regulation / enforcement action** | Update regulatory threat section and re-assess compliance risk ratings |
| **New vendor or technology addition** | Assess new threat vectors introduced and update relevant risk entries |
| **Major industry breach (peer organisation)** | Evaluate applicability to ResolvX and update relevant risk scores |

---

*ResolvX GRC Program — Internal Use Only — v1.0 — 2026*
*Standards Reference: NIST SP 800-30 Rev. 1, Appendix D (Threat Sources) & Appendix E (Threat Events)*
