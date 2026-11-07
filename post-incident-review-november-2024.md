---
title: "Post-Incident Review: November 2024"
document_id: FENN-RPT-001
version: "1.0"
effective_date: 2026-11-07
last_reviewed: 2026-11-07
next_review: 2027-11-07
owner: Head of Security
approver: CEO
scope: Review of the November 2024 exposure of a Fenn access key through a sub-processor breach, Fenn's response, and the resulting changes to Fenn's information security management system
framework_mapping:
  - ISO 27001:2022 Clause 10.2
  - ISO 27001:2022 A.5.27
  - UK GDPR Article 33
---

# Post-Incident Review: November 2024

## 1. Summary

In November 2024, a sub-processor that delivered data from customers' farm equipment into Fenn's platform was breached. An access key Fenn had issued to that provider was stolen in the breach. On 5 November 2024, the key was used to copy account data and encrypted farm operational data from Fenn's cloud storage. The copied data covered all 603 of Fenn's customers at the time and 2,214 user accounts. The account data consisted of users' names and email addresses. The farm operational data was encrypted with customer-held keys and could not be read.

Fenn learned of the incident on 13 November 2024, when the provider notified it, nine days after the provider discovered its own breach. Fenn revoked the key and notified every customer the same day. Fenn ended its contract with the provider and replaced it with direct connections to each equipment manufacturer. Automatic equipment data sync was paused from 13 November 2024 until those connections went live in February 2025. No equipment records were lost.

This review found six gaps. Three were in Fenn's security: the access key Fenn issued to the provider had no expiry date, Fenn had no alerts on access to its own storage, and Fenn depended on the provider to learn of the breach. Two were in how the response was run (Section 7). One remains today: Fenn's Incident Response Plan has not yet been tested. Section 8 sets out how each gap is now addressed.

## 2. About this review

At the time of the incident, Fenn's security rested on its product architecture and a baseline set of controls. Farm operational data was encrypted with customer-held keys, access keys were limited to what each service needed, and access logging was on across Fenn's systems. Fenn's baseline controls followed the Cyber Essentials requirements, and it had a founding security policy owned by the CTO. It did not yet have a formal information security management system, Incident Response Plan, or Head of Security. These were introduced in 2026.

The CTO led the response and investigated using Fenn's access logs. Fenn engaged an external forensic firm, which independently reviewed the logs and confirmed the CTO's findings. Fenn made changes in early 2025, but no formal post-incident review was written at the time.

This review was conducted retrospectively under Section 4.6 of the Incident Response Plan (FENN-PLN-001), so that the incident's lessons are recorded and its actions tracked within the information security management system. It draws on the access log entries the CTO preserved at the time, Fenn's notifications to customers, its correspondence with the provider, and interviews with the CTO.

This published version omits technical details that could help an attacker, such as system names and network addresses. The full technical record is held internally as a security incident record under the Data Retention Policy (FENN-POL-004).

## 3. Timeline

Times are UK time (GMT).

| Date | What happened |
|---|---|
| Mar 2022 | Fenn issues the provider an access key, with no expiry date, when the integration goes live. |
| Mon 4 Nov 2024 | The provider discovers it has been breached, according to its later notice to Fenn. |
| Tue 5 Nov 2024 | Automated tools use the stolen key to copy account data and encrypted farm operational data from Fenn's cloud storage. This is the attacker's only use of the key. |
| Wed 13 Nov 2024, 09:42 | The provider notifies Fenn by email. |
| Wed 13 Nov 2024, 10:31 | Fenn revokes the key, pausing automatic equipment sync. The CTO begins reviewing Fenn's access logs. |
| Wed 13 Nov 2024, 17:05 | Fenn emails all customers and gives the provider notice to end the contract. |
| Thu 14 Nov 2024 | The log review confirms which files were copied. Fenn engages an external forensic firm to review the logs independently, and reports the theft of the key to Action Fraud. |
| Fri 15 Nov 2024 | Fenn sends a second email to all customers, after legal review. |
| Fri 6 Dec 2024 | The forensic firm reports. It confirms the CTO's findings and finds no further access and no evidence that any data was decrypted. |
| Fri 13 Dec 2024 | The contract with the provider ends, terminated for the security breach with no exit fee. Fenn sends a closing email to all customers. |
| Mon 3 Feb 2025 | The first direct connections to equipment manufacturers go live, meeting Fenn's commitment to restore sync before spring field work. |
| By end Feb 2025 | The remaining direct connections go live. |

