# Data Flow and Architecture

## 1. Overview

This document shows where your data goes when you use Fenn and who can read it at each step. By default, Fenn encrypts your farm data on your device with keys that only you hold. Fenn stores the encrypted data and cannot read it. Fenn's servers are computers Fenn rents in Amazon Web Services' London data centers. A few features work differently because they need Fenn's servers to handle the data. This document identifies each one.

Every flow that involves Fenn carries one of four labels:

- **Encrypted on your device.** Your device encrypts the data with your key before it leaves. Fenn stores it and cannot read it.
- **Encrypted on Fenn's servers.** A service you connect sends data to Fenn's servers, not to your device. The servers lock it on arrival so only your keys can open it. Fenn cannot read it after that.
- **Readable on Fenn's servers while in use.** You turned on a feature that needs Fenn's servers to read your data while it runs. The servers delete it when the feature finishes. Fenn's staff are not permitted to access it, and Fenn does not use it to train its models.
- **Readable by Fenn's staff.** The details Fenn needs to run your account and support you. Fenn's staff can read them, as the Data Processing Agreement describes.

## 2. Diagram

![Data flow diagram. Your devices on the left, Fenn in the middle, outside services on the right. Each arrow is labeled Encrypted on your device, Encrypted on Fenn's servers, Readable on Fenn's servers while in use, or Readable by Fenn's staff.](https://fenn.wichman.io/images/data-flow.svg)

Fenn does not send reports to Defra, HMRC, or anyone else.

## 3. Data inventory

| Data | Where it comes from | Label | Who can read it |
|---|---|---|---|
| Farm records and their edit history | You enter them | Encrypted on your device | Only you and the team members you choose |
| Reports | Built on your device | None. Fenn does not store them | Only you, until you export, share, or print them |
| Location (when enabled) | Your phone's GPS, read when you log an activity | Encrypted on your device | Only you and the team members you choose |
| Data from connected services | Equipment (John Deere, Case IH, New Holland, AGCO, CLAAS), sensors (Soil Scout, Sentek, Davis), accounting (Xero, QuickBooks, Sage), drone services | Encrypted on Fenn's servers | Fenn's servers, only until it is encrypted. Then only you and the team members you choose |
| Weather (default) | Your device asks the Met Office | None. Fenn is not involved | The Met Office sees the location |
| Weather (forecasting on) | Fenn's servers ask the Met Office | Readable on Fenn's servers while in use | Fenn's servers and the Met Office |
| Forecast inputs | Your data, sent when forecasting is on | Readable on Fenn's servers while in use | Fenn's servers, only while the forecast runs. Deleted when it finishes |
| Forecast results | Fenn's forecast | Readable on Fenn's servers while in use, then encrypted on your device | Fenn's servers, only while the forecast runs. Then only you and the team members you choose |
| Team member list (names and emails) | You add them | Readable by Fenn's staff | Fenn's staff |
| Roles and key access | You set them | Encrypted on your device | Only you and the team members you choose |
| Login, billing, and support details | You enter them | Readable by Fenn's staff | Fenn's staff, Stripe (payments), and Plain (support) |
| Account access log (sign-ins, devices, IP addresses) | Fenn records it | Readable by Fenn's staff | Fenn's staff, and you |
| Account emails (invitations, password resets) | Fenn sends them | Readable by Fenn's staff | Fenn's staff and Amazon's email service (SES) |
| Error reports | Fenn's apps and servers, when something goes wrong | Readable by Fenn's staff | Fenn's staff and Sentry (EU). Never includes farm data |

## 4. Team accounts and keys

You decide who on your team can read each type of data. Fenn's app handles the keys, and Fenn never holds them.

Your data is sorted into categories, and each category has its own key. When you give a team member access to a category, your app hands them that key, locked so only their device can open it. Fenn passes the locked key along and cannot open it.

When you remove someone, or take away a category, your app makes a new key for that category. Everything saved from then on uses the new key. Data saved before the change is not re-encrypted. The person loses access to future data. They keep anything they already opened or downloaded.

Fenn gives you a recovery key when you open your account. You can also name a co-owner, who holds every key, so the account never depends on one person.

## 5. Limits and what you rely on

- **Lost keys.** If you lose your keys and have no recovery key or co-owner, no one can read your data, including Fenn.
- **What Fenn can always see.** Who is on your team, how many records you have and their size, when they change, and the IP addresses and devices you connect from.
- **Exports.** A report you export, share, or print is no longer encrypted. Protecting it is up to you.
- **Fenn's apps.** You rely on Fenn's apps to encrypt as described here.
- **Key delivery.** When you add a team member, Fenn delivers their public key to your app. You rely on Fenn to deliver the right one.
- **Outside services.** The Met Office and the services you connect hold their own copies under their own terms.

## Revision History

| Version | Date | Author | Description |
|---|---|---|---|
| 1.0 | 2026-10-22 | Jack Lowe, Head of Security | Initial document. Shows where customer data goes, who can read it at each step, and where Fenn's default encryption has exceptions. |
