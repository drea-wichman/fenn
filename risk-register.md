---
title: Risk Register
document_id: FENN-RSK-002
version: "1.1"
effective_date: 2026-07-01
last_reviewed: 2026-10-22
next_review: 2027-07-01
owner: Head of Security
approver: CEO
scope: All Fenn information assets, including systems, data, people, and third-party vendors
framework_mapping:
  - ISO 27001:2022 Clause 6.1.2
  - ISO 27001:2022 Clause 6.1.3
  - ISO 27001:2022 Clause 8.2
  - ISO 27001:2022 Clause 8.3
  - UK GDPR Article 32
---

# Risk Register

## 1. Purpose

This register records the information security risks identified through Fenn's risk assessment process. It documents each risk's scoring, treatment decision, and assigned owner. It is the primary evidence that Fenn has assessed and is managing its information security risks in accordance with ISO 27001:2022 and UK GDPR Article 32.

## 2. How to Read This Register

Risks are scored using the methodology defined in FENN-RSK-001. Likelihood and impact are each rated 1 to 5. Risk score equals likelihood multiplied by impact. Scores of 1 to 5 are Low, 6 to 12 are Medium, and 13 to 25 are High. Inherent risk is the score before controls are applied. Residual risk is the score after controls are applied.

## 3. Risk Register

