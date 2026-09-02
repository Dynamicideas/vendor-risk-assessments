# Security Assessment Report (SAR) - Third Party Vendor Review

**Vendor Name:** CloudStorage XYZ, Inc.  
**Product Evaluated:** Cloud-Native Enterprise File Storage SaaS  
**Assessment Date:** September 2026  
**Lead GRC Analyst:** [Your Name / GRC Technical Analyst]  

---

## 1. Executive Summary
This assessment evaluates the security and compliance posture of CloudStorage XYZ to determine the residual risk of introducing their product into our corporate environment. Evaluation artifacts reviewed include their latest **SOC 2 Type II Report (dated June 2026)** and their **SIG (Standardized Information Gathering) Questionnaire**. 

**Overall Recommendation:** **Approved with Conditions** (Low-to-Medium Risk Profile).

---

## 2. Review of Vendor Attestations (SOC 2 Type II Evaluation)
A detailed inspection of the vendor's SOC 2 Type II report revealed strong core alignment with the Trust Services Criteria (Security and Confidentiality), with two critical exceptions noted.

### 2.1 Confirmed Strengths
* **Data-in-Transit Encryption:** Leverages TLS 1.3 exclusively across all public endpoints.
* **Access Control:** Full integration with corporate Identity Providers (IdPs) supporting SAML 2.0 and mandatory Multi-Factor Authentication (MFA).
* **Physical Security:** Data centers hosted inside AWS US-East-1 regions, confirming physical security standard abstractions (ISO 27001 / SOC 2).

### 2.2 Identified Gaps & Auditor Exceptions
* **Exception 1 (SOC 2 Section IV):** The independent auditor noted that 3 out of 15 randomly sampled employee offboarding profiles did not have their production database access terminated within the vendor's policy-defined 24-hour SLA. 
* **Exception 2:** Data-at-Rest encryption keys are currently managed natively by the vendor rather than allowing the customer to bring their own keys (BYOK).

---

## 3. Risk Identification & Compensating Controls

| Risk ID | Vulnerability / Threat Scenario | Likelihood | Impact | Calculated Risk Level | Required Compensating Control / Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **VR-01** | Vendor employees retain active credentials post-termination, creating a vector for insider data exfiltration. | Medium | High | **Medium Risk** | **Condition of Approval:** Our company will implement strict IP-whitelisting on our storage instances so that credentials alone cannot access data outside our authorized network block. |
| **VR-02** | Lack of Customer-Managed Keys (BYOK) limits direct command over cryptographic shredding if data deletion is required. | Low | Medium | **Low Risk** | **Accepted Risk:** Vendor utilizes automated AES-256 bit underlying volume encryption. Risk is accepted pending a strict data deletion contractual clause. |

---

## 4. Final Sign-Off & Governance Verdict
* **Risk Disposition:** Accepted with Technical Restrictions.
* **Re-assessment Cadence:** Annually (Next Review Required: September 2027).
