# 9. MITRE ATT&CK Mapping

Mapping the phishing email findings to MITRE ATT&CK allows us to visualize the adversary's full kill chain and apply appropriate mitigations.

## Tactical Kill-Chain Mapping

| Vulnerability / Threat | MITRE Tactic | MITRE Technique ID | Technique Name | Adversary Action Enabled |
|:---|:---|:---|:---|:---|
| **Phishing Email (Advance Fee Fraud)** | **TA0001 (Initial Access)** | **T1566** | Phishing | The attacker impersonates a Diplomatic Agent using a spoofed domain to bypass reputation filters and create a legitimate-looking email. |
| **Absent Email Authentication (SPF FAIL, no DMARC)** | **TA0001 (Initial Access)** | **T1566** | Phishing | The lack of authentication controls *enabled* the initial access vector. The attacker exploited the trust inherent in email protocols. |
| **Gmail Reply-To Mismatch** | **TA0042 (Resource Development)** | **T1585.002** | Establish Accounts: Email Account | The attacker registers a free Gmail address (`mywoodforestbiz.7@gmail.com`) to collect victim replies and exfiltrate data, establishing a command & control channel completely outside the victim's corporate network. |

## Attack Chain Scenario (The "Real World" Threat)

1. **Reconnaissance (TA0043):** Attacker identifies the target organization and employee email addresses.
2. **Resource Development (TA0042):** Attacker registers a free Gmail address (`mywoodforestbiz.7@gmail.com`) and compromises a subdomain on a legitimate Russian government website (`54upr.rosreestr.ru`) to evade reputation-based filters.
3. **Initial Access (TA0001 - T1566):** Attacker sends an email impersonating a diplomat, exploiting authority and greed to lower the victim's defenses.
4. **Collection (TA0009):** Victim replies to the `@gmail.com` address, unknowingly providing their personal PII (Name, Phone, Address, Occupation).
5. **Impact (TA0040):** Attacker utilizes the collected PII for identity theft or sells the lead to other fraud syndicates.

**GRC Recommendation:** To disrupt this kill-chain:

1. Implement **DMARC `p=reject`** to block T1566 at the gateway.
2. Enable **DKIM signing** to ensure message integrity.
3. Enforce email gateway rules to **quarantine sender/reply-to domain mismatches** involving free email providers.