| ID | Risk | Asset | CIA | Inh. L | Inh. I | Inh. Score | Rating | Controls | Annex A | Treatment | Res. L | Res. I | Res. Score | Owner |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RR-001 | Ransomware or destructive malware encrypts or destroys Fenn infrastructure | Platform infrastructure, customer data | C, I, A | 3 | 5 | 15 | High | Endpoint detection and response on all devices; immutable, encrypted backups; incident response plan (FENN-PLN-001); security awareness training; patch management | A.8.7, A.8.8, A.8.13, A.8.16, A.5.26, A.6.3 | Mitigate | 2 | 5 | 10 | Head of Security |
| RR-002 | Phishing or social engineering leads to credential compromise | Employee accounts, Fenn systems | C, I | 4 | 3 | 12 | Medium | Hardware security keys (Nitrokey 3) required for all staff; JumpCloud SSO; phishing awareness training; privileged access controls (FENN-POL-001) | A.8.5, A.5.16, A.5.17, A.6.3, A.5.15, A.8.2 | Mitigate | 2 | 3 | 6 | Head of Security |
| RR-003 | Insider threat: employee or contractor accesses or exfiltrates data without authorization | Customer data, employee data, Fenn systems | C, I | 2 | 4 | 8 | Medium | Least privilege access; JIT privileged access; quarterly access reviews; all privileged sessions logged; JML process; staff not permitted to access data processed for opt-in features (FENN-POL-001) | A.5.15, A.8.2, A.8.5, A.8.15, A.5.18, A.6.5 | Mitigate | 1 | 4 | 4 | Head of Security |
| RR-004 | Cloud misconfiguration exposes Fenn systems or customer data | AWS infrastructure, customer data | C, A | 3 | 4 | 12 | Medium | AWS configuration reviewed against CIS benchmarks; IAM least privilege enforced; VPC architecture reviewed; changes follow documented change management process | A.8.9, A.5.15, A.8.20, A.5.23, A.8.2, A.8.32 | Mitigate | 2 | 4 | 8 | CTO |
| RR-005 | Sub-processor breach exposes data Fenn has shared with a third-party vendor | Customer data, employee data | C | 2 | 4 | 8 | Medium | Vendor risk tiering (FENN-POL-003); DPAs in place with all sub-processors; sub-processor list maintained; contractual security requirements; right to audit | A.5.19, A.5.20, A.5.22, A.5.31 | Mitigate | 1 | 4 | 4 | Head of Security |
| RR-006 | Software supply chain compromise introduces malicious code via a dependency or package | Platform infrastructure, customer data | C, I, A | 3 | 4 | 12 | Medium | Dependency scanning; Dependabot alerts enabled; code review required before merge; software bill of materials maintained | A.5.21, A.8.8, A.8.25, A.8.29 | Mitigate | 2 | 4 | 8 | CTO |
| RR-007 | API authentication bypass allows unauthorized access to the Fenn platform | Platform infrastructure, customer data, employee data | C, I, A | 3 | 5 | 15 | High | API authentication enforced on all endpoints; penetration testing; access logging via AWS CloudTrail; threat detection via Amazon GuardDuty; application error alerting via Sentry; incident response plan (FENN-PLN-001) | A.8.5, A.8.3, A.8.16, A.5.26, A.8.8, A.8.15 | Mitigate | 2 | 5 | 10 | CTO |
| RR-008 | Insecure code deployed to production introduces exploitable vulnerability | Platform infrastructure, customer data | C, I, A | 3 | 4 | 12 | Medium | Mandatory code review; staging environment required before production deployment; automated security testing in CI/CD pipeline; secure development training | A.8.25, A.8.28, A.8.29, A.8.31, A.6.3 | Mitigate | 2 | 4 | 8 | CTO |
| RR-009 | Accidental data exposure during development or support activity | Customer data, employee data | C | 2 | 4 | 8 | Medium | Production data not used in development or testing environments; support access granted JIT and logged; access revoked on ticket close; farm operational data removed from error reports before they are sent to Sentry | A.8.3, A.5.15, A.8.33, A.8.2, A.8.15, A.8.11 | Mitigate | 1 | 4 | 4 | Head of Security |
| RR-010 | UK GDPR non-compliance leads to ICO investigation or enforcement action | Customer data, employee data | C | 2 | 4 | 8 | Medium | Data retention policy (FENN-POL-004); DPA in place for all processor relationships; ICO registration maintained | A.5.31, A.5.34, A.5.33, A.8.10 | Mitigate | 1 | 4 | 4 | Head of Security |
| RR-011 | Customer loses their encryption key, rendering their farm data permanently unrecoverable | Customer data | A | 5 | 5 | 25 | High | Recovery key created for every account; optional co-owner holding every key; signup acknowledgment and in-app reminder that a lost key without a recovery key or co-owner means lost data; Fenn holds no copy of customer keys by design | A.8.24 | Mitigate | 3 | 5 | 15 | Head of Security |
| RR-012 | Total AWS London region failure causes platform unavailability | Platform infrastructure | A | 1 | 4 | 4 | Low | BCP defines recovery procedures for region-loss scenario (FENN-PLN-002); UK-only backup held with separate provider; RTO up to 72 hours formally accepted; single-region architecture is a deliberate privacy commitment | A.8.14, A.5.29, A.5.30, A.8.13 | Accept | 1 | 4 | 4 | CTO |
| RR-013 | Lost or stolen laptop or mobile device exposes cached data or credentials | Employee data, Fenn systems | C | 3 | 2 | 6 | Medium | Fenn-issued laptops only; full-disk encryption required; screen lock enforced; hardware keys required for authentication; lost or stolen devices reported to IT for immediate session revocation (FENN-POL-001) | A.6.7, A.7.9, A.8.1, A.8.24 | Mitigate | 2 | 2 | 4 | Head of Security |
| RR-014 | Distributed denial-of-service attack renders the Fenn platform unavailable | Platform infrastructure | A | 3 | 3 | 9 | Medium | AWS Shield Standard (always-on, automatic); auto-scaling; monitoring and alerting via AWS; incident response plan (FENN-PLN-001) | A.8.6, A.8.16, A.8.20, A.5.26 | Mitigate | 2 | 3 | 6 | CTO |
| RR-015 | Stolen integration access exposes customer data held by connected services, or a compromised connected service sends malicious data to Fenn | Integration access, customer data | C, I | 3 | 4 | 12 | Medium | Integration access stored encrypted in a secrets manager; read-only access where the service allows it; disconnecting a service revokes access; integration activity logged; incoming data validated before processing | A.5.14, A.5.17, A.8.3, A.8.15, A.8.24, A.8.26 | Mitigate | 2 | 4 | 8 | CTO |
| RR-016 | Forecast data is exposed while readable on Fenn's servers during yield forecasting | Customer data | C | 2 | 3 | 6 | Medium | Opt-in only; servers process only the data the forecast requires; inputs deleted when the forecast completes; staff not permitted to access forecast data; privileged sessions logged (FENN-POL-001) | A.8.2, A.8.3, A.8.10, A.8.15 | Mitigate | 1 | 3 | 3 | CTO |
| RR-017 | Fenn, or an attacker in Fenn's systems, delivers a substituted public key and reads data shared with team members | Customer data | C | 2 | 4 | 8 | Medium | Key delivery restricted to authenticated app sessions; privileged access to key-delivery systems limited and logged (FENN-POL-001); limit disclosed to customers in the Data Flow and Architecture document. Acceptance rationale: no customer-side key verification exists yet | A.8.2, A.8.5, A.8.24 | Accept | 2 | 4 | 8 | Head of Security |

