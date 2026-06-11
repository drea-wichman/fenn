---
title: Business Continuity Plan
document_id: FENN-POL-006
version: "1.0"
effective_date: 2026-06-10
last_reviewed: 2026-06-10
next_review: 2027-06-10
owner: Jack Lowe, Head of Security
approver: Cian Kelly, CTO
scope: Fenn's critical business functions and the systems, data, sub-processors, and personnel required to recover them during a disruption
framework_mapping:
  - ISO 27001:2022 A.5.29
  - ISO 27001:2022 A.5.30
  - ISO 27001:2022 A.8.13
  - ISO 27001:2022 A.8.14
  - UK GDPR Article 32
---

# Business Continuity Plan

## 1. Purpose

This plan defines how Fenn keeps its critical business functions running, or recovers them, during a disruption. It sets a recovery target for each critical function, describes how Fenn meets those targets, and assigns responsibility for activating and directing the response. Fenn recovers customer data within the United Kingdom and as ciphertext under customer-managed keys, so continuity does not come at the cost of data residency or confidentiality.

## 2. Scope

This plan applies to the systems, data, sub-processors, and personnel required to deliver and recover Fenn's critical business functions. It covers disruptions of any cause, including security incidents, infrastructure and third-party outages, and loss of access to people or facilities. It applies to all Fenn personnel involved in continuity and recovery.

## 3. Definitions

**Critical business function:** A function whose disruption would quickly cause unacceptable operational, regulatory, financial, or reputational harm.

**Business Impact Analysis (BIA):** The assessment that identifies Fenn's critical business functions and sets a recovery target for each, based on the impact of its disruption.

**Recovery Time Objective (RTO):** The maximum acceptable time to restore a function after a disruption begins.

**Recovery Point Objective (RPO):** The maximum acceptable amount of data loss in a disruption, expressed as a length of time (for example, one hour of data).

**Continuity event:** A disruption that threatens a critical business function or a recovery target, triggering activation of this plan.

## 4. Business Impact Analysis

The Business Impact Analysis identifies Fenn's critical business functions, sets a recovery target for each, and records the impact of disruption.

**Critical functions and recovery targets**

| Function | Tier | RTO | RPO |
|---|---|---|---|
| Platform availability | 1 | 4 hours | Not applicable (data resides in the data store) |
| Customer data store and backups | 1 | 8 hours | 1 hour |
| Data capture | 1 | 12 hours | 24 hours |
| Authentication | 1 | 4 hours | Not applicable |
| Customer support and incident communication | 2 (1 during an incident) | 2 hours | Not applicable |
| Billing | 3 | 48 hours | Not applicable (Stripe holds the record) |

**Dependencies**

| Function | Key dependencies |
|---|---|
| Platform availability | AWS London, JumpCloud, the customer data store |
| Customer data store and backups | AWS storage, the backup system, customer-managed keys |
| Data capture | Equipment manufacturer platforms, weather services, field sensors, AWS |
| Authentication | JumpCloud |
| Customer support and incident communication | Plain, the independently hosted status page, AWS SES |
| Billing | Stripe |

Several critical functions depend on third parties, including AWS, JumpCloud, the equipment manufacturer platforms, Plain, and Stripe. Fenn's recovery time for those functions is therefore bound in part by the recovery of the provider, not by Fenn alone. Vendor obligations and service levels are governed by the Vendor Risk Management Policy (FENN-POL-004).

One dependency lies outside Fenn's recovery entirely: the customer's encryption key. Because Fenn holds only ciphertext, a customer who loses their key cannot have their data restored by Fenn. This is a direct consequence of the customer-managed-key architecture and sets a boundary on what Fenn can recover.

**Impact**

When a Tier 1 function is unavailable, the primary impact is operational: customers lose real-time access to their records and cannot confirm field activity as it happens. Because data is captured at source, the records are not lost and backfill on recovery, so the impact is loss of live access rather than permanent data loss. Secondary impacts are financial (service credits and churn) and reputational. Tier 3 functions such as billing carry financial and administrative impact only, with no operational consequence within their recovery window.

**Seasonality**

Impact severity varies with the agricultural calendar. An outage costs most during autumn drilling (roughly mid-September to mid-October), the spring and early-summer crop protection windows, and the summer harvest, when field activity is intense and time-critical. UK professional pesticide users must record each application by product, timing, dose, area, and crop, and retain those records for at least three years. An outage during a spray window blocks the farmer's real-time logging at the point the law requires a record. The same outage in winter matters far less, so Fenn escalates incidents faster during high-activity windows.

## 5. Recovery Strategy

This section describes how Fenn meets the recovery targets set in the Business Impact Analysis.

**Infrastructure resilience**

Fenn's production systems run across multiple availability zones within the AWS London region. The loss of a single zone fails over to the remaining zones automatically, with no customer action required. This covers the realistic range of infrastructure failures and meets the recovery targets for platform availability.

