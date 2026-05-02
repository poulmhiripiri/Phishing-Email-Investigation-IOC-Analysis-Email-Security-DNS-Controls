# Phishing Email Investigation, IOC Analysis & Email Security DNS Controls

## Project Overview

This repository presents a practical, SOC-style phishing email investigation and Indicator of Compromise (IOC) analysis project by **Poul Mhiripiri**. The project demonstrates how suspicious emails are collected, analysed, enriched with threat intelligence, and converted into defensive recommendations for an organisation.

The investigation focuses on phishing email forensics, sender validation, suspicious URL analysis, sender IP reputation, sandbox behaviour, and DNS-based email security controls including **MX, SPF, DKIM and DMARC**.

The project was completed in a controlled lab environment using sample phishing emails and redacted evidence screenshots.

---

## Recruiter Summary

This project is designed to demonstrate that the author has practical experience across **email security, DNS, SOC investigation, infrastructure security and cloud security engineering**.

The author has also successfully registered and managed the domain **poulmhiripiri.co.zw on AWS**, using the domain for cloud and email-related portfolio work, including email addresses under **@poulmhiripiri.co.zw**.

In another cloud security project on this GitHub profile, the author designed and deployed a secure cloud-native architecture on AWS using:

- GitHub and AWS CodePipeline for CI/CD
- Private Amazon S3 access through CloudFront Origin Access Control (OAC)
- TLS encryption using AWS Certificate Manager (ACM)
- DNS routing using Amazon Route 53
- Secure CDN delivery using Amazon CloudFront

This phishing/email security project connects well with that cloud project because secure email operations require strong DNS governance, domain ownership, mail authentication, secure routing and continuous monitoring.

The author also has a comprehensive background working in an **ISP environment**, supporting hosted corporate client domains and DNS services, and later in a **banking environment**, managing email infrastructure, DNS records and customised internal URLs for easier access by business users.

---

## Skills Demonstrated

- Phishing email triage and investigation
- Email header analysis and transmission path review
- IOC extraction and classification
- SPF, DKIM and DMARC analysis
- MX record and DNS email-security validation
- Sender IP and domain reputation checks
- URL analysis and behavioural inspection
- Sandbox-based payload analysis
- SOC-style reporting and recommendations
- Infrastructure security and email governance
- Cloud/domain ownership awareness using AWS Route 53 and related services

---

## Tools Used

| Tool | Purpose |
|---|---|
| PhishTool | Email forensic analysis, header review and phishing triage |
| MXToolbox | Email header analysis and DNS record validation |
| VirusTotal | URL, domain, IP and file reputation checks |
| URLScan.io | URL behaviour and web infrastructure analysis |
| Cisco Talos Intelligence | Sender IP and domain reputation analysis |
| AbuseIPDB | IP abuse history and reputation validation |
| CAPE Sandbox / Zenbox | Attachment and payload behavioural analysis |
| dig / DNS tools | MX, SPF, DKIM and DMARC record validation |
| AWS Route 53 | Domain registration and DNS management experience |
| AWS ACM / CloudFront / S3 / CodePipeline | Supporting cloud security and DevSecOps portfolio experience |

---

## Repository Structure

```text
phishing-email-investigation-ioc-analysis/
├── README.md
├── docs/
│   ├── phishing-investigation-report-by-poul-mhiripiri.pdf
│   ├── investigation-methodology.md
│   ├── email-security-dns-controls.md
│   ├── mitigation-recommendations.md
│   └── recruiter-note.md
├── iocs/
│   ├── ioc-summary.csv
│   ├── malicious-urls.txt
│   ├── suspicious-domains.txt
│   ├── suspicious-ip-addresses.txt
│   └── suspicious-email-addresses.txt
├── screenshots/
│   ├── phishtool/
│   ├── virustotal/
│   ├── urlscan/
│   ├── cisco-talos/
│   ├── abuseipdb/
│   ├── sandbox-analysis/
│   ├── dns-record-checks/
│   └── use-case-evidence/
├── diagrams/
│   ├── phishing-investigation-workflow.mmd
│   └── email-security-dns-flow.mmd
└── templates/
    ├── phishing-analysis-template.md
    └── soc-incident-report-template.md
```

---

## Investigation Methodology

### 1. Collection

Sample phishing emails were downloaded and preserved for investigation.

### 2. Header and Metadata Analysis