## 4. Risk Acceptance

Residual risk is accepted under the criteria in FENN-RSK-001. The risk owner accepts Low residual risk. The risk owner accepts Medium residual risk with Head of Security approval. The CEO accepts High residual risk.

| ID | Residual Score | Rating | Accepted By | Date |
|---|---|---|---|---|
| RR-001 | 10 | Medium | Head of Security | 2026-10-22 |
| RR-002 | 6 | Medium | Head of Security | 2026-10-22 |
| RR-003 | 4 | Low | Head of Security | 2026-10-22 |
| RR-004 | 8 | Medium | CTO, approved by Head of Security | 2026-10-22 |
| RR-005 | 4 | Low | Head of Security | 2026-10-22 |
| RR-006 | 8 | Medium | CTO, approved by Head of Security | 2026-10-22 |
| RR-007 | 10 | Medium | CTO, approved by Head of Security | 2026-10-22 |
| RR-008 | 8 | Medium | CTO, approved by Head of Security | 2026-10-22 |
| RR-009 | 4 | Low | Head of Security | 2026-10-22 |
| RR-010 | 4 | Low | Head of Security | 2026-10-22 |
| RR-011 | 15 | High | CEO | 2026-10-22 |
| RR-012 | 4 | Low | CTO | 2026-10-22 |
| RR-013 | 4 | Low | Head of Security | 2026-10-22 |
| RR-014 | 6 | Medium | CTO, approved by Head of Security | 2026-10-22 |
| RR-015 | 8 | Medium | CTO, approved by Head of Security | 2026-10-22 |
| RR-016 | 3 | Low | CTO | 2026-10-22 |
| RR-017 | 8 | Medium | CEO | 2026-10-22 |

## 5. Review

This register is reviewed annually by the Head of Security. An out-of-cycle review is triggered by a significant change to Fenn's systems, operations, or threat environment, or following any security incident rated P1 or P2 under FENN-PLN-001.

## 6. Related Documents

- FENN-POL-001: Access Control Policy
- FENN-POL-003: Vendor Risk Management Policy
- FENN-POL-004: Data Retention Policy
- FENN-PLN-001: Incident Response Plan
- FENN-PLN-002: Business Continuity Plan
- FENN-RSK-001: Risk Assessment and Treatment Methodology
- Sub-processor List

## 7. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-07-01 | Jack Lowe, Head of Security | Initial register. |
| 1.1 | 2026-10-22 | Jack Lowe, Head of Security | Re-rated RR-011, corrected residual impact scores, added risk acceptance, and added RR-015 to RR-017. Includes earlier corrections to the RR-011 classification and document ID. |
