---
title: Scope and Context
document_id: FENN-SCP-001
version: "1.0"
effective_date: 2026-08-25
last_reviewed: 2026-08-25
next_review: 2027-08-25
owner: Head of Security
approver: CEO
scope: The boundaries, context, and interested parties of Fenn's information security management system
framework_mapping:
  - ISO 27001:2022 Clause 4.1
  - ISO 27001:2022 Clause 4.2
  - ISO 27001:2022 Clause 4.3
  - ISO 27001:2022 Clause 4.4
  - ISO 27001:2022 Amendment 1:2024
---

# Scope and Context

## 1. Purpose

This document defines the context, interested parties, and scope of Fenn Agritech's information security management system (ISMS). It establishes the boundary of the ISMS, the internal and external issues that shape it, and the parties whose requirements it must meet. It provides the foundation on which Fenn's risk assessment, controls, and supporting policies are built, satisfying Clause 4 of ISO 27001:2022.

## 2. Application

This document applies to the whole of Fenn's ISMS. It is reviewed annually and after any significant change to Fenn's systems, services, or organization, because the context and scope it defines determine the boundaries of every other document in the ISMS.

## 3. Definitions

**Information Security Management System (ISMS):** The framework of policies, procedures, roles, and controls Fenn uses to manage information security risk and protect the information it holds.

**Interested party:** Any individual or organization that can affect, be affected by, or perceive itself to be affected by Fenn's information security.

**Interface:** A point at which Fenn's systems or activities connect to those of another organization, such as an API, a data exchange, or a service dependency.

**Dependency:** A process, system, or service outside the ISMS boundary that Fenn relies on to operate.

## 4. Context of the Organization

### 4.1 Internal and External Issues

Fenn has determined the internal and external issues relevant to its information security management system and their bearing on its ability to protect the information it holds. These issues are reviewed annually and inform Fenn's risk assessment under the Risk Assessment and Treatment Methodology.

**External issues**

| Issue | Relevance to information security | Type |
|---|---|---|
| UK data protection law (UK GDPR and Data Protection Act 2018, as amended by the Data (Use and Access) Act 2025), regulated by the ICO | Sets Fenn's obligations as controller and processor; ongoing reform means compliance requirements continue to evolve | Risk |
| Privacy-first market position built on client-side encryption and customer-managed keys | Commits Fenn to holding no ability to read customer data, defining the ISMS boundary | Opportunity |
| Regulatory drivers in agriculture (Agriculture Act 2020, Defra digital record-keeping) | Customers rely on Fenn for compliance records they must legally keep, raising availability and integrity stakes | Risk |
| Dependence on AWS (single UK region) and third-party equipment-manufacturer APIs | Concentrates operational risk in few providers and constrains disaster recovery to the UK | Risk |
| Climate change | Extreme weather threatens the physical resilience of infrastructure Fenn depends on, addressed through AWS infrastructure controls and the Business Continuity Plan | Risk |

**Internal issues**

| Issue | Relevance to information security | Type |
|---|---|---|
| Zero-access architecture (customer data encrypted with customer-managed keys before it reaches Fenn) | Removes Fenn's ability to access customer data in plaintext, setting the boundary of what Fenn can protect and recover | Opportunity |
| Series B stage (closed October 2025) and rapid organizational growth | Growth can outpace security process maturity, increasing the risk of informal or inconsistent controls | Risk |
| Concentrated internal tooling (Proton) | Simplifies oversight but increases reliance on a single provider for email, calendar, file storage, and password management | Risk |
| Prior sub-processor credential exposure (November 2024) | Shapes Fenn's emphasis on vendor risk management and access control | Risk |

### 4.2 Interested Parties

Fenn has identified the interested parties relevant to its information security management system, their requirements, and which of those requirements are addressed through the ISMS.