Email headers were reviewed to identify:

- Sender identity anomalies
- From and Return-Path mismatch
- Reply-To manipulation
- SPF, DKIM and DMARC failures
- Suspicious email transmission hops
- Originating IP addresses

### 3. IOC Extraction

Indicators of Compromise were extracted from email bodies, headers, links and attachments.

### 4. Threat Intelligence Enrichment

Extracted IOCs were validated using VirusTotal, URLScan, Cisco Talos, AbuseIPDB and sandbox analysis.

### 5. Risk Classification

Each email was assessed based on authentication failure, malicious URL reputation, sender reputation, sandbox behaviour and likely user impact.

### 6. Mitigation Recommendations

Recommendations were produced for email gateway controls, DNS authentication, SOC monitoring, endpoint review and user awareness.

---

## Key Findings

### Use Case 1 - Failed Authentication and Malicious URL

- From and Return-Path did not align.
- Email authentication failed.
- Embedded URL was flagged as phishing or malicious by multiple vendors.
- URLScan showed suspicious HTTP activity and external infrastructure.
- Cisco Talos showed poor sender reputation for the originating IP.
- No attachment was present; the primary threat vector was a malicious link.

**Risk Rating:** High

**Likely Attack Type:** Credential harvesting / phishing landing page

---

### Use Case 2 - Missing SPF, DKIM and DMARC

- No SPF record was present.
- No DKIM authentication was detected.
- No DMARC policy was available.
- Embedded URLs were flagged by several vendors.
- Suspicious domain activity was identified.
- Some infrastructure was not heavily flagged, showing why reputation alone is not enough.

**Risk Rating:** High

**Likely Attack Type:** Spoofing and malicious URL delivery

---

### Use Case 3 - Reply-To Manipulation and Suspicious Origin

- Sign-in activity was associated with Russia/Moscow.
- From field appeared suspicious.
- Reply-To used a Gmail account that could be disposable.
- Sending domain lacked SPF/DKIM controls.
- Originating infrastructure was hosted outside the expected sender environment.
- VirusTotal did not heavily flag the IP, demonstrating the importance of context-based analysis.

**Risk Rating:** Medium to High

**Likely Attack Type:** Social engineering, impersonation or credential harvesting

---

## Email Security DNS Lessons

Strong email DNS configuration is essential to reducing phishing and spoofing risk.

### MX Records

Define which mail servers receive email for a domain.

### SPF

Defines which mail servers are authorised to send email for a domain.

### DKIM

Digitally signs email so receiving systems can verify message authenticity and integrity.

### DMARC

Uses SPF and DKIM alignment to determine whether an email should be delivered, quarantined or rejected.

Recommended DMARC maturity path:

```text
p=none -> monitor reports
p=quarantine -> send suspicious emails to spam/quarantine
p=reject -> reject unauthenticated emails
```

---

## Defensive Recommendations

- Implement SPF, DKIM and DMARC for all domains.
- Gradually move DMARC from `p=none` to `p=quarantine` and then `p=reject`.
- Maintain an inventory of authorised third-party senders.
- Review MX records and remove obsolete mail servers.
- Enable secure email gateway URL rewriting and time-of-click protection.
- Enable attachment sandboxing.
- Block confirmed malicious URLs, domains and IPs.
- Search the email estate for similar messages.
- Correlate email events with endpoint, proxy and SIEM logs.
- Train users to report suspicious emails.
- Monitor for domain spoofing and lookalike domains.

---

## Evidence Included

Evidence screenshots have been organised under the `screenshots/` folder:

- PhishTool analysis
- MXToolbox and DNS checks
- VirusTotal verdicts
- URLScan analysis
- Cisco Talos reputation analysis
- Sandbox analysis
- Use case evidence pages

The full project report is available in:

```text
docs/phishing-investigation-report-by-poul-mhiripiri.pdf
```

---

## Disclaimer

This repository is for cybersecurity education, portfolio demonstration and defensive security purposes only. The investigation was performed in a controlled lab environment using sample phishing emails. Sensitive information should be redacted before public publication.

---

## Author

**Poul Mhiripiri**  
Network, Infrastructure, Cloud and Cybersecurity Professional  
Portfolio domain: `poulmhiripiri.co.uk`  
AWS-managed domain used for cloud/email portfolio work: `poulmhiripiri.co.zw`
