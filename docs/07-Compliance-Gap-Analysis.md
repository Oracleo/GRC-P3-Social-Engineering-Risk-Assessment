# 7. Compliance Gap Analysis (ISO 27001, NIST CSF, GDPR)

This document maps the identified phishing incident and control gaps to specific regulatory frameworks.

## ISO 27001:2022 Annex A Mappings
| Control ID | Control Name | Gap Evidence | Compliance Status |
|:---:|:---|:---|:---:|
| **A.8.16** | Monitoring Activities | The phishing email reached the inbox unimpeded, indicating a gap in inbound email security monitoring and filtering. | 🟡 **Control Gap** |
| **A.8.6** | Capacity Management | Lack of DMARC `p=reject` undermines the organization's capacity to manage its electronic communications securely. | 🔴 **Non-Compliant** |
| **A.6.3** | Information Security Awareness | Users are not adequately trained to identify Reply-To address mismatches or authority-based social engineering (Advance Fee Fraud). | 🟡 **Control Gap** |
| **A.5.24** | Incident Management Planning | While the incident was reported, formalized containment and eradication steps for spoofed emails need integration with the IR plan. | 🟡 **Control Gap** |

## NIST Cybersecurity Framework (CSF) Mappings
| NIST Function | NIST Category | Gap Evidence |
|:---|:---|:---|
| **IDENTIFY (ID)** | ID.RA-2 (Cybersecurity Risk Assessment) | IT did not previously assess the risk of an email spoofing attack against the organization's email domain. The spoofed domain `postfiji.com.fj` was used to impersonate a trusted external entity, exposing a gap in how the risk assessment accounted for external domain spoofing vectors. |
| **PROTECT (PR)** | PR.AT-1 (Awareness and Training) | Users were not aware of this specific 419 scam and spoofing technique. |
| **DETECT (DE)** | DE.CM-3 (Personnel Activity Monitoring) | End-user report was the detection vector, rather than an automated email gateway alert. |
| **RESPOND (RS)** | RS.AN-1 (Notifications from Detection Systems are Investigated) | Incident report filed and investigated based on manual email header analysis. |

## GDPR (General Data Protection Regulation) Implications
If an employee had replied to this email, it would constitute a data breach (Article 4(12)), as the attacker would have obtained the employee's PII (Name, Phone, Address, Occupation). Failure to implement DMARC `p=reject` to prevent phishing constitutes a failure of "appropriate technical measures" under **Article 32 (Security of Processing)**.
