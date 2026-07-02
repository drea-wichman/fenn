---
title: Risk Assessment and Treatment Methodology
document_id: FENN-POL-007
version: "1.0"
effective_date: 2026-07-01
last_reviewed: 2026-07-01
next_review: 2027-07-01
owner: Head of Security
approver: CEO
scope: All Fenn information assets, including systems, data, people, and third-party vendors
framework_mapping:
  - ISO 27001:2022 Clause 6.1.2
  - ISO 27001:2022 Clause 6.1.3
  - UK GDPR Art. 32
---

# Risk Assessment and Treatment Methodology

## 1. Purpose

This methodology defines how Fenn Agritech identifies, scores, and treats information security risks across its operations.

## 2. Scope

This methodology applies to all Fenn information assets, including systems, data, people, and third-party vendors.

## 3. Risk Identification

Fenn uses an asset-based approach to risk identification. Risks are identified by inventorying information assets and assessing the threats and vulnerabilities that apply to each. All assessments consider risks to confidentiality, integrity, and availability. Each identified risk is tagged with the CIA dimension or dimensions it affects.

Risk identification is conducted during scheduled assessments and triggered by significant changes to Fenn's systems, operations, or threat environment. Climate change has been assessed as a relevant external issue under ISO 27001:2022 Clause 4.1. The primary exposure for Fenn's ISMS is physical infrastructure resilience to extreme weather events, which is addressed under RR-012 and mitigated by AWS infrastructure controls and the Business Continuity Plan (FENN-POL-006).

## 4. Risk Analysis

Each identified risk is scored on two dimensions:

- **Likelihood:** The probability that the risk materializes. Scored 1 (very unlikely) to 5 (almost certain).
- **Impact:** The consequence to Fenn if the risk materializes. Scored 1 (negligible) to 5 (catastrophic).

Risk score = Likelihood x Impact. Scores range from 1 to 25. Impact assessment considers harm to Fenn and harm to the individuals whose personal data Fenn processes.

## 5. Risk Evaluation

Risks are evaluated against the following thresholds:

| Score | Rating | Action Required |
|---|---|---|
| 1-5 | Low | Accept |
| 6-12 | Medium | Mitigate or accept with documented justification |
| 13-25 | High | Must treat or formally accept with CEO approval |

## 6. Risk Treatment

Each risk rated Medium or High must be assigned a treatment option:

- **Mitigate:** Apply controls to reduce likelihood or impact.
- **Accept:** Document the decision and rationale. Requires CEO approval for High-rated risks.
- **Transfer:** Shift risk to a third party through contract or insurance.
- **Avoid:** Discontinue the activity that creates the risk.

All treatment decisions are recorded in the Risk Register. Selected controls are compared against ISO 27001:2022 Annex A to confirm no applicable controls are omitted. Treatment decisions feed into the Statement of Applicability.

## 7. Roles and Responsibilities

**Head of Security** owns this methodology, conducts risk assessments, and maintains the Risk Register. The Head of Security approves acceptance of Medium-rated risks.

**CEO** approves risk treatment decisions and accepts residual risk. CEO approval is required before any High-rated risk is accepted without treatment.

**Risk owners** are responsible for risks within their area of operations, approving treatment plans for those risks, and accepting residual risk within their area. High residual risk escalates to the CEO for final acceptance.

## 8. Review

This methodology is reviewed annually. An out-of-cycle review is triggered by significant changes to Fenn's systems, operations, or threat environment.