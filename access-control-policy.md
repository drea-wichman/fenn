---
title: Access Control Policy
document_id: FENN-POL-001
version: "1.2"
effective_date: 2026-05-20
last_reviewed: 2026-10-25
next_review: 2027-05-20
owner: Head of Security
approver: CTO
scope: All Fenn employees, contractors, and third parties accessing Fenn systems
framework_mapping:
  - ISO 27001:2022 A.5.3
  - ISO 27001:2022 A.5.11
  - ISO 27001:2022 A.5.15
  - ISO 27001:2022 A.5.16
  - ISO 27001:2022 A.5.17
  - ISO 27001:2022 A.5.18
  - ISO 27001:2022 A.5.37
  - ISO 27001:2022 A.6.1
  - ISO 27001:2022 A.6.5
  - ISO 27001:2022 A.6.6
  - ISO 27001:2022 A.6.7
  - ISO 27001:2022 A.7.1
  - ISO 27001:2022 A.7.2
  - ISO 27001:2022 A.7.3
  - ISO 27001:2022 A.7.4
  - ISO 27001:2022 A.7.6
  - ISO 27001:2022 A.7.7
  - ISO 27001:2022 A.7.8
  - ISO 27001:2022 A.7.9
  - ISO 27001:2022 A.7.10
  - ISO 27001:2022 A.7.12
  - ISO 27001:2022 A.7.13
  - ISO 27001:2022 A.7.14
  - ISO 27001:2022 A.8.1
  - ISO 27001:2022 A.8.2
  - ISO 27001:2022 A.8.3
  - ISO 27001:2022 A.8.4
  - ISO 27001:2022 A.8.5
  - ISO 27001:2022 A.8.7
  - ISO 27001:2022 A.8.12
  - ISO 27001:2022 A.8.15
  - ISO 27001:2022 A.8.17
  - ISO 27001:2022 A.8.18
  - ISO 27001:2022 A.8.20
  - ISO 27001:2022 A.8.22
  - ISO 27001:2022 A.8.23
  - UK GDPR Article 32
---

# Access Control Policy

## 1. Purpose

This policy defines how access to Fenn's systems, applications, and data is granted, managed, and revoked. It establishes the controls Fenn uses to ensure that only authorized individuals can access information resources, and only to the extent required to perform their role. The policy supports Fenn's commitment to customer data sovereignty and aligns with the access control requirements of ISO 27001:2022 and UK GDPR.

## 2. Scope

This policy applies to all Fenn employees, contractors, and third parties with access to Fenn systems. It covers all Fenn-managed accounts and the credentials used to access them.

Customer authentication to the Fenn platform is covered in Section 4.9. This policy does not cover customer-side controls within customer accounts, such as how a customer manages its own users.

## 3. Definitions

**Privileged access:** Access that allows an individual to make changes to production systems, customer data, security configurations, or the accounts of other users.

**Production systems:** Live systems delivering the Fenn platform to customers, as opposed to development or test environments.

**System owner:** The individual accountable for decisions about a specific Fenn system or dataset, including approving access requests and participating in access reviews.

**Standalone credentials:** Credentials that authenticate to a system directly rather than through JumpCloud SSO, used only where SSO integration is not technically possible.

## 4. Policy Statements

### 4.1 Identity Management

Fenn uses JumpCloud as the central identity provider for all employee, contractor, and third-party accounts. Every individual is issued a unique account. Shared or generic accounts are not permitted.

All access to Fenn systems is granted through this central identity. Applications and services are integrated with JumpCloud via Single Sign-On (SSO) where supported. Standalone credentials are only used where SSO integration is not technically possible, and are tracked separately.

### 4.2 Authentication

All access to Fenn systems requires multi-factor authentication. Software authenticator apps and SMS codes are not accepted. Fenn issues hardware security keys (Nitrokey 3) to every employee and contractor as the required second factor. Each individual receives two keys: one for daily use and one stored as a backup. Credential handling is covered in the security training required at onboarding under the Information Security Policy.

Lost or damaged keys must be reported to IT immediately. Replacement keys are issued through the standard hardware request process, with temporary access granted only through a documented break-glass procedure.

### 4.3 Authorization and Least Privilege

Access to Fenn systems and data is granted on the principle of least privilege. Individuals receive only the access required to perform their assigned role, and no more.

Access is managed through role-based groups in JumpCloud rather than assigned to individual accounts. Group membership is tied to role and is updated when roles change.

Exceptions to standard access require approval from the system owner. All access decisions are logged for review.

Nobody approves their own access request, reviews their own access, or merges their own code without another person's review. Write access to code repositories is limited to engineering, and repository access is included in each quarterly access review.

### 4.4 Privileged Access

Privileged access is granted sparingly and managed under stricter controls than standard access.

Standing privileged access is limited to a defined Privileged Access Working Group, currently including the Head of Security and designated senior engineering staff. Membership is reviewed at each quarterly access review.

All other privileged access is granted just-in-time. Individuals request elevation when needed, access is granted for a limited window, and is automatically revoked when the window expires.

