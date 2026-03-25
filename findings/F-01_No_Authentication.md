# F-01 — No Authentication Required on Any Endpoint

| Field | Details |
|-------|---------|
| **Risk Level** | 🔴 CRITICAL |
| **CVSS Score** | 9.1 |
| **OWASP** | API1:2023 – Broken Object Level Authorization |
| **Priority** | Immediate |

## Description
Every endpoint is fully accessible without any authentication. No API key, OAuth token, or session credential is required to read any resource.

## Evidence
```
curl -s https://jsonplaceholder.typicode.com/users/1
→ Returns full user profile including name, email, phone, address, GPS — no auth required.

curl -s https://jsonplaceholder.typicode.com/todos?userId=1
→ Returns all private to-do items for a user — no credentials checked.
```

## Business Impact
Any anonymous attacker can read all user data, access private records, enumerate accounts, and scrape the entire database without any barrier.

## Fix
Implement JWT or OAuth 2.0 authentication. Apply auth middleware globally. Require valid tokens for all data access. Return HTTP 401 for unauthenticated requests.
