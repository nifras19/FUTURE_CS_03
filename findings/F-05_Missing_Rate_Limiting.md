# F-05 — Missing Rate Limiting on Write Endpoints

| Field | Details |
|-------|---------|
| **Risk Level** | 🟡 MEDIUM |
| **CVSS Score** | 5.3 |
| **OWASP** | API4:2023 – Unrestricted Resource Consumption |
| **Priority** | Week 2 |

## Description
While read endpoints show basic rate limit headers, write endpoints (POST/PUT/DELETE) accept unlimited requests with no throttling or abuse prevention.

## Evidence
```
curl -sI https://jsonplaceholder.typicode.com/posts
→ x-ratelimit-limit: 1000  (GET only)

curl -sI -X POST https://jsonplaceholder.typicode.com/posts
→ No rate limit headers on write endpoints
```

## Business Impact
Attackers can flood write endpoints with unlimited requests — exhausting server resources, spamming the database with malicious content, or abusing the API for automated fraud at scale.

## Fix
Apply rate limiting to ALL endpoints especially writes. Implement per-IP and per-user limits. Return HTTP 429 Too Many Requests with Retry-After header when exceeded.