Fenn does not fail over outside the United Kingdom. AWS operates a single UK region, so cross-region failover would place customer data in another country and conflict with Fenn's data residency commitment. The complete loss of the AWS London region is therefore treated as a low-likelihood, high-impact event, recovered from the independent UK backup rather than by automatic failover. Recovery in that case has a target of 72 hours, longer than the standard targets, a tradeoff Fenn accepts to keep customer data in the UK.

**Backup and restoration**

Fenn retains backups on a rolling 30-day cycle, consistent with the Data Retention Policy. Continuous backup with point-in-time recovery meets a one-hour recovery point objective for the primary store, so the maximum data loss in a normal restore is the most recent hour.

Backups contain only ciphertext, encrypted under customer-managed keys before the data reaches Fenn. Fenn cannot read backup contents, so a compromise of any backup store does not expose customer data. Fenn holds backups in the AWS London region and in a second, independent UK location with a separate provider. The independent copy is written with object-lock immutability, so it cannot be altered or deleted from Fenn's production environment, which protects it against both a regional outage and a ransomware event. The independent copy is refreshed daily, so recovery from it carries a recovery point objective of 24 hours. Captured data backfills from source on recovery, which reduces the data actually lost in that scenario.

**Data capture**

Fenn's data capture draws from external sources: equipment manufacturer platforms, weather services, and field sensors. When capture is disrupted, those sources retain their own data. On recovery, Fenn backfills the missed period from source, so the gap delays records rather than losing data. This meets the 24-hour recovery point objective for data capture.

**Authentication**

Authentication depends on JumpCloud, an external identity provider. Fenn monitors JumpCloud availability and relies on its service commitments for recovery. Fenn maintains a break-glass administrative account, used only when JumpCloud is unavailable, so recovery is not blocked by a dependency outside Fenn's control.

**Customer communication**

Fenn hosts its status page independently of its production infrastructure, so it stays available to give customers incident updates during an outage that affects Fenn's own systems.

## 6. Activation and Roles

**Activation**

The Incident Commander activates this plan when a disruption threatens a critical business function or puts a recovery target at risk, typically a P1 incident under the Incident Response Plan affecting a function identified in the Business Impact Analysis.

Activation does not depend on the cause. A continuity event may be a security incident, a third-party or infrastructure outage, or any other disruption that affects a critical function. The test is the impact on critical functions, not the nature of the cause.

**Relationship to the Incident Response Plan**

Where a disruption is also a security incident, this plan and the Incident Response Plan (FENN-POL-003) run in parallel. The Incident Response Plan governs the security response; this plan governs the continuity and recovery of critical functions. A single Incident Commander directs both, so the plans coordinate rather than compete.

**Roles**

- **Incident Commander.** Declares activation, directs the response, and owns recovery decisions and external communication. This is the same role defined in the Incident Response Plan.
- **Technical recovery lead.** Executes recovery, including failover and restoration from backup. Sits with engineering under the CTO.
- **Communications lead.** Manages customer updates and the status page during a disruption. The Incident Commander may delegate this role.

For major continuity events, the Incident Commander informs the CEO, who holds overall accountability for the company's response.

The Incident Commander ensures each role has a designated alternate, so the response does not depend on any single person being available.

## 7. Communication

**Internal coordination**

During a continuity event, the response team coordinates through a designated primary channel. Fenn maintains an out-of-band fallback that does not depend on its production systems, so the team can keep coordinating if the primary channel is caught in the disruption.

**Customer updates**

Fenn communicates with customers through its independently hosted status page. During an active major incident, Fenn posts an initial notice once the disruption is confirmed and updates at least every 60 minutes until service is restored. Fenn issues a resolution notice when service returns, and a short summary after significant events.

**Scope of this section**

This section covers operational communication only: service status and expected recovery. Where a disruption also involves a personal data breach, legal and contractual notification is governed by the Incident Response Plan (FENN-POL-003).

## 8. Training and Testing

Fenn tests this plan at planned intervals and at least once per year.

**Backup restoration testing**

Fenn tests that backups restore successfully at planned intervals and at least once per year, including from the independent UK copy as well as the primary store. Testing confirms the recovery point objectives can be met in practice.

**Plan exercises**

The response team conducts exercises that simulate a continuity event, validating the plan, the recovery procedures, and the assigned roles. Fenn records the findings and uses them to update the plan.

**Training**

Fenn trains response team members on their responsibilities under this plan.

## 9. Plan Maintenance and Review

The Head of Security owns this plan and reviews it at planned intervals and at least once per year.

Fenn also reviews the plan after any activation, after a significant change to its systems, vendors, or critical functions, and after an exercise that identifies gaps. The Business Impact Analysis is reviewed on the same cycle and triggers, since it sets the targets the rest of the plan depends on. Fenn records material changes in the revision history.

## 10. Related Documents

- Information Security Policy
- Incident Response Plan
- Vendor Risk Management Policy
- Data Retention Policy

## 11. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-06-10 | Jack Lowe, Head of Security | Initial plan. Establishes critical business functions, recovery targets, and continuity procedures aligned with ISO 27001:2022. |