# 6. Asset Business Criticality & Context Analysis

In a professional GRC environment, a reported phishing email is not just a "spam complaint." It is an attack on a critical business asset. For the purposes of this risk engagement, we contextualize the **Organizational Email System** as follows:

## 6.1 Asset Profile
| Asset Attribute | Assigned Context |
|:---|:---|
| **Asset Type** | Enterprise Email System (Exchange / Office 365 / Mimecast). |
| **Business Function** | Primary communication channel for invoicing, financial wire instructions, and employee PII handling. |
| **Data Sensitivity** | **High.** Handles outbound wire transfers and PII for HR records. |
| **Regulatory Footprint** | Subject to **GDPR** (if EU employee data is processed) and local financial fraud regulations. |
| **Operational Criticality** | Mission-critical. Successful BEC can siphon millions in wire transfers. |

## 6.2 Impact Analysis Matrix
| Threat Scenario | Operational Impact | Compliance Impact | Financial/Reputational Impact |
|:---|:---|:---|:---|
| **Phishing (T1566)** leading to BEC financial fraud | Unauthorized wire transfers from finance department. | Violates GDPR Article 32 if PII is exfiltrated via a compromised email account. | **~$100,000+** direct financial loss. Severe loss of client trust. |
| **Compromised Third-Party Relay (`rosreestr.ru`)** | Bypasses reputation-based filtering, allowing advanced phishing attacks. | Violates NIST ID.RA-2 (Third-party risk assessment). | Harder to detect future attacks, leading to eventual data breach. |

## 6.3 Conclusion on Priority Scoring
The lack of DMARC is escalated to a **Critical P1** because it is a foundational control. If an adversary can spoof your domain at will, every single employee is at risk of a targeted BEC attack. The priority matrix in `03-Risk-Register.md` is driven by the high financial value of wire transfers occurring over this channel.
