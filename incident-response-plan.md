---
title: Incident Response Plan
document_id: FENN-POL-003
version: "1.0"
effective_date: 2026-05-30
last_reviewed: 2026-05-30
next_review: 2027-05-30
owner: Jack Lowe, Head of Security
approver: Cian Kelly, CTO
scope: All Fenn employees, contractors, and third-party integrations
framework_mapping:
  - ISO 27001:2022 A.5.24
  - ISO 27001:2022 A.5.25
  - ISO 27001:2022 A.5.26
  - ISO 27001:2022 A.5.27
  - ISO 27001:2022 A.5.28
  - ISO 27001:2022 A.6.8
  - UK GDPR Art. 33
  - UK GDPR Art. 34
---

# Incident Response Plan

## 1. Purpose

This plan defines how Fenn identifies, responds to, and recovers from security incidents. It ensures that when something goes wrong, the right people know what to do, decisions get made quickly, and Fenn meets its legal obligations, including the UK GDPR requirement to notify the ICO within 72 hours of becoming aware of a personal data breach.

## 2. Scope

This plan applies to all Fenn systems, employees, contractors, and third-party integrations. It covers security incidents of any kind, including personal data breaches, unauthorized access, ransomware, and service disruptions caused by a security event.

## 3. Definitions

**Security incident:** Any event that threatens the confidentiality, integrity, or availability of Fenn systems, data, or services.

**Personal data breach:** A security incident involving the accidental or unlawful destruction, loss, alteration, unauthorized disclosure of, or access to personal data. Personal data breaches are a subset of security incidents and trigger additional obligations under UK GDPR.

**Incident Commander:** The individual responsible for leading Fenn's response to a security incident. At Fenn, this role is held by the Head of Security. In the absence of the Head of Security, the CTO assumes command.

**Severity levels:**

- **P1 (Critical):** Active attack, confirmed data breach, ransomware, or customer data exposed. Full response activated. External legal counsel notified. Where personal data is affected, the ICO 72-hour notification clock starts.
- **P2 (Significant):** Suspected breach or unauthorized access under active investigation. Scope not yet confirmed. Head of Security leads, CTO informed. Monitored for escalation to P1.
- **P3 (Low):** Contained, low-impact event. No personal data involved. Handled by the Head of Security, logged, reviewed at the next scheduled security review.

## 4. Incident Response Phases

### 4.1 Preparation

The following must be maintained at all times:

- Incident response contacts are documented and current, including the Head of Security, the CTO, and external legal counsel
- Contact details for external legal counsel and an external forensic provider are documented alongside internal contacts and verified at each annual review
- All staff know how to report a suspected incident and who to contact
- Backups are tested quarterly and confirmed restorable
- This plan is reviewed annually and after every P1 incident
- The incident response plan is tested through a tabletop exercise at least annually

All staff report suspected incidents directly to the Head of Security. In the absence of the Head of Security, reports go to the CTO.

### 4.2 Detection and Reporting

Incidents may be detected through automated monitoring, including alerts from AWS, Sentry, or JumpCloud, or reported by any employee or contractor who suspects a security issue.

Anyone who suspects an incident must report it to the Head of Security immediately. Do not wait for certainty. A suspected incident that turns out to be a false alarm is preferable to a delayed report.

No employee or contractor will face penalty for reporting a suspected incident in good faith, including reports that turn out to be false alarms.

Third parties and sub-processors report incidents affecting Fenn data to the Head of Security via the contact details specified in their data processing agreement.

For out-of-hours reporting, the Head of Security is contactable by phone. The contact number is maintained in the incident response contact list.

Reports should include, where possible:

- What was observed and when
- Which systems or data may be affected
- Any actions already taken

All reports are logged upon receipt.

### 4.3 Assessment

Upon receiving a report, the Head of Security assesses the incident and assigns an initial severity level based on the definitions in section 3.

Assessment should establish, as far as immediately possible:

- Whether personal data has been or may have been affected
- Which systems and data are involved
- The likely cause and current status

**If personal data is involved, the 72-hour ICO notification clock starts immediately.** It does not wait for the investigation to be complete.

Severity may be revised as the investigation develops. A P2 incident escalates to P1 if personal data exposure is confirmed or an active threat is identified.

The CTO is notified of all P1 and P2 incidents at the point of assessment.

### 4.4 Containment

The Incident Commander coordinates containment actions to limit the spread and impact of the incident. Containment is prioritized over investigation; stopping ongoing damage takes precedence over establishing root cause.

Containment actions depend on the nature of the incident and may include:

- Revoking compromised accounts or sessions via JumpCloud
- Isolating affected systems from the network
- Suspending compromised API keys or third-party integrations
- Preserving logs and evidence before any remediation steps

Evidence preservation is mandatory. No affected system should be wiped, rebuilt, or modified before logs and relevant data have been secured.

