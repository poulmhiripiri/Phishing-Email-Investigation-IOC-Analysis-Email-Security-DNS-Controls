# Mitigation and Prevention Recommendations

## Immediate Containment

- Quarantine confirmed phishing emails.
- Search all mailboxes for the same sender, subject, URL, domain or message ID.
- Block malicious URLs at the secure email gateway, proxy and DNS filtering layer.
- Block confirmed malicious domains and IP addresses.
- Identify users who clicked links or submitted credentials.
- Reset passwords and revoke sessions where compromise is suspected.
- Review endpoint telemetry for suspicious activity.

## Email Security Gateway Improvements

- Enable anti-spoofing protection.
- Enable impersonation protection for executives and finance users.
- Enable URL rewriting and time-of-click protection.
- Enable attachment sandboxing.
- Add external sender banners.
- Quarantine emails with failed DMARC and suspicious content.

## DNS and Domain Controls

- Publish SPF records for all authorised senders.
- Enable DKIM signing for all outbound platforms.
- Implement DMARC reporting.
- Move DMARC gradually from `p=none` to `p=quarantine` and `p=reject`.
- Review MX records regularly.
- Monitor for lookalike domains.
- Maintain an authorised sender inventory.

## SOC Monitoring

- Alert on repeated DMARC failures.
- Alert on From and Reply-To mismatches.
- Alert on suspicious newly registered domains.
- Correlate email logs with proxy, DNS and endpoint logs.
- Feed confirmed IOCs into SIEM watchlists.

## User Awareness

- Train users to identify suspicious sender domains.
- Encourage reporting instead of deleting suspicious emails.
- Run phishing simulation campaigns.
- Teach users not to enter credentials after clicking email links.
