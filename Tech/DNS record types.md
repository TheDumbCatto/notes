# A & AAAA records

## A (Address) records

Points a domain name to an IPv4 address.

## AAAA records

Same as A records, but for IPv6.

# CNAME & DNAME records

## CNAME (Canonical NAME)

Points subdomains to an existing A record. Can't be used with root domains
> E.g: Can't be used for example.com, but example.com can have CNAME records containing subdomains such as a.example.com

## DNAME

Creates CNAME for all subdomains of an A record and links those CNAMEs to CNAMEs of another A record.
> E.g: DNAME on domain.com pointed to example.com would link a.domain.com, b.domain.com to a.example.com and b.domain.com, respectively.

# MX, PTR & SPF records

## MX (Mail Xchange)

Steers an email domain (e.g. @gmail.com) to an appropriate mail server registered for that email domain.

## SPF

Points an email domain to a list of authorized sender's IPs. Only the mail servers whose IP is in this list are allowed to send mails using that email domain.

## PTR

Points an IP to its associated domain. Commonly used in mail spam prevention by pointing a mail server's IP to the specific email domain that the mail from that server can be sent from.