# 2. Executive Dashboard

*  **Incident ID:** SOC-2023-07-PHISH
*  **Date of Report:** 11 November 2025
*  **Analyst:** Niladri Biswas

## Incident Severity & Status

| Attribute | Status |
|:---|:---|
| **Severity Classification** | 🟡 Medium |
| **Incident Status** | ✅ Confirmed Malicious / Responded |
| **Attack Vector** | Email (Advance Fee Fraud / 419 Scam) |
| **Detection Method** | Manual User Reporting & Email Header Analysis |

---

## Executive Risk Heatmap

| Risk Area | Inherent Risk (Pre-Controls) | Control Gaps Identified | Residual Risk (Post-Controls) |
|:---|:---:|:---|:---:|
| **Financial Fraud** | 🔴 High | No DMARC `p=reject`, weak SPF enforcement. | 🟡 Low |
| **Data/Identity Theft** | 🟠 Medium | Lack of user awareness on "Reply-To" mismatches. | 🟡 Low |
| **Brand Reputation** | 🔴 High | External adversaries can spoof the company domain at will. | 🟡 Low |
| **Third-Party Infrastructure** | 🟠 Medium | Attacker exploited a compromised Russian government subdomain. | 🟢 Minimal |

---

## Financial Impact & Cost-Benefit Analysis

| Countermeasure | Implementation Cost | Avoided Cost (Risk Mitigation) |
|:---|:---:|:---:|
| **DMARC `p=reject` Policy** | ~$200 (Engineer + DNS update) | **~$100,000+** (Prevents BEC / Financial Fraud) |
| **Perimeter IP/Domain Blocking** | ~$100 (Admin overhead) | **~$50,000** (Prevents future malware/C2 attempts) |
| **Employee Security Awareness** | ~$1,000 (Annual program cost) | **~$20,000** (Avoids GDPR/Privacy breach remediation) |
| **Total Remediation Cost** | **~$1,300** | **~$170,000+** (Cost of Inaction) |

---

## High-Priority Action Items

1.  **P1 - DMARC Enforcement:** Configure `p=reject` and enforce strict SPF alignment on all organizational domains to prevent sender spoofing.
2.  **P1 - IOC Blocking:** Block source IP `109.202.24.52` and the compromised relay `54upr.rosreestr.ru`.
3.  **P2 - User Training:** Update security awareness modules to include "Reply-To" address mismatch detection and Advance Fee Fraud examples.
4.  **P3 - Threat Intel Integration:** Configure email gateway to quarantine messages exhibiting multiple weak signals (SPF FAIL + No DKIM + Reply-To mismatch).

---

## Key Metrics

| Metric | Value |
|:---|:---|
| **Automated Detection Rate** | 0% (VirusTotal 0/93 false negative) |
| **Manual Verification Required?** | ✅ Yes |
| **Compliance Frameworks Triggered** | ISO 27001, NIST CSF, GDPR |

---
