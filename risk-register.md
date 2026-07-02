---
title: Risk Register
document_id: FENN-POL-008
version: "1.0"
effective_date: 2026-07-01
last_reviewed: 2026-07-01
next_review: 2027-07-01
owner: Jack Lowe, Head of Security
approver: Zoe Cooper-Hartley, CEO
scope: All Fenn information assets, including systems, data, people, and third-party vendors
framework_mapping:
  - ISO 27001:2022 Clause 6.1.2
  - ISO 27001:2022 Clause 6.1.3
  - ISO 27001:2022 Clause 8.2
  - ISO 27001:2022 Clause 8.3
  - UK GDPR Art. 32
---

# Risk Register

## 1. Purpose

This register records the information security risks identified through Fenn's risk assessment process. It documents each risk's scoring, treatment decision, and assigned owner. It is the primary evidence that Fenn has assessed and is managing its information security risks in accordance with ISO 27001:2022 and UK GDPR Art. 32.

## 2. How to Read This Register

Risks are scored using the methodology defined in FENN-POL-007. Likelihood and impact are each rated 1 to 5. Risk score equals likelihood multiplied by impact. Scores of 1 to 5 are Low, 6 to 12 are Medium, and 13 to 25 are High. Inherent risk is the score before controls are applied. Residual risk is the score after controls are applied.

## 3. Risk Register

