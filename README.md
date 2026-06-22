# Enterprise Risk Assessment & Risk Register

**Organization:** HealthVibe Telemedicine (Fictional Entity)
**Project Author:** Prasun Sharma
**Date:** June 2026
**Framework Alignment:** NIST Cybersecurity Framework (CSF) 2.0, HIPAA Security Rule

---

## 1. Executive Summary

HealthVibe is a rapidly growing, cloud-native telemedicine startup. With a 100% remote workforce, HealthVibe connects patients with healthcare providers via secure video consultations. The organization stores heavily regulated Patient Health Information (PHI) within an AWS-hosted infrastructure.

The purpose of this Risk Assessment is to identify critical business assets, evaluate potential cyber threats, calculate inherent and residual risks, and propose mitigating controls to ensure business continuity and regulatory compliance.

## 2. Risk Assessment Methodology

This assessment utilizes a qualitative risk matrix approach. Risk is calculated using the standard formula:
**Risk Score = Likelihood × Impact**

### 2.1 Likelihood Scale

* **1 - Rare:** Highly unlikely to occur.
* **2 - Unlikely:** Not expected, but possible.
* **3 - Possible:** Might occur at some point.
* **4 - Likely:** Will probably occur in most circumstances.
* **5 - Almost Certain:** Expected to occur frequently.

### 2.2 Impact Scale

* **1 - Negligible:** Minor operational friction; no data loss.
* **2 - Minor:** Short-term disruption; isolated non-sensitive data loss.
* **3 - Moderate:** Noticeable service degradation; minor compliance breach.
* **4 - Major:** Prolonged outage; severe financial loss; PHI breach triggering regulatory fines.
* **5 - Catastrophic:** Business-ending event; massive PHI exfiltration; criminal negligence.

### 2.3 Risk Matrix Thresholds

* **1 - 4:** **Low Risk** (Acceptable, monitor regularly)
* **5 - 9:** **Medium Risk** (Implement controls where cost-effective)
* **10 - 16:** **High Risk** (Requires immediate mitigation planning)
* **17 - 25:** **Critical Risk** (Unacceptable; requires immediate executive intervention)

---

## 3. Asset Inventory (Scope)

1. **AWS Cloud EHR Database:** Primary repository for all Patient Health Information (PHI).
2. **Remote Employee Endpoints:** Laptops issued to doctors, nurses, and administrative staff.
3. **Telehealth Video Application:** The proprietary web portal used for doctor-patient consultations.
4. **AWS S3 Cloud Storage:** Used for storing patient documents, lab results, and backups.

---

## 4. Comprehensive Risk Register

| Risk ID | Asset | Threat Actor / Event | Vulnerability | Inherent Likelihood | Inherent Impact | Inherent Risk Score | Proposed Mitigating Controls | Residual Likelihood | Residual Impact | Residual Risk Score | Treatment Decision |
|---|---|---|---|:---:|:---:|:---:|---|:---:|:---:|:---:|---|
| **R-01** | AWS EHR Database | Cybercriminal Group (Ransomware) | Lack of robust database backups and network segmentation. | 4 | 5 | **20 (Critical)** | Implement Immutable Backups, Network Segmentation, and EDR on database servers. | 2 | 3 | **6 (Medium)** | **Mitigate** |
| **R-02** | Employee Endpoints | Opportunistic Thief (Physical Theft) | Missing Full Disk Encryption (FDE); weak password policies. | 3 | 4 | **12 (High)** | Enforce BitLocker/FileVault via MDM; Implement strong password policies and remote wipe capabilities. | 3 | 1 | **3 (Low)** | **Mitigate** |
| **R-03** | Telehealth App | Script Kiddie / Malicious Hacker | Lack of rate limiting on login portal; no Multi-Factor Authentication (MFA). | 4 | 4 | **16 (High)** | Enforce mandatory MFA for all users; Implement Web Application Firewall (WAF) to block brute-force. | 1 | 4 | **4 (Low)** | **Mitigate** |
| **R-04** | AWS S3 Storage | Insider Threat (Accidental) | Cloud misconfiguration (S3 bucket left public without IAM restrictions). | 3 | 5 | **15 (High)** | Automated Cloud Security Posture Management (CSPM) alerts; strict IAM Least Privilege enforcement. | 1 | 5 | **5 (Medium)** | **Mitigate** |
| **R-05** | Employee Endpoints | Advanced Persistent Threat / Cybercriminal | Employee falls for targeted phishing email delivering malware. | 5 | 4 | **20 (Critical)** | Monthly Security Awareness Training, Phishing Simulations, and Email Gateway Filtering. | 2 | 2 | **4 (Low)** | **Mitigate** |

---

## 5. Risk Treatment Plan & Implementation Details

Following the assessment, HealthVibe leadership has agreed to prioritize the following control implementations to bring all Critical and High risks down to an acceptable level:

### Immediate Actions (30 Days)

* **Identity & Access Management (IAM):** Enforce mandatory Multi-Factor Authentication (MFA) across all corporate accounts, EHR access, and AWS administrative consoles. *(Mitigates R-03)*
* **Endpoint Security:** Deploy Mobile Device Management (MDM) to enforce Full Disk Encryption (FDE) and remote-wipe capabilities on all 100% remote endpoints. *(Mitigates R-02)*

### Short-Term Actions (60-90 Days)

* **Cloud Architecture:** Audit all AWS S3 buckets using a CSPM tool to ensure "Block Public Access" is enabled globally. Restrict IAM roles based on the principle of Least Privilege. *(Mitigates R-04)*
* **Disaster Recovery:** Establish immutable, air-gapped backups for the main EHR database to ensure ransomware resilience. *(Mitigates R-01)*

### Continuous Actions

* **Human Firewall:** Institute mandatory monthly security awareness training with quarterly simulated phishing campaigns targeting the remote workforce. *(Mitigates R-05)*

---
*Disclaimer: This is a fictional project created for educational and portfolio demonstration purposes.*
