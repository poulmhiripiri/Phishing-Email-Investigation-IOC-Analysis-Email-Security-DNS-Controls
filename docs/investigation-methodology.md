# Investigation Methodology

## Objective

Investigate suspicious phishing emails, extract Indicators of Compromise (IOCs), validate them using threat intelligence platforms, and recommend mitigation actions.

## Workflow

1. Preserve the original email sample.
2. Upload the email to PhishTool for structured analysis.
3. Review headers, sender details and authentication results.
4. Identify From, Return-Path and Reply-To anomalies.
5. Extract URLs, domains, IP addresses, file hashes and suspicious email addresses.
6. Validate IOCs using VirusTotal, URLScan, Cisco Talos and AbuseIPDB.
7. Detonate or analyse suspicious files using CAPE Sandbox/Zenbox where relevant.
8. Assign risk rating based on technical evidence.
9. Recommend containment and prevention controls.
10. Document evidence and lessons learned.

## Risk Factors Considered

- Failed SPF, DKIM or DMARC
- Missing DMARC policy
- Mismatched From and Return-Path
- Suspicious Reply-To address
- Malicious URL verdict
- Poor sender IP reputation
- Suspicious sandbox behaviour
- Suspicious hosting provider or geography
- Credential harvesting indicators
- Social engineering language