| ID | Risk | Asset | CIA | Inh. L | Inh. I | Inh. Score | Rating | Controls | Annex A | Treatment | Res. L | Res. I | Res. Score | Owner |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RR-001 | Ransomware or destructive malware encrypts or destroys Fenn infrastructure | Platform infrastructure, customer data | C, I, A | 3 | 5 | 15 | High | Endpoint detection and response on all devices; immutable, encrypted backups; incident response plan (FENN-POL-003); security awareness training; patch management | A.8.7, A.8.13, A.8.16, A.5.26, A.6.3 | Mitigate | 2 | 5 | 10 | Head of Security |
| RR-002 | Phishing or social engineering leads to credential compromise | Employee accounts, Fenn systems | C, I | 4 | 3 | 12 | Medium | Hardware security keys (Nitrokey 3) required for all staff; JumpCloud SSO; phishing awareness training; privileged access controls (FENN-POL-001) | A.8.5, A.5.16, A.5.17, A.6.3, A.5.15 | Mitigate | 2 | 3 | 6 | Head of Security |
| RR-003 | Insider threat: employee or contractor accesses or exfiltrates data without authorization | Customer data, employee data, Fenn systems | C, I | 2 | 4 | 8 | Medium | Least privilege access; JIT privileged access; quarterly access reviews; all privileged sessions logged; JML process (FENN-POL-001) | A.5.15, A.8.2, A.8.5, A.8.15, A.5.18, A.6.5 | Mitigate | 1 | 4 | 4 | Head of Security |
| RR-004 | Cloud misconfiguration exposes Fenn systems or customer data | AWS infrastructure, customer data | C, A | 3 | 4 | 12 | Medium | AWS configuration reviewed against CIS benchmarks; IAM least privilege enforced; VPC architecture reviewed; changes follow documented change management process | A.8.9, A.5.15, A.8.20, A.5.23, A.8.2 | Mitigate | 2 | 3 | 6 | CTO |
| RR-005 | Sub-processor breach exposes data Fenn has shared with a third-party vendor | Customer data, employee data | C | 2 | 4 | 8 | Medium | Vendor risk tiering (FENN-POL-004); DPAs in place with all sub-processors; sub-processor list maintained; contractual security requirements; right to audit | A.5.19, A.5.20, A.5.22, A.5.31 | Mitigate | 1 | 4 | 4 | Head of Security |
| RR-006 | Software supply chain compromise introduces malicious code via a dependency or package | Platform infrastructure, customer data | C, I, A | 2 | 4 | 8 | Medium | Dependency scanning; Dependabot alerts enabled; code review required before merge; software bill of materials maintained | A.5.21, A.8.25, A.8.29 | Mitigate | 2 | 3 | 6 | CTO |
| RR-007 | API authentication bypass allows unauthorized access to the Fenn platform | Platform infrastructure, customer data, employee data | C, I, A | 3 | 5 | 15 | High | API authentication enforced on all endpoints; penetration testing; access logging via AWS CloudTrail and GuardDuty; application error alerting via Sentry; incident response plan (FENN-POL-003) | A.8.5, A.8.3, A.8.16, A.8.20, A.5.26 | Mitigate | 2 | 4 | 8 | CTO |
| RR-008 | Insecure code deployed to production introduces exploitable vulnerability | Platform infrastructure, customer data | C, I, A | 3 | 4 | 12 | Medium | Mandatory code review; staging environment required before production deployment; automated security testing in CI/CD pipeline; secure development training | A.8.25, A.8.26, A.8.28, A.8.29 | Mitigate | 2 | 3 | 6 | CTO |
| RR-009 | Accidental data exposure during development or support activity | Customer data, employee data | C | 2 | 4 | 8 | Medium | Production data not used in development or testing environments; support access granted JIT and logged; access revoked on ticket close | A.8.3, A.5.15, A.8.33, A.8.5 | Mitigate | 1 | 4 | 4 | Head of Security |
| RR-010 | UK GDPR non-compliance leads to ICO investigation or enforcement action | Customer data, employee data | C | 2 | 4 | 8 | Medium | Data retention policy (FENN-POL-005); DPA in place for all processor relationships; ICO registration maintained; DSAR procedure documented; privacy notice published | A.5.31, A.5.34, A.5.33, A.8.12 | Mitigate | 1 | 4 | 4 | Head of Security |
| RR-011 | Customer loses their encryption key, rendering their farm data permanently unrecoverable | Customer data | C, A | 1 | 5 | 5 | Low | Acceptance rationale: key loss risk disclosed in DPA and customer documentation; customers advised to maintain secure key backups; Fenn has no technical ability to recover customer keys by design | A.8.24, A.8.13 | Accept | 1 | 5 | 5 | Head of Security |
| RR-012 | Total AWS London region failure causes platform unavailability | Platform infrastructure | A | 1 | 4 | 4 | Low | BCP defines recovery procedures for region-loss scenario (FENN-POL-006); UK-only backup held with separate provider; RTO up to 72 hours formally accepted; single-region architecture is a deliberate privacy commitment | A.8.14, A.5.29, A.5.30 | Accept | 1 | 4 | 4 | CTO |
| RR-013 | Lost or stolen laptop or mobile device exposes cached data or credentials | Employee data, Fenn systems | C | 3 | 2 | 6 | Medium | Fenn-issued laptops only; full-disk encryption required; screen lock enforced; hardware keys required for authentication; lost or stolen devices reported to IT for immediate session revocation (FENN-POL-001) | A.6.7, A.7.9, A.8.1, A.8.24 | Mitigate | 2 | 2 | 4 | Head of Security |
| RR-014 | Distributed denial-of-service attack renders the Fenn platform unavailable | Platform infrastructure | A | 3 | 3 | 9 | Medium | AWS Shield Standard (always-on, automatic); auto-scaling; monitoring and alerting via AWS; incident response plan (FENN-POL-003) | A.8.6, A.8.16, A.8.20, A.5.26 | Mitigate | 2 | 3 | 6 | CTO |

## 4. Review

This register is reviewed annually by the Head of Security. An out-of-cycle review is triggered by a significant change to Fenn's systems, operations, or threat environment, or following any security incident rated P1 or P2 under FENN-POL-003.

## 5. Related Documents

- FENN-POL-007: Risk Assessment and Treatment Methodology
- FENN-POL-001: Access Control Policy
- FENN-POL-003: Incident Response Plan
- FENN-POL-004: Vendor Risk Management Policy
- FENN-POL-005: Data Retention Policy
- FENN-POL-006: Business Continuity Plan