All privileged sessions are logged. Logs are retained for 13 months under the Data Retention Policy. Logs are sent to a separate AWS account with write-once storage that administrators of production systems cannot change or delete. The Head of Security reviews privileged-session logs monthly, and the CTO reviews the Head of Security's own sessions.

Administrative tools that can bypass normal controls are limited to the Privileged Access Working Group or just-in-time access, and their use is logged.

Production systems synchronize their clocks to the Amazon Time Sync Service, staff devices use their operating system's network time service, and logs record time in UTC.

Privileged access does not extend to customer data that Fenn's servers process for opt-in features such as yield forecasting. Staff are not permitted to access that data.

### 4.5 Joiner, Mover, Leaver

Access is provisioned, modified, and revoked in coordination with HR throughout the employment lifecycle.

**Joiners.** New employees and contractors are set up in JumpCloud before their start date, including hardware keys and role-based access. Before joining, everyone has a right-to-work check, references, and an employment history check. Once Fenn's appropriate policy document for criminal offense data is in place, anyone joining the Privileged Access Working Group will also have a basic DBS check, judged only against convictions relevant to the role. Contractors sign a confidentiality agreement before getting access, and agreements are reviewed at each annual policy review.

**Movers.** When an individual changes role, their access is updated to match.

**Leavers.** Accounts are disabled on the individual's last working day. SSO-connected access is revoked automatically. Standalone credentials and any remaining access are revoked through a documented offboarding checklist. Fenn-issued laptops and hardware security keys are returned on or before the individual's last working day. Returned laptops are wiped before reuse. Confidentiality obligations in the individual's contract continue after they leave and are confirmed to them at offboarding.

### 4.6 Access Reviews

Access rights are reviewed quarterly to confirm that current access matches each individual's role and that no unnecessary access exists. Privileged Access Working Group membership and standalone credentials are included in each review.

Findings are documented. Access that is no longer required is removed promptly.

### 4.7 Remote Access

All access to Fenn systems is performed from Fenn-issued laptops. Personal laptops are not permitted to access production systems, customer data, or internal tools.

Personal mobile devices may be used to access Fenn email, calendar, and team chat where required by an individual's role. Access to customer data and production systems from mobile devices is not permitted. All devices accessing Fenn systems must meet baseline security requirements, including disk encryption, screen lock, and current operating system updates. Personal mobile devices must pass a work-profile check through device management before they can reach Fenn email, calendar, or chat. Fenn sees only the work profile.

Every Fenn laptop runs endpoint detection and response, managed by IT, with alerts to the Head of Security. Device management blocks USB storage and applies DNS filtering to block known malicious sites.

Lost or stolen devices must be reported to IT immediately so that sessions can be revoked.

### 4.8 Office Access

Entry to Fenn's Bristol office is by badge. The building's landlord provides reception and CCTV. Visitors sign in and are escorted.

Office network equipment and cabling are kept in a locked cupboard, entered only by IT for maintenance. IT keeps the equipment updated. The office network is treated as untrusted and has no direct route to production systems. Access to Fenn systems requires SSO and a hardware key from any network.

Customer and account data is not left visible or unattended.

### 4.9 Customer Authentication

Fenn's platform requires every customer user to sign in with a password and a second factor, by authenticator app or passkey. SMS codes are not offered.

## 5. Roles and Responsibilities

**Head of Security** owns this policy. Responsibilities include maintaining the policy, approving exceptions, and overseeing the Privileged Access Working Group.

**IT** is responsible for day-to-day operations: provisioning and revoking accounts, managing JumpCloud configuration, issuing hardware keys, and maintaining the standalone credentials inventory.

**System owners** are responsible for approving access requests for the systems and data they own, and for participating in quarterly access reviews.

**All employees and contractors** are responsible for protecting their credentials and hardware keys, reporting lost or stolen devices immediately, and complying with this policy.

Operating procedures, including the offboarding checklist and break-glass procedure, are kept in Fenn's internal knowledge base for the staff who need them.

## 6. Exceptions

Exceptions to this policy may be granted in writing by the Head of Security. Each exception must include a documented justification, the duration of the exception, and any compensating controls required to manage the resulting risk. Exceptions are reviewed quarterly alongside access reviews and removed when no longer required.

## 7. Related Documents

- FENN-POL-002: Information Security Policy
- FENN-POL-003: Vendor Risk Management Policy
- FENN-POL-004: Data Retention Policy
- FENN-PLN-001: Incident Response Plan
- Sub-processor List

## 8. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-05-20 | Jack Lowe, Head of Security | Initial formal policy. Codifies existing practices aligned with ISO 27001:2022. |
| 1.1 | 2026-10-22 | Jack Lowe, Head of Security | Added the restriction on staff access to data processed for opt-in features. Includes earlier corrections to references and wording. |
| 1.2 | 2026-10-25 | Jack Lowe, Head of Security | Added office access, customer authentication, and screening. Updated segregation of duties, logging, device, and joiner and leaver requirements. |
