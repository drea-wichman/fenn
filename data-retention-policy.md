---
title: Data Retention Policy
document_id: FENN-POL-005
version: "1.0"
effective_date: 2026-06-07
last_reviewed: 2026-06-07
next_review: 2027-06-07
owner: Jack Lowe, Head of Security
approver: Cian Kelly, CTO
scope: All data Fenn processes, across all systems, storage locations, and sub-processors
framework_mapping:
  - ISO 27001:2022 A.5.33
  - ISO 27001:2022 A.5.34
  - ISO 27001:2022 A.8.10
  - UK GDPR Article 5(1)(e)
  - UK GDPR Article 17
---

# Data Retention Policy

## 1. Purpose

This policy defines how long Fenn keeps data, when and how it is deleted, and who is responsible for enforcing those limits. It implements the UK GDPR storage limitation principle: personal data must not be kept longer than necessary for the purpose it was collected for. Where the law requires Fenn to keep a record for a set period, this policy records that requirement. Where the law is silent, this policy sets a defensible limit and the reason for it.

## 2. Scope

This policy applies to all data Fenn processes, in all systems and storage locations, including production systems, backups, internal tooling, and sub-processor systems. It covers customer data, corporate records, and employee data. It applies to all Fenn personnel and to any sub-processor acting on Fenn's behalf.

## 3. Definitions

**Retention period:** The maximum length of time a category of data is kept before it is deleted or anonymized.

**Retention trigger:** The event that starts the retention clock (for example, contract end, invoice date, or incident close).

**Deletion:** Permanent removal of data from production systems such that it cannot be recovered through normal operations. Data deleted from production persists in backups only until those backups age out of the rolling cycle defined in Section 5.

**Anonymization:** Irreversible removal of all information that identifies, or could identify, an individual, such that the remaining data is no longer personal data.

**Client-side encrypted data:** Farm operational data encrypted on the customer's device with customer-managed keys before it reaches Fenn. Fenn stores only ciphertext and cannot read it. Deletion of this data means deletion of the ciphertext Fenn holds.

## 4. Retention Schedule

Fenn retains each category of data for no longer than the period below. Periods marked **Legal** are fixed by statute or regulation and cannot be shortened. Periods marked **Standard** are set by Fenn and reflect operational need balanced against the storage limitation principle.

### 4.1 Customer Data

| Data category | Retention period | Trigger | Basis |
|---|---|---|---|
| Customer account & user profile (contacts, logins) | Contract term + 60 days | Contract end | Standard |
| Farm operational data (field, crop, compliance, sustainability records, client-side encrypted) | Contract term + 60-day export window, then deleted | Cancellation | Standard |
| Billing & invoice records | 6 years | Invoice date | Legal: HMRC (tax/VAT records, 6 years) |
| Support tickets (Plain) | 24 months | Ticket close | Standard |

### 4.2 Operational & Security Data

| Data category | Retention period | Trigger | Basis |
|---|---|---|---|
| Application & security audit logs | 13 months | Log creation | Standard: 12-month coverage plus overlap margin |
| Error monitoring data (Sentry) | 90 days | Capture | Standard: vendor default |
| Transactional email metadata (AWS SES) | 90 days | Send | Standard |
| Security incident records | 6 years | Incident close | Standard: aligned to Limitation Act 1980 six-year claim window |

### 4.3 Employee Data

| Data category | Retention period | Trigger | Basis |
|---|---|---|---|
| Employee records | Employment + 6 years | Employment end | Standard: aligned to Limitation Act 1980 six-year claim window |
| Payroll & tax records | 6 years | End of relevant tax year | Legal: HMRC (6 years; NMW, auto-enrolment, and holiday pay records all require 6 years) |
| Right-to-work checks | Employment + 2 years | Employment end | Legal: Home Office |
| Unsuccessful applicant data | 12 months | Application decision | Standard: conservative buffer beyond the discrimination claim limit (3 months, extending to 6 months from October 2026) |

## 5. Deletion on Cancellation

When a customer cancels, Fenn deletes their data on the following timeline:

1. **60-day grace and export window.** For 60 days after cancellation, the customer's data remains recoverable. During this window the customer may export their farm operational data. Fenn does not process the data for any purpose other than enabling export and account recovery.
2. **Permanent deletion from production.** At the end of the grace window, the customer's account data and farm operational data (ciphertext) are permanently deleted from production systems.
3. **Backup expiry.** Backups run on a rolling 30-day cycle. Deleted data ages out of all backups within 30 days of production deletion. Fenn does not selectively restore deleted customer data from backup.
4. **Confirmation of deletion.** When production deletion completes, Fenn automatically sends the customer a deletion confirmation. The confirmation records the account, the date of deletion, the categories of data removed, and notes that billing records are retained for their statutory period under Section 4.1. Confirmation is sent automatically; the customer does not need to request it.

Net effect: customer data is removed from all Fenn systems within approximately 90 days of cancellation. Billing and invoice records are the sole exception and are retained for 6 years under Section 4.1 to meet UK tax requirements.

## 6. Erasure Requests

Data subjects may request erasure of their personal data under UK GDPR Article 17. Erasure requests are handled within one month of receipt. Where Fenn is legally required to retain a record (for example, billing records under Section 4.1), that data is retained for the remainder of its statutory period and erased at the end of it; Fenn explains this to the requester. When erasure completes, Fenn automatically sends a deletion confirmation as described in Section 5. Erasure requests are routed to privacy@fenn.io.

## 7. Legal Holds

When data is subject to a legal dispute, regulatory investigation, or formal preservation request, automated and manual deletion is suspended for the affected data until the hold is lifted. The Head of Security authorizes and documents each legal hold, including the data categories affected, the reason for the hold, and the date it was placed. Legal holds override the retention schedule, including periods marked Standard. When the hold is lifted, normal retention and deletion resume.

## 8. Enforcement and Disposal

Retention periods are enforced through automated deletion wherever the system supports it. Fenn logs each deletion event, including the account, date, and categories of data removed, and retains the log as audit evidence. Where automated deletion is not available, the Head of Security maintains a scheduled manual review to identify and dispose of data that has reached the end of its retention period. Where Fenn holds data on physical media, disposal follows secure destruction by a certified provider.

Sub-processors are contractually required to delete or return Fenn data at the end of their engagement and to honor the retention periods in this schedule for data they hold on Fenn's behalf.

## 9. Roles and Responsibilities

The **Head of Security** owns this policy, maintains the retention schedule, and oversees enforcement and disposal. The **CTO** approves the policy and is accountable for the production and backup systems that enforce it. **All personnel** are responsible for not retaining data beyond its defined period in local or ad hoc storage.

## 10. Review

This policy is reviewed annually, or sooner if there is a material change to Fenn's systems, sub-processors, or legal obligations. Changes to retention periods require approval by the CTO.

## 11. Exceptions

Exceptions to this policy may be granted in writing by the Head of Security. Each exception must include a documented justification, the duration of the exception, and the data categories affected. Legal retention periods cannot be subject to exception.

## 12. Related Documents

- Information Security Policy
- Access Control Policy
- Incident Response Plan
- Vendor Risk Management Policy
- Sub-processor List
- Record of Processing Activities

## 13. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-06-07 | Jack Lowe, Head of Security | Initial policy. Establishes data retention schedule and deletion procedures aligned with ISO 27001:2022. |