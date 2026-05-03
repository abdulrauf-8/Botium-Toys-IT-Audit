# 🔐 Botium Toys — Internal Security Audit

> **Audit Type:** Internal IT Security Audit  
> **Framework:** NIST Cybersecurity Framework (CSF)  
> **Risk Score:** 8 / 10 (High)  
> **Risk Score Rationale:** Scored High due to the **criticality of exposed data** (PII, SPII, and cardholder data) combined with the **depth of system vulnerability** (no encryption, no IDS, no backups). Under an Impact × Likelihood model, a single ransomware event could result in total business failure given the current absence of recovery controls.  
> **Scope:** Entire security program — assets, internal network, systems, and compliance practices

> **Definitions:**  
> **PII** (Personally Identifiable Information) — any data that can identify an individual (name, address, email).  
> **SPII** (Sensitive PII) — higher-risk PII such as Social Security numbers, financial records, or biometric data.  
> **CDE** (Cardholder Data Environment) — any system that stores, processes, or transmits credit card data.

---

## ⚠️ Key Findings

Before reviewing the full checklist, the following three findings represent the most critical threats to Botium Toys and require immediate executive attention:

1. **Total exposure of cardholder and customer data** — All employees have unrestricted access to the CDE and customer PII/SPII, with no encryption protecting data at rest or in transit. A single insider incident or external breach would expose the entire customer database.
2. **Zero recovery capability** — There are no backups and no disaster recovery plan. A ransomware attack or hardware failure would likely cause irreversible data loss and business disruption with no path to recovery.
3. **Detection blindness** — Without an IDS or a formalized legacy system monitoring schedule, the organization has no reliable means of knowing a breach has occurred — rendering any incident response or regulatory notification plan effectively unenforceable.

---

## 🗂️ Controls Assessment Checklist

> **Question:** Does Botium Toys currently have this control in place?

### Administrative / Managerial Controls

| Control | In Place? | Notes |
|---|---|---|
| Least Privilege | ❌ No | Unrestricted access to the CDE creates insider threat risk and violates PCI DSS Requirement 7 |
| Disaster Recovery Plans | ❌ No | No plans currently exist; business continuity is fully unprotected |
| Password Policies | ⚠️ Partial | Policy exists but does not meet current minimum complexity requirements (8+ chars, mixed case, numbers, special characters) |
| Separation of Duties | ❌ No | Not implemented; increases risk of undetected fraud or misuse |

### Technical Controls

| Control | In Place? | Notes |
|---|---|---|
| Firewall | ✅ Yes | Blocks traffic based on a defined ruleset |
| Intrusion Detection System (IDS) | ❌ No | No visibility into anomalous or malicious network activity |
| Backups | ❌ No | No copies of critical data exist; violates 3-2-1 backup standard |
| Antivirus Software | ✅ Yes | Installed and monitored regularly |
| Manual Monitoring for Legacy Systems | ⚠️ Partial | Monitoring occurs but lacks a regular schedule and documented intervention procedures |
| Encryption | ❌ No | Cardholder data is unencrypted at rest and in transit; violates PCI DSS Requirements 3 & 4 |
| Password Management System | ❌ No | No centralized enforcement of password policy |

### Physical / Operational Controls

| Control | In Place? | Notes |
|---|---|---|
| Locks (offices, storefront, warehouse) | ✅ Yes | Sufficient physical locks in place |
| CCTV Surveillance | ✅ Yes | Up-to-date system in place |
| Fire Detection / Prevention Systems | ✅ Yes | Functioning fire alarm and sprinkler system |

---

## ✅ Compliance Checklist

> **Question:** Does Botium Toys currently adhere to this compliance best practice?

### 💳 Payment Card Industry Data Security Standard (PCI DSS)

| Best Practice | Compliant? | Notes |
|---|---|---|
| Only authorized users have access to customers' credit card information | ❌ No | All employees can access the CDE; violates Requirement 7 |
| Credit card data stored, accepted, processed, and transmitted in a secure environment | ❌ No | No environmental controls or access restrictions in place |
| Data encryption implemented for credit card transaction touchpoints | ❌ No | No encryption at rest or in transit; violates Requirements 3 & 4 |
| Secure password management policies adopted | ❌ No | Existing policy is nominal and unenforced via a management system |

### 🇪🇺 General Data Protection Regulation (GDPR)

