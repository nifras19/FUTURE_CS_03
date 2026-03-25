# F-04 — Excessive Data Exposure & User Enumeration (IDOR)

| Field | Details |
|-------|---------|
| **Risk Level** | 🟠 MEDIUM |
| **CVSS Score** | 6.5 |
| **OWASP** | API3:2023 – Broken Object Property Level Authorization |
| **Priority** | Week 2 |

## Description
The /users endpoint returns complete PII including full name, email, phone, physical address with GPS coordinates, and company name. Sequential integer IDs allow full database enumeration.

## Evidence
```
curl -s https://jsonplaceholder.typicode.com/users/1
→ name, username, email, phone, address.street, address.city,
  address.zipcode, address.geo.lat, address.geo.lng, company.name

All 10 users enumerated via sequential IDs 1-10 — no access control.
```

## Business Impact
Exposes PII of all users to any anonymous caller. Sequential IDs enable automated scraping of the entire user database. GDPR data protection breach in a regulated environment.

## Fix
Return only minimum required fields. Use non-sequential UUIDs as identifiers. Apply field-level access control — restrict sensitive fields to authenticated users only.
