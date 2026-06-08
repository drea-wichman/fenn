---
title: Access Control Policy
document_id: FENN-POL-001
version: 1.0
effective_date: 2026-05-20
last_reviewed: 2026-05-20
next_review: 2027-05-20
owner: Jack Lowe, Head of Security
approver: Cian Kelly, CTO
scope: All Fenn employees, contractors, and third parties accessing Fenn systems
framework_mapping:
  - ISO 27001:2022 A.5.11
  - ISO 27001:2022 A.5.15
  - ISO 27001:2022 A.5.16
  - ISO 27001:2022 A.5.17
  - ISO 27001:2022 A.5.18
  - ISO 27001:2022 A.6.5
  - ISO 27001:2022 A.6.7
  - ISO 27001:2022 A.8.1
  - ISO 27001:2022 A.8.2
  - ISO 27001:2022 A.8.3
  - ISO 27001:2022 A.8.5
  - ISO 27001:2022 A.8.15
  - ISO 27001:2022 A.8.16
  - UK GDPR Art. 32
---

# Access Control Policy

## 1. Purpose

This policy defines how access to Fenn's systems, applications, and data is granted, managed, and revoked. It establishes the controls Fenn uses to ensure that only authorized individuals can access information resources, and only to the extent required to perform their role. The policy supports Fenn's commitment to customer data sovereignty and aligns with the access control requirements of ISO 27001:2022 and UK GDPR.

## 2. Scope

This policy applies to all Fenn employees, contractors, and third parties with access to Fenn systems. It covers all Fenn-managed accounts and the credentials used to access them.

Customer access to the Fenn platform is governed separately by the Information Security Policy. This policy does not cover customer-side controls within customer accounts.

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

All access to Fenn systems requires multi-factor authentication. Software authenticator apps and SMS codes are not accepted. Fenn issues hardware security keys (Nitrokey 3) to every employee and contractor as the required second factor. Each individual receives two keys: one for daily use and one stored as a backup.

Lost or damaged keys must be reported to IT immediately. Replacement keys are issued through the standard hardware request process, with temporary access granted only through a documented break-glass procedure.

### 4.3 Authorization and Least Privilege

Access to Fenn systems and data is granted on the principle of least privilege. Individuals receive only the access required to perform their assigned role, and no more.

Access is managed through role-based groups in JumpCloud rather than assigned to individual accounts. Group membership is tied to role and is updated when roles change.

Exceptions to standard access require approval from the system owner. All access decisions are logged for review.

### 4.4 Privileged Access

Privileged access is granted sparingly and managed under stricter controls than standard access.

Standing privileged access is limited to a defined Privileged Access Working Group, currently including the Head of Security and designated senior engineering staff. Membership is reviewed at each quarterly access review.

All other privileged access is granted just-in-time. Individuals request elevation when needed, access is granted for a limited window, and is automatically revoked when the window expires.

All privileged sessions are logged.

### 4.5 Joiner, Mover, Leaver

Access is provisioned, modified, and revoked in coordination with HR throughout the employment lifecycle.

**Joiners.** New employees and contractors are set up in JumpCloud before their start date, including hardware keys and role-based access.

**Movers.** When an individual changes role, their access is updated to match.

**Leavers.** Accounts are disabled on the individual's last working day. SSO-connected access is revoked automatically. Standalone credentials and any remaining access are revoked through a documented offboarding checklist.

### 4.6 Access Reviews

Access rights are reviewed quarterly to confirm that current access matches each individual's role and that no unnecessary access exists. Privileged Access Working Group membership and standalone credentials are included in each review.

Findings are documented. Access that is no longer required is removed promptly.

### 4.7 Remote Access

All access to Fenn systems is performed from Fenn-issued laptops. Personal laptops are not permitted to access production systems, customer data, or internal tools.

Personal mobile devices may be used to access Fenn email, calendar, and team chat where required by an individual's role. Access to customer data and production systems from mobile devices is not permitted. All devices accessing Fenn systems must meet baseline security requirements, including disk encryption, screen lock, and current operating system updates.

Lost or stolen devices must be reported to IT immediately so that sessions can be revoked.

## 5. Roles and Responsibilities

**Head of Security** owns this policy. Responsibilities include maintaining the policy, approving exceptions, and overseeing the Privileged Access Working Group.

**IT** is responsible for day-to-day operations: provisioning and revoking accounts, managing JumpCloud configuration, issuing hardware keys, and maintaining the standalone credentials inventory.

**System owners** are responsible for approving access requests for the systems and data they own, and for participating in quarterly access reviews.

**All employees and contractors** are responsible for protecting their credentials and hardware keys, reporting lost or stolen devices immediately, and complying with this policy.

## 6. Exceptions

Exceptions to this policy may be granted in writing by the Head of Security. Each exception must include a documented justification, the duration of the exception, and any compensating controls required to manage the resulting risk. Exceptions are reviewed quarterly alongside access reviews and removed when no longer required.

## 7. Related Documents

- Information Security Policy
- Mobile Device Policy
- Sub-processor List
- Incident Response Plan
- Data Retention Policy
- Vendor Risk Management Policy

## 8. Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-05-20 | Jack Lowe, Head of Security | Initial formal policy. Codifies existing practices aligned with ISO 27001:2022. |