Eight days passed between the copy and Fenn learning of it.

## 4. What was affected

**Account data.** Names and email addresses for 2,214 user accounts, covering all 603 customers at the time. These were the accounts of farmers and the people they had invited to their farm's account.

**Farm operational data.** Customers' farm operational data files in Fenn's storage were copied. The files were encrypted with keys held by customers, which Fenn does not hold. The attacker could not read them, and the forensic firm found no evidence that any were decrypted.

**Availability.** Revoking the key stopped automatic equipment sync for all customers from 13 November 2024. Equipment data remained in each manufacturer's platform throughout. When customers approved Fenn's new direct connection to each manufacturer, the missing data filled in automatically. No equipment records were lost.

**Not affected.** The key could not reach passwords or billing details, and Fenn does not hold payment card details. No customer data was changed. The provider passed equipment data to Fenn without storing it, as Fenn had confirmed before engaging it, and the provider's notice confirmed that it held no Fenn customer data.

## 5. Root cause

In March 2022, Fenn engaged the provider to deliver equipment data into its platform. Before signing, Fenn reviewed the provider's security practices and agreed a contract with UK GDPR processor terms, including a commitment to notify Fenn of a breach without undue delay. Fenn issued the provider an access key limited to the parts of its storage the integration needed: farm operational data files, and the account records used to match equipment data to the right farm. Those account records held users' names and email addresses alongside each farm's account number.

The key had no expiry date. Fenn knew long-lived keys should be rotated, and introducing expiry was planned, but the work had not been scheduled and the risk was not formally recorded. The key remained valid for two years and eight months. Industry baselines such as the CIS AWS Foundations Benchmark recommend rotating access keys at least every 90 days.

The provider was breached in a wide attack that was not aimed at Fenn. Fenn's key was among the credentials stolen. On 5 November 2024, the attacker's automated tools used the key to copy the data it could reach.

Two further gaps meant Fenn did not detect the copy itself:

- **No alerting.** Fenn's cloud access logs recorded every action taken with the key, including the copy. The logs were kept for investigation, but nothing watched them, so the activity raised no alert.
- **Dependence on the provider.** Fenn's only route to learning of the breach was the provider's notice. The contract required notice without undue delay but set no fixed deadline. The provider notified Fenn nine days after discovering its own breach.

The key's limited access contained the damage, and the lack of alerting delayed Fenn's response by eight days. Fenn's logs show when the key was used, not when it was copied from the provider's systems, so a regularly rotated key may still have been valid when it was used. The lack of expiry remains a gap: a key that never expires stays usable by anyone who copies it, for as long as it exists.

## 6. Notification

Fenn processed all of the affected data on its customers' behalf. Under UK GDPR Article 33(2), a processor must notify the controller without undue delay after becoming aware of a personal data breach. Fenn notified every customer on 13 November 2024, the day it became aware.

Each customer, as controller, was responsible for deciding whether to report the breach to the Information Commissioner's Office (now the Information Commission) under Article 33(1) and whether to inform the people affected under Article 34. Fenn's notices gave customers what they needed to decide:

- **13 November.** What had happened, the approximate number of accounts involved, that the key had been revoked and equipment sync paused, and that Fenn was still investigating. Fenn committed to restoring sync before spring field work.
- **15 November.** After the log review and legal review: Fenn's findings on scope, which an external forensic firm was independently reviewing; that farm operational data had been copied but was encrypted with keys Fenn does not hold (relevant to Article 34(3)(a)); and that the main risk to users was scam emails using their names and email addresses.
- **13 December.** That the forensic firm had confirmed Fenn's findings, that the contract with the provider had ended, and that Fenn was building direct connections to each equipment manufacturer.

