# Phishing Email Incident Report

## Summary
A phishing email impersonating a diplomatic agent was detected attempting to scam the recipient by requesting personal information and claiming delivery of $10.5 million USD.

## Detection Method
Manual email header analysis identified SPF failure, spoofed sender domain, and mismatched Reply-To address.

## Indicators of Compromise (IOC)

- Sender IP: 109.202.24.52  
- Relay Domain: 54upr.rosreestr.ru  
- Reply-To Email: mywoodforestbiz.7@gmail.com  
- Fake Sender Domain: postfiji.com.fj  

## Technical Analysis

- SPF: Fail  
- DKIM: None  
- DMARC: None  
- Gmail Reply-To mismatch  
- Scam content requesting sensitive information  

VirusTotal and AbuseIPDB showed low reputation, however content analysis and authentication failures confirmed malicious intent.

## Threat Intelligence

- Infrastructure traced to Russian relay domain  
- Known scam pattern (Advance Fee Fraud / 419 Scam)

## MITRE ATT&CK Mapping

- T1566 – Phishing

## Impact

Potential credential theft and financial fraud.

## Response Actions

- Blocked sender IP and domain  
- Reported phishing attempt  
- Recommended user awareness training  
- Suggested email gateway rule updates  

## Severity

Medium

## Status

Closed
