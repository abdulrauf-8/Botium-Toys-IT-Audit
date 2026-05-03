# 🔐 Botium Toys — Internal Security Audit

> **Audit Type:** Internal IT Security Audit  
> **Framework:** NIST Cybersecurity Framework (CSF)  
> **Risk Score:** 8 / 10 (High)  
> **Scope:** Entire security program — assets, internal network, systems, and compliance practices

---

## 📋 Overview

Botium Toys is a small U.S.-based toy retailer with a growing online presence serving customers in the U.S. and the E.U. This audit was conducted to assess existing controls and compliance practices, identify gaps, and provide recommendations to improve the company's overall security posture.

---

## 🗂️ Controls Assessment Checklist

> **Question:** Does Botium Toys currently have this control in place?

### Administrative / Managerial Controls

| Control | In Place? | Notes |
|---|---|---|
| Least Privilege | ❌ No | All employees have broad access to internal data, including cardholder data and PII |
| Disaster Recovery Plans | ❌ No | No plans currently exist |
| Password Policies | ⚠️ Partial | Policy exists but does not meet current minimum complexity requirements |
| Separation of Duties | ❌ No | Not implemented |

### Technical Controls

| Control | In Place? | Notes |
|---|---|---|
| Firewall | ✅ Yes | Blocks traffic based on a defined set of security rules |
| Intrusion Detection System (IDS) | ❌ No | Not installed |
| Backups | ❌ No | No backups of critical data exist |
| Antivirus Software | ✅ Yes | Installed and monitored regularly |
| Manual Monitoring for Legacy Systems | ⚠️ Partial | Monitoring occurs but lacks a regular schedule and clear intervention methods |
| Encryption | ❌ No | Credit card data is not encrypted at rest or in transit |
| Password Management System | ❌ No | No centralized system to enforce password policy |

### Physical / Operational Controls

| Control | In Place? | Notes |
|---|---|---|
| Locks (offices, storefront, warehouse) | ✅ Yes | Sufficient locks in place |
| CCTV Surveillance | ✅ Yes | Up-to-date system in place |
| Fire Detection / Prevention Systems | ✅ Yes | Functioning fire alarm and sprinkler system |

---

## ✅ Compliance Checklist

> **Question:** Does Botium Toys currently adhere to this compliance best practice?

### 💳 Payment Card Industry Data Security Standard (PCI DSS)

| Best Practice | Compliant? |
|---|---|
| Only authorized users have access to customers' credit card information | ❌ No |
| Credit card data is stored, accepted, processed, and transmitted in a secure environment | ❌ No |
| Data encryption procedures implemented for credit card transaction touchpoints | ❌ No |
| Secure password management policies adopted | ❌ No |

### 🇪🇺 General Data Protection Regulation (GDPR)

| Best Practice | Compliant? |
|---|---|
| E.U. customers' data is kept private/secured | ❌ No |
| Plan to notify E.U. customers within 72 hours of a breach | ✅ Yes |
| Data is properly classified and inventoried | ❌ No |
| Privacy policies, procedures, and processes enforced and documented | ✅ Yes |

### 🏢 System and Organizations Controls (SOC type 1, SOC type 2)

| Best Practice | Compliant? |
|---|---|
| User access policies are established | ❌ No |
| Sensitive data (PII/SPII) is confidential/private | ❌ No |
| Data integrity ensures data is consistent, complete, accurate, and validated | ✅ Yes |
| Data is available to individuals authorized to access it | ✅ Yes |

---

## 💡 Recommendations

### 🔴 Priority 1 — Immediate Action (High Risk)

- **Implement Least Privilege & Separation of Duties** — All employees currently have broad access to internal data including cardholder data and PII/SPII. Access must be restricted to only what each role requires.
- **Deploy Encryption** — Credit card data is accepted, processed, transmitted, and stored without encryption. This is a critical PCI DSS and GDPR violation.
- **Establish Disaster Recovery Plans & Data Backups** — The complete absence of both means any incident (ransomware, hardware failure, breach) could cause irreversible data loss and business disruption.
- **Install an Intrusion Detection System (IDS)** — With a growing online presence and no visibility into anomalous network traffic, threats may go undetected indefinitely.

### 🟡 Priority 2 — Near-Term (Medium Risk)

- **Upgrade Password Policy** — The current policy does not meet minimum complexity standards (8+ characters, mixed letters, numbers, special characters). Update and enforce it company-wide.
- **Deploy a Centralized Password Management System** — This will enforce the updated policy and reduce helpdesk burden caused by password resets.
- **Formalize Legacy System Maintenance Schedule** — Monitoring occurs ad hoc. A structured schedule with documented intervention methods is needed to manage risk from end-of-life systems.
- **Complete Asset Classification & Inventory** — The IT department cannot currently identify which assets are at risk. This is a prerequisite for the NIST CSF *Identify* function and effective risk management.

### 🟢 Maintain — Already in Place

- Firewall, antivirus, CCTV, physical locks, and fire detection systems are functioning and should be maintained with regular reviews.
- The 72-hour E.U. breach notification plan and privacy documentation satisfy GDPR requirements and should be extended and communicated across all departments.

---

## 📊 Risk Summary

| Area | Risk Level |
|---|---|
| Access Controls (Least Privilege, Separation of Duties) | 🔴 High |
| Encryption (PII, Credit Card Data) | 🔴 High |
| Disaster Recovery & Backups | 🔴 High |
| Intrusion Detection | 🔴 High |
| Password Management | 🟡 Medium |
| Legacy System Procedures | 🟡 Medium |
| Asset Classification | 🟡 Medium |
| Physical Security | 🟢 Low |
| GDPR Breach Notification | 🟢 Low |

---

*Audit conducted using the NIST Cybersecurity Framework (CSF). Controls assessed against the Controls Categories document covering Administrative/Managerial, Technical, and Physical/Operational control types.*