Fenn sent every notice to all customers. No customer was singled out.

None of Fenn's own records were involved, so Fenn had no report of its own to make to the regulator. Fenn reported the theft of its access key to Action Fraud (now Report Fraud), the national fraud and cyber crime reporting service, on 14 November 2024. The Network and Information Systems Regulations 2018 did not apply: Fenn was a small enterprise at the time and exempt.

## 7. How the response went

**What went well**

- **Containment was fast.** Fenn revoked the key 49 minutes after the provider's notice. The attacker had used the key once, eight days earlier, and never used it again.
- **Customers heard first from Fenn, the same day.** The first notice went out before the investigation was complete and said so. Every later notice went to all customers, and the second followed legal review.
- **The logs answered the key questions.** Because access logging was on, the CTO confirmed exactly what was copied within a day, and the forensic firm confirmed those findings independently.
- **The architecture held.** The copied farm operational data was encrypted with customer-held keys and could not be read.
- **Fenn met its commitment.** Equipment sync was restored before spring field work, as promised in the first notice, and no equipment records were lost.
- **Fenn acted beyond the affected provider.** In early 2025, Fenn replaced every other key held by outside services as a precaution and turned on threat detection for its cloud environment.

**What went wrong**

- **The response depended on one person.** With no written plan, the CTO led the investigation, customer notices, legal review, and the provider contract at once. Decisions were sound, but roles and steps were worked out on the day.
- **Outside support was arranged under pressure.** Fenn had no pre-agreed forensic firm or documented legal contacts, so both were arranged during the incident.

## 8. Gaps and actions

Each action has an owner and is tracked by the Head of Security under Section 4.6 of the Incident Response Plan.

| Gap | Action | Owner | Status |
|---|---|---|---|
| Key had no expiry date | Replace every key held by outside services | CTO | Implemented, early 2025 |
| | Require systems and vendors to use temporary credentials where supported, and rotate any long-lived access key at least every 90 days (Access Control Policy) | Head of Security | Implemented, November 2026 |
| | Record the risk of a vendor-held key being stolen in a vendor's breach (Risk Register, RR-019) | Head of Security | Implemented, November 2026 |
| No alerts on access to storage | Turn on threat detection for Fenn's cloud environment, with alerts feeding incident detection | CTO | Implemented, early 2025 |
| Dependence on the provider | Require Critical vendors to notify Fenn of a breach within 48 hours, with any exception recorded and reviewed yearly (Vendor Risk Management Policy 4.2) | Head of Security | Implemented, November 2026 |
| | Replace every key a vendor holds on the day it reports a breach (Vendor Risk Management Policy 4.3) | Head of Security | Implemented, November 2026 |
| Response depended on one person | Assign incident roles, led by an Incident Commander (Incident Response Plan) | Head of Security | Implemented, May 2026 |
| Outside support arranged under pressure | Document legal and forensic contacts and verify them yearly (Incident Response Plan 4.1) | Head of Security | Implemented, May 2026 |
| Response not yet tested | Test the Incident Response Plan with a tabletop exercise based on a supplier breach | Head of Security | Planned, Q1 2027 |

Fenn also set a 48-hour limit on its own notice to customers (Data Processing Agreement).

## 9. Related Documents

- FENN-POL-001: Access Control Policy
- FENN-POL-003: Vendor Risk Management Policy
- FENN-POL-004: Data Retention Policy
- FENN-PLN-001: Incident Response Plan
- FENN-RSK-002: Risk Register
- Data Processing Agreement

## 10. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-11-07 | Jack Lowe, Head of Security | Initial review. Records the November 2024 sub-processor credential exposure, Fenn's response, and the resulting actions. |
