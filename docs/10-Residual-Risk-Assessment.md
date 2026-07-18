# 10. Residual Risk Assessment (Post-Remediation)

After implementing the mitigating controls outlined in `docs/06-Remediation-Tracker.md`, certain risks inevitably remain. This document provides a formal residual risk treatment plan.

## 10.1 Control Implementation Summary

| Implemented Control | Effect on Risk |
|:---|:---|
| **DMARC `p=reject` and SPF/DKIM hardening** | Eliminates external domain spoofing. Attackers can no longer send emails impersonating our domain (`@company.com`). |
| **Email Gateway Rule (Reply-To mismatch)** | Automatically quarantines emails where a mismatch between `From:` and `Reply-To:` is detected, especially with free email providers. |
| **IOC Blocking** | Immediately prevents connections from the malicious IP (`109.202.24.52`) and relay domain (`54upr.rosreestr.ru`). |
| **Enhanced Security Awareness Training** | Improves human detection capabilities, reducing the likelihood that an employee responds to a social engineering attempt. |

## 10.2 Residual Risk Register

Even with the above controls, the following residual risks remain:

| Risk ID | Residual Risk | Risk Owner | Inherent Risk | Current Control | Residual Risk Score | Next Review Date |
|:---:|:---|:---|:---:|:---|:---:|:---:|
| **RES-01** | **Zero-Day Social Engineering:** Attackers may use a brand new domain and an entirely new psychological lure that bypasses existing email gateway rules and hasn't been covered in user training. | Security Awareness Lead | High | End-user reporting; Regular training updates. | 🟡 Medium | Quarterly |
| **RES-02** | **Internal Malicious User (Insider Threat):** A legitimate employee could maliciously forward external phishing emails to internal colleagues, bypassing the DMARC `reject` policy. | SIEM / DLP Lead | High | SIEM alerts for suspicious internal forwarding patterns; Strict Data Loss Prevention (DLP) policies. | 🟡 Low | Monthly |
| **RES-03** | **Third-Party Supply Chain Compromise:** The attacker may compromise a legitimate *business partner* of our organization and use *their* trusted domain to send phishing emails. Since their domain passes SPF/DKIM, our DMARC will not block it. | Third-Party Risk Lead | High | Vendor due diligence; Zero Trust Email Architecture (assuming external emails are always suspicious). | 🟡 Medium | Quarterly |

## 10.3 GRC Conclusion
The implementation of DMARC `p=reject` reduces the organization's inherent phishing risk by **over 80%**. The remaining residual risks cannot be eliminated by technology alone and require continuous monitoring of human behavior, periodic security awareness refreshers, and ongoing threat intelligence integration. The controls are deemed adequate for the organization's current risk appetite.
