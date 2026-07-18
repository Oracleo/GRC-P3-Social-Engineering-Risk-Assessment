# 2. Incident Scope & Investigation Methodology

*  **Document Type:** Terms of Reference (ToR)
*  **Investigation Period:** July 29, 2023
*  **Investigation Owner:** Niladri Biswas

## 2.1 Purpose
To conduct a formal Social Engineering Risk Assessment and Incident Response. The objective is to analyze a reported phishing email, identify the root causes of its delivery, map the threat actor's infrastructure, and provide a prioritized remediation plan aligned with NIST CSF and ISO 27001 requirements.

## 2.2 In-Scope & Out-of-Scope Assets
| **Scope Element** | **Details** |
|:---|:---|
| **Incident Evidence** | Single phishing `.eml` file delivered to a user's inbox. |
| **Attack Vector** | Email - Advance Fee Fraud (419 Scam). |
| **Investigation Methods** | Manual header analysis, SPF/DKIM/DMARC verification, Threat Intel enrichment (VirusTotal, AbuseIPDB, WHOIS). |
| **Out-of-Scope** | Interaction with the attacker's infrastructure, links, or attachments. (Read-only analysis only). |

## 2.3 Technical Investigation Methodology (6 Phases)

**Phase 1 — Evidence Preservation**
The email was preserved in `.eml` format to maintain the integrity of the complete header chain and message content, ensuring forensic auditability.

**Phase 2 — Header Analysis & Authentication Verification**
SPF, DKIM, and DMARC authentication results were manually extracted from the email headers. The SMTP routing path was traced to identify the originating sender IP and the relay domain.

**Phase 3 — IOC Extraction**
Malicious indicators were documented, including: Sender IP, Mail Relay Domain, Reply-To Address, and Spoofed Sender Domain.

**Phase 4 — Threat Intelligence Enrichment**
Each IOC was submitted to external threat intelligence platforms:
*   **VirusTotal:** To check for IP reputation and malicious vendor flags.
*   **AbuseIPDB:** To correlate the IP against past abuse reports.
*   **WHOIS:** To identify domain registration details and ownership of the relay infrastructure.

**Phase 5 — Social Engineering Content Assessment**
The email body was analyzed for manipulative tactics (Authority exploitation, greed, urgency, and information harvesting).

**Phase 6 — GRC Documentation**
The findings were documented in a formal incident report, mapped to ISO 27001 Annex A controls, NIST CSF functions, and MITRE ATT&CK TTPs.

## 2.4 Constraints & Limitations
*   **Passive Investigation:** As per Incident Response best practices for a reported sample, no active engagement was made with the attacker's infrastructure or the included Gmail address. This limits the ability to identify additional infrastructure clusters.
*   **Automated Tool Limitations:** VirusTotal showed 0 detections for the sender IP, highlighting that reputation-based threat intel can produce false negatives for new or targeted campaigns.