The Incident Commander designates who collects evidence on a per-incident basis. All evidence is handled to preserve its integrity for regulatory, legal, or disciplinary use:

- Record what was collected, by whom, and when
- Store evidence securely with access limited to the response team
- Log any access to or transfer of evidence

Where forensic analysis exceeds Fenn's internal capability, the Head of Security engages an external provider.

All containment actions are documented in real time.

### 4.5 Eradication and Recovery

Once containment is confirmed, the Incident Commander coordinates eradication of the threat and recovery of affected systems.

Eradication actions may include:

- Removing malicious code or unauthorized access points
- Patching the vulnerability or misconfiguration that enabled the incident
- Resetting compromised credentials and revoking associated sessions

Recovery actions may include:

- Restoring systems or data from verified clean backups
- Rebuilding affected infrastructure where necessary
- Confirming system integrity before returning to production

Systems are not returned to production until the Incident Commander confirms eradication is complete. Speed of recovery does not take precedence over confirmed safety.

### 4.6 Post-Incident Review

A post-incident review is conducted after every P1 and P2 incident, and after any P3 incident that reveals a systemic issue.

The review is led by the Head of Security and must be completed within 14 days of incident closure. It covers:

- A timeline of events from detection to resolution
- Root cause analysis
- Assessment of whether the response was effective
- Identified gaps in controls, processes, or documentation
- Recommended actions with assigned owners and deadlines

Findings are documented and retained. Recommended actions are tracked to completion by the Head of Security.

This plan is updated if the review identifies gaps in the response procedures. Findings are also reviewed for impact on the risk register, related policies, and training requirements.

Incident records are retained in accordance with the Data Retention Policy.

## 5. Notification

Fenn's notification obligations depend on its role in relation to the data affected.

Fenn is not required to appoint a Data Protection Officer under UK GDPR Art. 37. Fenn is not a public authority, its core activities do not involve large-scale regular and systematic monitoring of individuals, and it does not process special category or criminal offense data at scale. The Head of Security serves as Fenn's designated data protection contact point for regulatory correspondence and data subject inquiries.

**Where Fenn is a processor** (customer data processed on behalf of Fenn's customers): Fenn notifies the affected customer without undue delay. The customer, as controller, determines whether to notify the ICO and affected data subjects. Fenn supports the customer's notification obligations by providing all relevant details of the breach.

**Where Fenn is a controller** (employee data, recruitment data, business contacts): The Head of Security consults external legal counsel and determines whether notification to the ICO is required. Where required, notification is submitted as soon as practicable and no later than 72 hours after Fenn becomes aware of the breach, even if the investigation is still in progress. Supplementary information is provided as it becomes available.

Not all personal data breaches require ICO notification. Notification is required where the breach is likely to result in a risk to the rights and freedoms of the affected individuals. External legal counsel supports this assessment.

ICO notifications must include, as required by Art. 33(3):

- The nature of the breach, including the categories and approximate number of data subjects and records affected
- The name and contact details of the data protection contact point
- The likely consequences of the breach
- The measures taken or proposed to address the breach and mitigate its effects

Where information is not yet available at the time of notification, it is provided in phases as the investigation develops.

**Data subject notification.** Where Fenn is the controller and a breach is likely to result in a high risk to the rights and freedoms of affected individuals, Fenn notifies those individuals directly and without undue delay. The notification describes the nature of the breach, the likely consequences, the measures Fenn has taken in response, and a contact point for further information. Where customer data encrypted with customer-managed keys is involved, the Art. 34(3)(a) exemption may apply if the encryption renders the data unintelligible to any unauthorized party. External legal counsel advises on this assessment.

**External communications.** External communications beyond regulatory and data subject notification are authorized by the CEO.

All notification decisions and their rationale are documented and retained.

## 6. Roles and Responsibilities

**Head of Security** owns this plan and serves as Incident Commander. Responsibilities include leading the response to all security incidents, coordinating containment and recovery, determining whether ICO notification is required, and ensuring post-incident reviews are completed. The Head of Security also serves as Fenn's designated data protection contact point.

**CTO** approves this plan and is notified of all P1 and P2 incidents. Assumes the Incident Commander role in the absence of the Head of Security.

**External legal counsel** is consulted on all notification decisions involving personal data breaches, including ICO notification thresholds and customer communication requirements.

**CEO** authorizes external communications beyond regulatory and data subject notification.

**All employees and contractors** are responsible for reporting suspected security incidents to the Head of Security immediately and cooperating with any investigation.

## 7. Exceptions

Exceptions to this plan may be granted in writing by the Head of Security. Each exception must include a documented justification, the duration of the exception, and any compensating controls required to manage the resulting risk.

## 8. Related Documents

- Information Security Policy
- Access Control Policy
- Sub-processor List
- Data Retention Policy
- Vendor Risk Management Policy

## 9. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-05-30 | Jack Lowe, Head of Security | Initial plan. Establishes incident response procedures aligned with ISO 27001:2022. |