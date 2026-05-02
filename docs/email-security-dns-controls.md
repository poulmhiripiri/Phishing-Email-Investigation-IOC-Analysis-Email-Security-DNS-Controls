# Email Security DNS Controls

## Why DNS Matters in Email Security

DNS records are central to secure email delivery. They help receiving mail systems determine where to deliver email, which systems are authorised to send email, and how to handle unauthenticated messages.

## MX Records

Mail Exchange records define the mail servers responsible for receiving email for a domain.

Example:

```text
example.com MX 10 mail.example.com
```

Lower MX priority values are preferred first.

## SPF Records

Sender Policy Framework records define which IP addresses or platforms can send email on behalf of a domain.

Example:

```text
v=spf1 include:spf.protection.outlook.com -all
```

A strong SPF policy helps reduce unauthorised sending, but SPF alone is not enough because it does not fully protect the visible From address.

## DKIM Records

DomainKeys Identified Mail signs outbound messages using a private key. Receiving systems verify the signature using the public key published in DNS.

DKIM helps verify:

- The sender domain authorised the message
- The message was not modified in transit
- The domain has cryptographic ownership of the signing process

## DMARC Records

DMARC links SPF and DKIM to the visible From domain and defines what should happen when authentication fails.

Example:

```text
v=DMARC1; p=quarantine; rua=mailto:dmarc-reports@example.com
```

Common DMARC policies:

| Policy | Action |
|---|---|
| p=none | Monitor only |
| p=quarantine | Send suspicious messages to spam or quarantine |
| p=reject | Reject unauthenticated messages |

## Recommended Maturity Path

```text
1. Publish SPF for approved senders
2. Enable DKIM signing
3. Start DMARC at p=none
4. Review DMARC aggregate reports
5. Fix legitimate sender alignment issues
6. Move to p=quarantine
7. Move to p=reject
8. Monitor continuously
```

## Link to AWS Domain Experience

The author has practical domain/DNS experience through ISP and banking environments, and has also registered and managed `poulmhiripiri.co.zw` on AWS. This supports practical understanding of Route 53 DNS hosting, domain ownership, DNS routing, and email-domain governance.
