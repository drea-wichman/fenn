---
title: Statement of Applicability
document_id: FENN-SOA-001
version: "1.0"
effective_date: 2026-10-25
last_reviewed: 2026-10-25
next_review: 2027-10-25
owner: Head of Security
approver: CEO
scope: All 93 controls in ISO 27001:2022 Annex A, as they apply to Fenn's information security management system
framework_mapping:
  - ISO 27001:2022 Clause 6.1.3
---

# Statement of Applicability

## 1. Purpose

This Statement of Applicability records Fenn's decision on each of the 93 controls in ISO 27001:2022 Annex A. For each control, it states whether the control applies, why, whether it is implemented, and where it is documented. It satisfies Clause 6.1.3 d) of ISO 27001:2022.

It links Fenn's risk assessment to the controls Fenn operates. Each included control traces to a risk in the Risk Register (FENN-RSK-002), a legal or contractual requirement, or an ISO 27001 clause. Each excluded control states why it does not apply.

## 2. Scope

This document covers every control in ISO 27001:2022 Annex A, applied to the ISMS boundary defined in Scope and Context (FENN-SCP-001).

## 3. How to Read This Document

The Basis column gives the reason a control is included: a risk in the Risk Register, a legal or contractual requirement, or an ISO 27001 clause. Status is one of three values:

- **Implemented:** a published Fenn document sets out how the control is carried out.
- **Partial:** part of the control is in place, or Fenn carries it out but has not yet documented how.
- **Planned:** the control applies but is not yet in place.

Every Partial and Planned control appears in Section 5 with an owner and a target date.

## 4. Controls

### 4.1 Organizational

