# 5. Risk Register

This register serves as the master document for tracking the identified phishing incident and the underlying control gaps.

## Risk Scoring Context
*   **Asset:** Organizational email system (inbound and outbound).
*   **Threat:** External adversary utilizing social engineering to gain initial access or commit fraud.
*   **Vulnerability:** Absent DMARC enforcement, weak SPF/DKIM configuration, and potential end-user susceptibility to authority-based social engineering.

## Risk Register Entries
| Priority | Vulnerability / Threat | Likelihood | Business Impact | Risk Score | Recommended Owner |
|:---:|:---|:---:|:---|:---|:---|
| **P1** | **Absent DMARC Enforcement (`p=reject`)** | Very High (External adversaries can spoof your domain at will) | **Critical:** Brand reputation damage, BEC (Business Email Compromise) financial fraud, and data theft. | Critical | Security Architect |
| **P2** | **Users susceptible to Advance Fee Fraud (419 Scams)** | High (End-users are the last line of defense) | **Medium:** PII leakage, credential theft, and identity fraud | High | HR / InfoSec Trainer |
| **P2** | **Compromised Third-Party Relay (Rosreestr.ru)** | Medium | **Medium:** Attackers utilizing "trusted" domains to bypass reputation filters. | Medium | Threat Intel Lead |
| **P2** | **Spoofed Sender Domain (`postfiji.com.fj`)** | Medium (Requires attacker to register a similar domain or compromise a trusted third party) | **Low:** Creates false trust, enabling the phishing email to bypass basic reputation filters. | Low | Email Gateway Admin / Threat Intel |
