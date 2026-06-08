---
title: Vendor Risk Management Policy
document_id: FENN-POL-004
version: "1.0"
effective_date: 2026-05-30
last_reviewed: 2026-05-30
next_review: 2027-05-30
owner: Jack Lowe, Head of Security
approver: Cian Kelly, CTO
scope: All third-party vendors that access, process, or store Fenn or customer data
framework_mapping:
  - ISO 27001:2022 A.5.19
  - ISO 27001:2022 A.5.20
  - ISO 27001:2022 A.5.21
  - ISO 27001:2022 A.5.22
  - ISO 27001:2022 A.5.23
  - UK GDPR Art. 28
---

# Vendor Risk Management Policy

## 1. Purpose

This policy defines how Fenn assesses, approves, and monitors third-party vendors. It ensures that vendors handling Fenn or customer data meet security and data protection standards before they are engaged, and continue to meet them for as long as the relationship lasts.

## 2. Scope

This policy applies to all third-party vendors that access, process, or store Fenn data, including customer data and internal operational data. It covers the full vendor lifecycle: assessment, onboarding, ongoing monitoring, and offboarding.

## 3. Definitions

**Vendor:** Any third-party organization that provides services to Fenn involving access to, processing of, or storage of Fenn or customer data.

**Vendor risk tiers:**

- **Critical:** Vendors that process or store customer personal data, or have access to production systems. Examples: AWS, Stripe, Sentry, JumpCloud, Plain.
- **Standard:** Vendors that process internal Fenn data or access internal systems, but do not handle customer data. Examples: Proton.
- **Low:** Vendors with no access to Fenn or customer data. Examples: office suppliers, general SaaS tools with no data integration.

Vendor risk tiers reflect operational risk to Fenn and are distinct from sub-processor status. A vendor may be Critical without being a sub-processor (e.g., JumpCloud manages employee identity but does not process customer personal data). The Sub-processor List identifies only those vendors that process customer personal data.

## 4. Policy Statements

### 4.1 Vendor Assessment

All vendors are assessed before onboarding. The depth of assessment is determined by the vendor's risk tier.

**Critical vendors** undergo a full security assessment, including review of security certifications (ISO 27001, SOC 2, or Cyber Essentials Plus), data processing practices, incident response capability, and sub-processor arrangements. Assessment findings are documented.

**Standard vendors** undergo a review of their published security practices and completion of a vendor security questionnaire. A full security assessment is not required.

**Low vendors** are approved by the Head of Security without a formal assessment where no Fenn or customer data is involved.

Critical vendors require approval from the Head of Security and the CTO. Standard vendors require approval from the Head of Security.

### 4.2 Contractual Requirements

All Critical and Standard vendors must have a written agreement in place that includes appropriate security obligations.

Where a vendor processes personal data on behalf of Fenn or Fenn's customers, a Data Processing Agreement is required in accordance with UK GDPR Art. 28. The DPA must include the following terms as required by Art. 28(3):

- Processing only on Fenn's documented instructions
- Confidentiality obligations for all personnel authorized to process the data
- Appropriate technical and organizational security measures in accordance with Art. 32
- Conditions for engaging sub-processors, including prior written authorization from Fenn
- Assistance with data subject rights requests
- Assistance with Fenn's obligations under Art. 32 to 36, including breach notification
- At the controller's choice, deletion or return of all personal data at the end of the processing relationship
- Making available all information necessary to demonstrate compliance and contributing to audits

Sub-processors are listed on the Fenn Sub-processor List and subject to the notification and objection process described in that document.

Where a vendor is located outside the United Kingdom, the assessment must confirm that an appropriate transfer mechanism is in place under UK GDPR Art. 44 to 49. Fenn's current EU-based sub-processors (Sentry, Plain) are covered by the UK's adequacy decision for the European Economic Area. Transfer adequacy is reassessed if a vendor changes its processing location or if the relevant adequacy decision is revoked or amended.

### 4.3 Ongoing Monitoring

Vendor risk is reviewed annually. Critical vendors are reviewed against their original assessment criteria. Standard and Low vendors are reviewed for any material changes in their service or data handling.

The Head of Security tracks vendor security incidents, certification lapses, or material changes disclosed by vendors between scheduled reviews. Any such event triggers an ad-hoc reassessment.

Where a vendor no longer meets Fenn's security requirements, the Head of Security determines whether remediation is possible within a defined timeframe or whether the vendor relationship should be terminated.

### 4.4 Offboarding

When a vendor relationship ends, Fenn confirms that all Fenn and customer data held by the vendor is returned or securely deleted. Confirmation is obtained through vendor attestation or certificate of destruction. Access credentials and integrations are revoked. Completion is documented.

### 4.5 Cloud Services

Fenn's production infrastructure runs on AWS. Cloud services carry specific risks that are addressed as part of the vendor assessment and ongoing monitoring process.

The assessment of cloud providers includes the shared responsibility model (the provider secures the infrastructure; Fenn secures the application, data, and configuration), data portability and exit provisions, data residency and jurisdictional requirements, and the provider's incident notification commitments.

Cloud configuration is managed by the CTO and reviewed as part of the ongoing monitoring cycle. Fenn requires the ability to extract and migrate customer data independently of the cloud provider.

### 4.6 Software Supply Chain

Fenn's platform depends on open-source libraries and third-party software components. Supply chain risk from these dependencies is managed through automated vulnerability monitoring of dependencies, prompt application of security patches for known vulnerabilities, and review of new dependencies before adoption.

These controls sit alongside vendor management and are maintained by the CTO.

## 5. Roles and Responsibilities

**Head of Security** owns this policy. Responsibilities include conducting vendor assessments, maintaining the approved vendor register, and coordinating annual reviews.

**CTO** co-approves all Critical vendor engagements and is responsible for cloud configuration and software supply chain controls.

**System owners**, as defined in the Access Control Policy, are responsible for identifying when a new vendor relationship involves Fenn or customer data and initiating the assessment process before onboarding.

**All employees and contractors** must not engage third-party vendors or tools that access Fenn or customer data without completing the assessment process defined in this policy.

## 6. Exceptions

Exceptions to this policy may be granted in writing by the Head of Security. Each exception must include a documented justification, the duration of the exception, and any compensating controls required to manage the resulting risk.

## 7. Related Documents

- Information Security Policy
- Access Control Policy
- Incident Response Plan
- Sub-processor List
- Data Retention Policy

## 8. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-05-30 | Jack Lowe, Head of Security | Initial policy. Establishes vendor risk management procedures aligned with ISO 27001:2022. |