| Best Practice | Compliant? | Notes |
|---|---|---|
| E.U. customers' data is kept private/secured | ❌ No | No encryption or access restrictions on customer data |
| Plan to notify E.U. customers within 72 hours of a breach | ⚠️ Partial | Plan exists on paper, but absence of an IDS and no formal monitoring schedule means a breach could go undetected for months — making timely notification effectively impossible |
| Data is properly classified and inventoried | ❌ No | No asset classification process exists |
| Privacy policies, procedures, and processes enforced and documented | ✅ Yes | Documented and enforced among IT staff and employees |

### 🏢 System and Organizations Controls (SOC type 1, SOC type 2)

| Best Practice | Compliant? | Notes |
|---|---|---|
| User access policies are established | ❌ No | No least privilege or access control policies in place |
| Sensitive data (PII/SPII) is confidential/private | ❌ No | Broadly accessible to all staff without restriction |
| Data integrity ensures data is consistent, complete, accurate, and validated | ✅ Yes | IT department has integrated controls for data integrity |
| Data is available to individuals authorized to access it | ✅ Yes | Availability is maintained |

---

## 💡 Recommendations by NIST CSF Function

### 🔵 Identify
*Know what assets exist and what risks they carry.*

- **Complete an asset classification and inventory.** The IT department cannot currently determine which assets are at risk. This is a prerequisite for every other security function and the starting point of the NIST CSF.
- **Formalize a risk register** that maps each asset to its data sensitivity level (PII, SPII, cardholder data) and potential business impact if compromised.

### 🟣 Protect
*Limit access and safeguard systems against threats.*

- **Implement Least Privilege and Separation of Duties.** Restrict access to the CDE to only authorized roles per PCI DSS Requirement 7. No single employee should have unchecked access to sensitive data.
- **Deploy encryption:** Use **AES-256** for data at rest and **TLS 1.2+** for data in transit to protect cardholder and customer data per PCI DSS Requirements 3 and 4.
- **Upgrade the password policy** to enforce minimum complexity (8+ characters, mixed case, numbers, special characters) and deploy a **centralized password management system** to enforce it automatically.

### 🟡 Detect
*Build the capability to know when something goes wrong.*

- **Install an Intrusion Detection System (IDS).** Without one, the organization is effectively blind to network threats. This also directly impacts the enforceability of the GDPR 72-hour breach notification obligation.
- **Formalize a legacy system monitoring schedule** with documented intervention procedures. Ad hoc monitoring creates unpredictable gaps in visibility.

### 🟠 Respond
*Have a plan for when an incident occurs.*

- **Develop a formal Incident Response Plan (IRP).** Currently no documented process exists for identifying, containing, or escalating a security incident. This is a gap not covered by the existing 72-hour GDPR notification plan, which addresses communication only — not response.
- Ensure the IRP includes roles, responsibilities, escalation paths, and regulatory notification procedures for both PCI DSS and GDPR obligations.

### 🔴 Recover
*Be able to restore operations after an incident.*

- **Implement the 3-2-1 Backup Rule:** Maintain **3 copies** of critical data, on **2 different storage media**, with **1 copy stored offsite** (or in a separate cloud region). This is the industry gold standard for resilience against ransomware and hardware failure.
- **Establish a Disaster Recovery Plan (DRP)** that defines Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO) for all critical systems. Without this, even restored backups may not return the business to operation in an acceptable timeframe.

---

## 📊 Risk Summary

| Finding | NIST Function | Risk Level |
|---|---|---|
| No encryption (AES-256 / TLS 1.2+) | Protect | 🔴 Critical |
| No least privilege / separation of duties | Protect | 🔴 Critical |
| No backups (3-2-1 rule not met) | Recover | 🔴 Critical |
| No disaster recovery plan | Recover | 🔴 Critical |
| No IDS — detection blindness | Detect | 🔴 Critical |
| No incident response plan | Respond | 🔴 Critical |
| Weak / unenforced password policy | Protect | 🟡 Medium |
| Legacy system monitoring gaps | Detect | 🟡 Medium |
| No asset classification or inventory | Identify | 🟡 Medium |
| GDPR 72-hr notification (plan only, unenforceable) | Respond | 🟡 Medium |
| Physical security (locks, CCTV, fire systems) | Protect | 🟢 Low |
| Privacy documentation (GDPR) | Protect | 🟢 Low |

---

*Audit conducted using the NIST Cybersecurity Framework (CSF) five core functions: Identify, Protect, Detect, Respond, Recover. Controls assessed against the Controls Categories document covering Administrative/Managerial, Technical, and Physical/Operational control types. Compliance evaluated against PCI DSS, GDPR, and SOC type 1/type 2 requirements.*
