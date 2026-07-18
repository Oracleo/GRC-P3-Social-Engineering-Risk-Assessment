# Phishing Email Incident Report

## Summary
A phishing email impersonating a diplomatic agent was detected attempting to scam the recipient by requesting personal information and claiming delivery of $10.5 million USD.

## Detection Method
Manual email header analysis identified **SPF failure**, a spoofed sender domain, and a mismatched Reply-To address.

## Indicators of Compromise (IOC)

- **Sender IP:** `109.202.24.52`
- **Relay Domain:** `54upr.rosreestr.ru`
- **Reply-To Email:** `mywoodforestbiz.7@gmail.com`
- **Spoofed Sender Domain:** `postfiji.com.fj` (The attacker forged this domain to make the email appear legitimate; the domain itself was not compromised, only spoofed).

## Technical Analysis

- **SPF:** Fail
- **DKIM:** None
- **DMARC:** None
- **Gmail Reply-To mismatch:** Confirmed
- **Content:** Scam content requesting sensitive PII (Name, Phone, Address).

**VirusTotal Assessment:** The sender IP (`109.202.24.52`) showed **0/93 vendor detections** at the time of analysis. This is a critical **false negative**. While the automated reputation score was clean, cross-referencing the authentication failures (SPF FAIL, no DKIM, no DMARC) and the malicious Reply-To mismatch confirmed malicious intent with high confidence.

## Threat Intelligence

- **Infrastructure:** Traced to a compromised Russian relay domain (`rosreestr.ru`), a legitimate government entity whose subdomain was abused for phishing.
- **Pattern:** Known scam pattern (Advance Fee Fraud / 419 Scam).

## MITRE ATT&CK Mapping

- T1566 – Phishing

## Impact

- **Immediate:** Potential PII exposure (Name, Phone, Address, Occupation).
- **Escalation:** Credential theft, Business Email Compromise (BEC), and financial fraud.

## Response Actions

- **Containment:** Blocked sender IP `109.202.24.52` and relay domain `54upr.rosreestr.ru` at the perimeter firewall and email gateway.
- **Remediation:** Recommended user awareness training and strict DMARC enforcement (`p=reject`).
- **Prevention:** Suggested email gateway rule updates to quarantine messages with Reply-To mismatches.

## Severity
**🟡 Medium**

## Status
**✅ Closed**
