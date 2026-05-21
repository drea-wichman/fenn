---
title: Information Security Policy
document_id: FENN-POL-002
version: "1.0"
effective_date: 2026-05-20
last_reviewed: 2026-05-20
next_review: 2027-05-20
owner: Jack Lowe, Head of Security
approver: Zoe Cooper-Hartley, CEO
scope: All Fenn employees, contractors, and third parties with access to Fenn systems, information, and facilities
framework_mapping:
  - ISO 27001:2022 Clause 5.1
  - ISO 27001:2022 Clause 5.2
  - ISO 27001:2022 Clause 5.3
  - ISO 27001:2022 Clause 6.1
  - ISO 27001:2022 Clause 7.2
  - ISO 27001:2022 Clause 7.3
  - ISO 27001:2022 Clause 10
  - UK GDPR
  - Data Protection Act 2018
---

# Information Security Policy

## 1. Purpose

This policy establishes Fenn Agritech's commitment to protecting the confidentiality, integrity, and availability of the information it holds, and defines the Information Security Management System (ISMS) through which that commitment is delivered. As a provider of crop and field management software to UK farms, Fenn processes operational and personal data on behalf of its customers. Protecting that data is fundamental to Fenn's obligations to its customers and under UK data protection law.

This policy sits at the top of Fenn's information security policy hierarchy; all other security policies and procedures derive from it. It commits Fenn to meeting applicable legal, regulatory, and contractual requirements and to the continual improvement of its ISMS, which is aligned with ISO 27001:2022. Annex A controls are mapped in Fenn's subordinate policies and Statement of Applicability. This policy is communicated to all Fenn employees and contractors and is made available to interested parties as appropriate.

## 2. Scope

This policy applies to all Fenn employees, contractors, and third parties with access to Fenn systems, information, and facilities. It covers all information Fenn holds or processes, the systems and applications used to deliver the Fenn platform, internal tools and corporate systems, and the people and processes that support them.

Customer data processed through the Fenn platform is encrypted with customer-managed keys. Fenn has no technical ability to access customer data in plaintext. The security of customer-side controls, including customer account management and customer key management, is the responsibility of the customer and falls outside the boundary of Fenn's ISMS. This policy governs Fenn's own systems, people, and handling of information; it does not govern actions taken by customers within their own accounts.

## 3. Definitions

**Information Security Management System (ISMS):** The framework of policies, procedures, roles, and controls Fenn uses to manage information security risk and protect the information it holds.

**Information asset:** Any information or system that has value to Fenn and requires protection, including customer data, business data, source code, credentials, and the systems that store or process them.

**Customer data:** Data uploaded to or generated within the Fenn platform by a customer. Customer data is encrypted with customer-managed keys and cannot be accessed by Fenn in plaintext.

## 4. Policy Statements

### 4.1 Leadership and Governance

Fenn's senior management is accountable for information security. Leadership establishes this policy, sets the direction of the ISMS, and provides the resources needed to operate and improve it. Information security objectives are set in line with Fenn's business goals and reviewed by management at planned intervals.

The Head of Security is responsible for the day-to-day operation of the ISMS, including maintaining policies, coordinating risk management, and reporting on security to senior management.

### 4.2 Risk Management

Fenn manages information security through a risk-based approach. Risks to the confidentiality, integrity, and availability of Fenn's information are identified, assessed, and treated on an ongoing basis. Risk assessments consider the likelihood and impact of each risk, and treatment decisions are documented and assigned to an owner.

Risks are reviewed regularly and after significant changes to Fenn's systems, operations, or threat environment.

### 4.3 Access Control

Access to Fenn systems, applications, and data is granted on the principle of least privilege. Individuals receive only the access required for their role. Access is authenticated, authorized, logged, and reviewed, and is revoked promptly when no longer required.

### 4.4 Cryptography

Fenn protects information using strong, industry-standard cryptography. Customer data is encrypted with customer-managed keys, and Fenn does not hold the means to decrypt it. Cryptographic controls are reviewed as standards and threats evolve.

### 4.5 Supplier and Third-Party Security

Fenn assesses the security of suppliers and third parties before granting them access to Fenn systems or data, and monitors them throughout the relationship. Sub-processors that handle customer data are subject to contractual data protection obligations and are disclosed to customers.

### 4.6 Incident Management

Fenn maintains the capability to detect, report, and respond to information security incidents. Incidents are recorded, assessed for severity, and managed through to resolution. Where an incident involves personal data, Fenn meets its breach notification obligations under UK data protection law, including notification to the Information Commissioner's Office where required. Where Fenn acts as a processor for customer data, Fenn notifies the relevant controller without undue delay.

### 4.7 Business Continuity

Fenn maintains plans to continue operating and to recover its services in the event of disruption. Continuity and recovery arrangements are documented, assigned to owners, and tested at planned intervals to confirm they remain effective.

### 4.8 Data Protection

Fenn processes personal data in accordance with UK GDPR and the Data Protection Act 2018. Personal data is collected for specified purposes, held only as long as necessary, and protected by appropriate technical and organizational measures. Fenn respects the rights of data subjects and supports its customers in meeting their own data protection obligations.

### 4.9 Information Security Awareness

All Fenn employees and contractors receive information security training appropriate to their role, both at onboarding and on an ongoing basis. Everyone with access to Fenn systems is responsible for understanding and following this policy and for reporting security concerns promptly.

### 4.10 Compliance

Fenn complies with applicable legal, regulatory, and contractual requirements relating to information security and data protection. Its primary regulator is the Information Commissioner's Office. Compliance obligations are reviewed as the legal and regulatory environment changes. Breach of this policy may result in disciplinary action up to and including termination of employment, and termination of contract for contractors.

## 5. Roles and Responsibilities

**Senior management** owns the ISMS, approves this policy, provides resources, and reviews information security at planned intervals.

**Head of Security** is responsible for the day-to-day operation of the ISMS, including maintaining policies, coordinating risk management, overseeing incident response, and reporting to senior management.

**System owners** are accountable for the security of the systems and data they own, including access decisions and participation in risk and access reviews.

**All employees and contractors** are responsible for following this policy, completing required training, protecting the information and systems they use, and reporting security concerns promptly.

## 6. Exceptions

Exceptions to this policy may be granted in writing by the Head of Security. Each exception must include a documented justification, the duration of the exception, and any compensating controls required to manage the resulting risk. Exceptions are reviewed at planned intervals and removed when no longer required.

## 7. Related Documents

- Access Control Policy
- Sub-processor List
- Data Processing Agreement
- Incident Response Plan
- Vendor Risk Management Policy
- Data Retention Policy
- Business Continuity Plan
- Cryptography Policy
- Risk Register

## 8. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-05-20 | Jack Lowe, Head of Security | Initial version. Establishes Fenn's top-level information security policy and ISMS commitment. |