| Interested party | Requirements relevant to information security | Addressed through the ISMS |
|---|---|---|
| Customers (crop farms in England and Wales) | Confidentiality and integrity of farm operational data; data sovereignty through customer-managed keys; availability of the platform during key periods in the farming calendar; support for their own data protection obligations | Addressed through the Information Security Policy (Cryptography), the Access Control Policy, the Business Continuity Plan, and the Data Processing Agreement. |
| Information Commissioner's Office (ICO) | Compliance with UK GDPR and the Data Protection Act 2018, as amended by the Data (Use and Access) Act 2025; lawful processing; breach notification within statutory timeframes; a complaints procedure accessible to data subjects | Addressed through the Information Security Policy, the Incident Response Plan, the Data Retention Policy, and the Data Protection Complaints Procedure. |
| Employees and contractors | Protection of their personal and employment data; clear security responsibilities; a safe and lawful working environment | Addressed through the Information Security Policy, the Access Control Policy, and the Data Retention Policy. |
| Sub-processors and suppliers | Clear contractual security and data protection obligations; defined processing instructions; incident notification arrangements | Addressed through the Vendor Risk Management Policy, the Data Processing Agreement, and the Sub-processor List. |
| Company leadership and investors | Protection of Fenn's reputation and commercial interests; regulatory compliance; continuity of the platform; evidence of security maturity to support growth, and progress toward ISO 27001 and Cyber Essentials Plus certification | Addressed through the ISMS as a whole. |

Fenn has considered whether its interested parties have requirements related to climate change, in accordance with ISO 27001:2022 Amendment 1:2024. At the time of this assessment, no interested party has imposed climate-specific information security requirements on Fenn. This determination will be reviewed alongside the interested parties table at each annual review.

### 4.3 Scope of the ISMS

The ISMS applies to the development, operation, and support of the Fenn platform, a crop and field management SaaS product serving approximately 1,000 commercial farms across England and Wales, and to the information, systems, people, and processes that support it. Fenn employs approximately 100 people.

**In scope**

- The Fenn platform and its supporting production infrastructure, hosted on Amazon Web Services in the London region
- Internal corporate systems and tools used to operate the business, including the Proton suite used for internal collaboration
- All Fenn employees and contractors, working from Fenn's Bristol office and remotely on Fenn-issued devices
- All information Fenn holds or processes, including customer account data, employee data, corporate records, and the ciphertext of customer farm operational data
- The management of Fenn's interfaces with third-party providers and sub-processors, including cloud infrastructure, payment processing, and equipment-manufacturer APIs

**Out of scope**

- Customer-side controls, including customer account management and customer key management. Farm operational data is encrypted with customer-managed keys before it reaches Fenn, and Fenn has no technical ability to access it in plaintext. Security of the customer's own environment and key management is the responsibility of the customer.
- The internal operations of third-party providers and sub-processors. Fenn manages these as interfaces and dependencies through its Vendor Risk Management Policy, but the providers' own internal security controls fall outside Fenn's ISMS.

**Boundaries and dependencies**

Fenn's ISMS boundary is defined by what Fenn controls. Where Fenn depends on third parties (AWS for infrastructure, JumpCloud for identity, sub-processors for supporting services), those providers' internal controls sit outside the ISMS, but the security of the interface, including access credentials, contractual obligations, and data protection terms, is within scope and governed by the Vendor Risk Management Policy.

One sub-processor processes customer personal data in the European Economic Area (Sentry in Frankfurt). This transfer of customer personal data is a restricted transfer under UK GDPR and is permitted under the UK's adequacy regulations for the EEA. Transfer arrangements are governed by the Vendor Risk Management Policy and reassessed if a sub-processor's location or the relevant adequacy regulations change.

## 5. Information Security Management System

Fenn establishes, implements, maintains, and continually improves an information security management system in accordance with ISO 27001:2022. The ISMS covers the scope defined in Section 4.3 and is governed by the Information Security Policy, supported by the policies, plans, procedures, and records that implement it.

Responsibility for the ISMS sits with Fenn's senior management. The Head of Security is responsible for its day-to-day operation, and information security objectives, risks, and performance are reviewed at planned intervals.

## 6. Review

This document is reviewed annually, and after any significant change to Fenn's systems, services, organization, or the legal and regulatory environment in which it operates.

## 7. Related Documents

- FENN-POL-001: Access Control Policy
- FENN-POL-002: Information Security Policy
- FENN-POL-003: Vendor Risk Management Policy
- FENN-POL-004: Data Retention Policy
- FENN-PLN-001: Incident Response Plan
- FENN-PLN-002: Business Continuity Plan
- FENN-PRO-001: Data Protection Complaints Procedure
- FENN-RSK-001: Risk Assessment and Treatment Methodology
- FENN-RSK-002: Risk Register
- Data Processing Agreement
- Sub-processor List

## 8. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-08-25 | Jack Lowe, Head of Security | Initial version. Establishes the context, interested parties, and scope of Fenn's ISMS in line with ISO 27001:2022 Clause 4. |