| Control | Applies | Basis | Status | How Fenn does it | Documents |
|---|---|---|---|---|---|
| A.5.1 Policies for information security | Yes | Clause 5.2 | Implemented | Information Security Policy at the top, topic policies below it; each approved, published, reviewed yearly; staff confirm they have read and will follow it at onboarding and after significant changes, and Fenn keeps a record | Information Security Policy 1, 4.9 |
| A.5.2 Information security roles and responsibilities | Yes | Clause 5.3 | Implemented | Defined in the Information Security Policy and in every policy's roles section | Information Security Policy 5 |
| A.5.3 Segregation of duties | Yes | RR-003, RR-008 | Implemented | Nobody approves their own access request, reviews their own access, or merges their own code without another person's review; Head of Security reports to the CEO, independent of engineering | Access Control Policy 4.3, 5; Information Security Policy 4.1 |
| A.5.4 Management responsibilities | Yes | Clause 5.1 | Implemented | Senior management accountable; all staff required to follow policy | Information Security Policy 4.1, 4.9, 4.10 |
| A.5.5 Contact with authorities | Yes | UK GDPR Article 33, RR-001 | Implemented | Incident contact list covers the ICO, the NCSC, and police cyber crime reporting; Head of Security is the data protection contact | Incident Response Plan 4.1, 5 |
| A.5.6 Contact with special interest groups | Yes | RR-001, RR-006 | Implemented | Signed up to the NCSC Early Warning service; member of at least one professional security community | Information Security Policy 4.6 |
| A.5.7 Threat intelligence | Yes | RR-001, RR-006, RR-007 | Implemented | NCSC Early Warning and advisories, vendor security bulletins, and threat detection and dependency alerts; Head of Security reviews new threats monthly and updates the risk register | Information Security Policy 4.6, Risk Register |
| A.5.8 Information security in project management | Yes | RR-005, RR-008 | Implemented | New features or projects that change how data flows get a security review from the Head of Security before building starts, and the Data Flow and Architecture document is updated; new vendors assessed before use | Information Security Policy 4.2, Vendor Risk Management Policy 4.1 |
| A.5.9 Inventory of information and other associated assets | Yes | RR-003, RR-013 | Partial | Methodology identifies risks from an asset inventory; vendor register and credentials inventory exist; no asset register | Risk Assessment and Treatment Methodology 3, Vendor Risk Management Policy 5, Access Control Policy 5 |
| A.5.10 Acceptable use of information and other associated assets | Yes | RR-003, RR-013 | Partial | Device rules; staff may not keep data beyond its retention period in local or ad hoc storage; no acceptable use policy | Access Control Policy 4.7, Data Retention Policy 9 |
| A.5.11 Return of assets | Yes | RR-003, RR-013 | Implemented | Laptops and hardware keys returned by the last working day | Access Control Policy 4.5 |
| A.5.12 Classification of information | Yes | RR-003, RR-009 | Implemented | Four levels: Restricted (farm operational data, encrypted with customer-held keys), Confidential (account data, employee data, Fenn's own records), Internal, Public | Information Security Policy 4.11 |
| A.5.13 Labelling of information | Yes | RR-009 | Implemented | Restricted data encrypted by the app with customer-held keys, readable by Fenn only in the opt-in exceptions set out in Data Flow and Architecture; Confidential and Internal documents marked; Trust Center documents marked Public | Information Security Policy 4.11 |
| A.5.14 Information transfer | Yes | RR-005, RR-015 | Implemented | Data in transit encrypted with TLS 1.3, or TLS 1.2 where 1.3 is not supported, older versions disabled; international transfer rules; connected-service data encrypted on arrival | Information Security Policy 4.4, Vendor Risk Management Policy 4.2, Scope and Context 4.3, Data Processing Agreement, Data Flow and Architecture |
| A.5.15 Access control | Yes | RR-002, RR-003, RR-004 | Implemented | Least privilege, role groups, just-in-time admin access, quarterly reviews | Access Control Policy |
| A.5.16 Identity management | Yes | RR-002, RR-003 | Implemented | One unique JumpCloud identity per person, no shared accounts, joiner, mover, leaver process | Access Control Policy 4.1, 4.5 |
| A.5.17 Authentication information | Yes | RR-002 | Implemented | Hardware keys issued and replaced through a controlled process; credential handling in onboarding training; standalone credentials tracked | Access Control Policy 4.2, 5 |
| A.5.18 Access rights | Yes | RR-003 | Implemented | Access granted by role, approved by system owners, reviewed quarterly, removed at leaving | Access Control Policy 4.3 to 4.6, 5 |
| A.5.19 Information security in supplier relationships | Yes | RR-005 | Implemented | Vendors tiered by risk and assessed before use | Vendor Risk Management Policy 3, 4.1 |
| A.5.20 Addressing information security within supplier agreements | Yes | RR-005, UK GDPR Article 28 | Implemented | Written agreements with security terms; every Article 28 term required where vendors handle personal data | Vendor Risk Management Policy 4.2 |
| A.5.21 Managing information security in the information and communication technology (ICT) supply chain | Yes | RR-006 | Implemented | Dependencies monitored for vulnerabilities, patched promptly, reviewed before adoption | Vendor Risk Management Policy 4.6 |
| A.5.22 Monitoring, review and change management of supplier services | Yes | RR-005 | Implemented | Annual vendor reviews; incidents or certification lapses trigger reassessment | Vendor Risk Management Policy 4.3 |
| A.5.23 Information security for use of cloud services | Yes | RR-004, RR-012 | Implemented | Cloud assessment covers shared responsibility, data residency, and exit; Fenn can extract customer data independently of AWS | Vendor Risk Management Policy 4.5 |
| A.5.24 Information security incident management planning and preparation | Yes | RR-001, RR-007, UK GDPR Article 33 | Implemented | Incident Commander, contacts, severity levels, annual tabletop | Incident Response Plan 3, 4.1, 6 |
| A.5.25 Assessment and decision on information security events | Yes | RR-001, RR-007 | Implemented | Head of Security assesses every report and assigns a severity | Incident Response Plan 4.3 |
| A.5.26 Response to information security incidents | Yes | RR-001, RR-007 | Implemented | Containment, eradication, and recovery steps | Incident Response Plan 4.4, 4.5 |
| A.5.27 Learning from information security incidents | Yes | RR-001 | Implemented | Post-incident review within 14 days; findings feed the risk register and policies | Incident Response Plan 4.6 |
| A.5.28 Collection of evidence | Yes | RR-001, RR-003 | Implemented | Evidence preserved before remediation; collection logged | Incident Response Plan 4.4 |
| A.5.29 Information security during disruption | Yes | RR-012 | Implemented | Security controls stay in force during recovery; farm operational data in backups stays encrypted under customer-held keys | Business Continuity Plan 5 |
| A.5.30 ICT readiness for business continuity | Yes | RR-012, RR-014 | Implemented | Recovery targets per function, multi-zone failover, yearly testing | Business Continuity Plan 4, 5, 8 |
| A.5.31 Legal, statutory, regulatory and contractual requirements | Yes | RR-010 | Implemented | Laws and interested-party requirements identified, with how each is addressed; reviewed yearly | Scope and Context 4.1, 4.2 |
| A.5.32 Intellectual property rights | Yes | Software license terms | Implemented | New dependencies checked for license terms before adoption; staff use only licensed software | Vendor Risk Management Policy 4.6 |
| A.5.33 Protection of records | Yes | RR-010 | Implemented | Retention schedule; deletion logs and legal hold records not edited; immutable backup copy | Data Retention Policy 4, 7, 8; Business Continuity Plan 5 |
| A.5.34 Privacy and protection of personal identifiable information (PII) | Yes | RR-010, UK GDPR | Partial | Data Processing Agreement, retention schedule, complaints procedure, and data flow document in place; no privacy notice, record of processing activities, or subject access procedure | Data Processing Agreement, Data Retention Policy, Data Protection Complaints Procedure, Data Flow and Architecture |
| A.5.35 Independent review of information security | Yes | Clause 9.2 | Planned | Not yet implemented | To be developed |
| A.5.36 Compliance with policies, rules and standards for information security | Yes | Clause 9.2, RR-003 | Partial | Quarterly access reviews and yearly policy reviews; no compliance checking process | Access Control Policy 4.6 |
| A.5.37 Documented operating procedures | Yes | RR-003, RR-012 | Implemented | Incident, continuity, and complaints procedures published; operating procedures such as the offboarding checklist and break-glass procedure kept in Fenn's internal knowledge base for the staff who need them | Incident Response Plan, Business Continuity Plan, Data Protection Complaints Procedure, Access Control Policy 5 |

### 4.2 People

| Control | Applies | Basis | Status | How Fenn does it | Documents |
|---|---|---|---|---|---|
| A.6.1 Screening | Yes | RR-003, RR-017, Home Office right-to-work rules | Partial | Everyone: right to work, references, employment history. Privileged admin group: basic DBS check, judged only against convictions relevant to the role, results deleted after the decision, starting once the appropriate policy document for criminal offense data is in place | Access Control Policy 4.5, Data Retention Policy 4.3 |
| A.6.2 Terms and conditions of employment | Yes | RR-003 | Implemented | Employment and contractor contracts require following Fenn's security policies and carry confidentiality obligations | Information Security Policy 4.9, Access Control Policy 4.5 |
| A.6.3 Information security awareness, education and training | Yes | RR-001, RR-002, RR-008 | Implemented | Role-based training at onboarding and ongoing | Information Security Policy 4.9 |
| A.6.4 Disciplinary process | Yes | RR-003 | Implemented | Policy breaches handled under Fenn's disciplinary procedure, which follows the Acas Code of Practice; outcomes up to dismissal | Information Security Policy 4.10 |
| A.6.5 Responsibilities after termination or change of employment | Yes | RR-003 | Implemented | Confidentiality continues after leaving and is confirmed at offboarding | Access Control Policy 4.5 |
| A.6.6 Confidentiality or non-disclosure agreements | Yes | UK GDPR Article 28(3)(b), RR-003 | Implemented | Staff contracts carry a confidentiality clause; contractors sign a confidentiality agreement before access, reviewed at each annual policy review; vendors bound through their contracts | Access Control Policy 4.5, Vendor Risk Management Policy 4.2, Data Processing Agreement |
| A.6.7 Remote working | Yes | RR-013 | Implemented | Fenn-issued laptops for all system access; personal phones limited to email, calendar, and chat; encryption, screen lock, lost devices reported | Access Control Policy 4.7 |
| A.6.8 Information security event reporting | Yes | UK GDPR Article 33, RR-001 | Implemented | Staff report to the Head of Security; no penalty for good-faith reports | Incident Response Plan 4.2 |

### 4.3 Physical

| Control | Applies | Basis | Status | How Fenn does it | Documents |
|---|---|---|---|---|---|
| A.7.1 Physical security perimeters | Yes | RR-018 | Implemented | Data centers: AWS. Office: badge entry, building reception and CCTV through the landlord | AWS ISO 27001 certification, Vendor Risk Management Policy 4.5, Access Control Policy 4.8 |
| A.7.2 Physical entry | Yes | RR-018 | Implemented | Data centers: AWS. Office: badge entry; visitors signed in and escorted | AWS ISO 27001 certification, Access Control Policy 4.8 |
| A.7.3 Securing offices, rooms and facilities | Yes | RR-018 | Implemented | Office: badge entry, locked network cupboard with IT-only access, visitors escorted | Access Control Policy 4.8 |
| A.7.4 Physical security monitoring | Yes | RR-018 | Implemented | Data centers: AWS. Office: badge entry and building CCTV through the landlord | AWS ISO 27001 certification, Access Control Policy 4.8 |
| A.7.5 Protecting against physical and environmental threats | Yes | RR-012 | Implemented | AWS protects its data centers; Fenn plans for total London region loss; if the office is unusable, staff work remotely on Fenn-issued laptops | AWS ISO 27001 certification, Business Continuity Plan |
| A.7.6 Working in secure areas | Yes | RR-018 | Implemented | Only IT enters the office network cupboard, for maintenance; it stays locked when not in use | Access Control Policy 4.8 |
| A.7.7 Clear desk and clear screen | Yes | RR-003, RR-013, RR-018 | Implemented | Screen lock enforced; no customer or account data left visible or unattended | Access Control Policy 4.7, 4.8 |
| A.7.8 Equipment siting and protection | Yes | RR-018 | Implemented | Data centers: AWS. Office network equipment in a locked cupboard with IT-only access | AWS ISO 27001 certification, Access Control Policy 4.8 |
| A.7.9 Security of assets off-premises | Yes | RR-013 | Implemented | Fenn-issued laptops for all system access; personal phones limited to email, calendar, and chat; encryption, screen lock, lost devices reported | Access Control Policy 4.7 |
| A.7.10 Storage media | Yes | RR-013 | Implemented | Laptop disks encrypted; USB storage blocked on Fenn laptops through device management; physical media destroyed by a certified provider | Access Control Policy 4.7, Data Retention Policy 8 |
| A.7.11 Supporting utilities | Yes | RR-012 | Implemented | AWS provides power and cooling resilience; production does not depend on the office | AWS ISO 27001 certification, Business Continuity Plan |
| A.7.12 Cabling security | Yes | RR-018 | Implemented | Data centers: AWS. Office network equipment and cabling in a locked cupboard | AWS ISO 27001 certification, Access Control Policy 4.8 |
| A.7.13 Equipment maintenance | Yes | RR-001 | Implemented | Laptops kept on current OS updates; IT keeps office network equipment updated | Access Control Policy 4.7, 4.8 |
| A.7.14 Secure disposal or re-use of equipment | Yes | RR-003, RR-013 | Implemented | Laptops returned at leaving and wiped before reuse; physical media destroyed by a certified provider | Access Control Policy 4.5, Data Retention Policy 8 |

### 4.4 Technological

| Control | Applies | Basis | Status | How Fenn does it | Documents |
|---|---|---|---|---|---|
| A.8.1 User end point devices | Yes | RR-013 | Implemented | Laptops encrypted, screen-locked, kept updated; personal phones must meet the same baseline, checked through a work profile before they can reach Fenn email, calendar, or chat | Access Control Policy 4.7 |
| A.8.2 Privileged access rights | Yes | RR-002, RR-003, RR-004 | Implemented | Small standing admin group plus just-in-time access, all sessions logged, reviewed quarterly | Access Control Policy 4.4, 4.6 |
| A.8.3 Information access restriction | Yes | RR-003, RR-007, RR-009 | Implemented | Least privilege through role groups; farm operational data encrypted with customer-held keys; staff not permitted to access forecast data | Access Control Policy 4.3, 4.4; Data Flow and Architecture |
| A.8.4 Access to source code | Yes | RR-006, RR-008 | Implemented | Write access to code repositories limited to engineering, behind SSO; repository access included in quarterly access reviews | Access Control Policy 4.1, 4.3, 4.6 |
| A.8.5 Secure authentication | Yes | RR-002 | Implemented | Staff: SSO with hardware keys, no SMS or app codes. Customers: password plus required two-factor by authenticator app or passkey, no SMS | Access Control Policy 4.1, 4.2, 4.9 |
| A.8.6 Capacity management | Yes | RR-014 | Implemented | Auto-scaling; AWS alerts when usage nears limits; capacity reviewed before autumn drilling, spring crop protection, and summer harvest | Business Continuity Plan 4, 5; Risk Register |
| A.8.7 Protection against malware | Yes | RR-001 | Implemented | Every Fenn laptop runs endpoint detection and response, managed by IT, with alerts to the Head of Security; security training | Access Control Policy 4.7, Information Security Policy 4.9 |
| A.8.8 Management of technical vulnerabilities | Yes | RR-001, RR-006, RR-007 | Implemented | Dependency monitoring; critical and high-risk updates applied within 14 days of release, matching Cyber Essentials; independent penetration testing | Vendor Risk Management Policy 4.1, 4.6 |
| A.8.9 Configuration management | Yes | RR-004 | Partial | CTO manages cloud configuration; reviewed against CIS benchmarks; no baseline written down | Vendor Risk Management Policy 4.5, Risk Register |
| A.8.10 Information deletion | Yes | RR-010, RR-016 | Implemented | Retention schedule with automated deletion and deletion logs; forecast inputs deleted when forecasts finish | Data Retention Policy 4, 8; Data Processing Agreement |
| A.8.11 Data masking | Yes | RR-009 | Implemented | Farm operational data removed from error reports before they reach Sentry | Data Processing Agreement, Data Flow and Architecture |
| A.8.12 Data leakage prevention | Yes | RR-003, RR-009 | Partial | Fenn holds farm operational data only as ciphertext, readable only for the opt-in features set out in Data Flow and Architecture; account data protected by least privilege and logging; staff may not keep data beyond its retention period in local or ad hoc storage; USB storage blocked; no data leakage prevention tool by design; personal email rule not yet written | Data Flow and Architecture, Access Control Policy 4.3, 4.7, Data Retention Policy 9 |
| A.8.13 Information backup | Yes | RR-001, RR-012 | Implemented | 30-day rolling backups, one-hour recovery point, second UK copy with object lock, restore tested quarterly | Business Continuity Plan 5, Incident Response Plan 4.1 |
| A.8.14 Redundancy of information processing facilities | Yes | RR-012 | Implemented | Multiple availability zones in London with automatic failover | Business Continuity Plan 5 |
| A.8.15 Logging | Yes | RR-003, RR-007, RR-015, RR-016 | Implemented | Privileged sessions and access logged, kept 13 months; logs sent to a separate AWS account with write-once storage that admins of production systems cannot change or delete; Head of Security reviews privileged-session logs monthly | Access Control Policy 4.4, Data Retention Policy 4.2 |
| A.8.16 Monitoring activities | Yes | RR-001, RR-007, RR-014 | Implemented | Alerts from AWS, Sentry, and JumpCloud feed incident detection | Incident Response Plan 4.2 |
| A.8.17 Clock synchronization | Yes | RR-003, RR-007 | Implemented | Production systems sync to the Amazon Time Sync Service; staff devices use their operating system's network time; logs record time in UTC | Access Control Policy 4.4 |
| A.8.18 Use of privileged utility programs | Yes | RR-003, RR-004 | Implemented | Admin tools that can bypass normal controls limited to the admin group or just-in-time access, and their use is logged | Access Control Policy 4.4 |
| A.8.19 Installation of software on operational systems | Yes | RR-006, RR-008 | Partial | Production changes pass code review and staging; no written procedure for installing software on production systems | Risk Register |
| A.8.20 Networks security | Yes | RR-004, RR-014, RR-018 | Partial | Cloud network architecture reviewed; AWS Shield against attacks; office network untrusted | Risk Register, Access Control Policy 4.8 |
| A.8.21 Security of network services | Yes | RR-004, RR-014 | Partial | AWS assessed under the shared responsibility model; AWS Shield always on | Vendor Risk Management Policy 4.5, Risk Register |
| A.8.22 Segregation of networks | Yes | RR-004, RR-018 | Partial | Office network has no direct route to production; segregation within production not documented | Access Control Policy 4.8, Risk Register |
| A.8.23 Web filtering | Yes | RR-001, RR-002 | Implemented | Fenn laptops use DNS filtering, through device management, to block known malicious sites | Access Control Policy 4.7 |
| A.8.24 Use of cryptography | Yes | RR-011, RR-013, RR-015, RR-017 | Partial | Farm operational data encrypted on device with customer-held keys; a key per data category, replaced when access is removed; laptop disk encryption; integration secrets encrypted; TLS 1.3 or 1.2 in transit; Fenn's own key management not documented | Information Security Policy 4.4, Data Flow and Architecture 4, Access Control Policy 4.7, Risk Register |
| A.8.25 Secure development life cycle | Yes | RR-006, RR-008 | Partial | Code review, staging, automated security testing, new dependencies reviewed before adoption | Risk Register, Vendor Risk Management Policy 4.6 |
| A.8.26 Application security requirements | Yes | RR-007, RR-015 | Partial | Authentication on every API endpoint; customer two-factor required; incoming data validated; read-only integration access where possible; no written security requirements for new features | Access Control Policy 4.9, Risk Register |
| A.8.27 Secure system architecture and engineering principles | Yes | RR-011, RR-016, RR-017 | Partial | Zero access by default, exceptions opt-in and limited, published to customers; no written engineering principles | Data Flow and Architecture, Scope and Context 4.1 |
| A.8.28 Secure coding | Yes | RR-008 | Partial | Secure development training; mandatory code review | Risk Register |
| A.8.29 Security testing in development and acceptance | Yes | RR-006, RR-007, RR-008 | Partial | Automated security testing in the deployment pipeline; independent penetration testing at least yearly and after major changes | Risk Register, Vendor Risk Management Policy 4.1 |
| A.8.30 Outsourced development | No | N/A | N/A | Excluded: Fenn develops its software in-house; contractors work as Fenn personnel under Fenn's access controls | N/A |
| A.8.31 Separation of development, test and production environments | Yes | RR-008, RR-009 | Partial | Staging required before production; production data never used in development or testing | Access Control Policy 3, Risk Register |
| A.8.32 Change management | Yes | RR-004, RR-008 | Partial | Code review and staging before production; no change management policy | Risk Register |
| A.8.33 Test information | Yes | RR-009 | Partial | Production data never used in development or testing | Risk Register |
| A.8.34 Protection of information systems during audit testing | Yes | RR-007 | Implemented | Penetration tests by an independent CREST-accredited firm, at least yearly and after major changes, scoped and scheduled in advance with the CTO and Head of Security, run against staging where possible, written approval needed for production; customer audits need advance notice and must not unreasonably disrupt operations | Vendor Risk Management Policy 4.1, Data Processing Agreement |

## 5. Risk Treatment Plan

This section is Fenn's risk treatment plan under Clause 6.1.3 e). Each document below completes the Partial and Planned controls listed against it.

| Document | Controls | Owner | Target |
|---|---|---|---|
| Asset Management Policy and Asset Register | A.5.9 | Head of Security | Q1 2027 |
| Appropriate Policy Document for criminal record checks | A.6.1 | Head of Security | Q1 2027 |
| Change Management Policy | A.8.32 | CTO | Q1 2027 |
| Infrastructure Security Standard | A.8.9, A.8.20, A.8.21, A.8.22, A.8.24 | CTO | Q1 2027 |
| Secure Development Policy | A.8.19, A.8.25, A.8.26, A.8.27, A.8.28, A.8.29, A.8.31, A.8.33 | CTO | Q2 2027 |
| Acceptable Use Policy | A.5.10, A.8.12 | Head of Security | Q2 2027 |
| Internal Audit Procedure | A.5.35, A.5.36 | Head of Security | Q2 2027 |
| Privacy Notice, Record of Processing Activities, and Subject Access Procedure | A.5.34 | Head of Security | Q2 2027 |

Approved by the risk owners (Head of Security and CTO) and the CEO on 2026-10-25.

## 6. Review

This document is reviewed annually, and whenever a new or updated Fenn document changes the status of a control.

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
- FENN-SCP-001: Scope and Context
- Data Processing Agreement
- Data Flow and Architecture

## 8. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-10-25 | Jack Lowe, Head of Security | Initial Statement of Applicability. Records Fenn's decision on all 93 Annex A controls and its risk treatment plan. |
