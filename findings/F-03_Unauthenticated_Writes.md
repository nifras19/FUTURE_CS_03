# F-03 — Unauthenticated Write & Delete Operations

| Field | Details |
|-------|---------|
| **Risk Level** | 🟠 HIGH |
| **CVSS Score** | 7.5 |
| **OWASP** | API5:2023 – Broken Function Level Authorization |
| **Priority** | Week 1 |

## Description
All write operations — creating, updating, and deleting resources — are accepted without any authentication or ownership verification.

## Evidence
```
curl -X POST https://jsonplaceholder.typicode.com/posts \
  -H "Content-Type: application/json" \
  -d '{"title":"Injected","body":"Content","userId":1}'
→ HTTP 201  {"id": 101}  ← Accepted without auth

curl -X DELETE https://jsonplaceholder.typicode.com/posts/1
→ HTTP 200  {}  ← Deleted without auth or ownership check
```

## Business Impact
Any attacker can create malicious content, modify other users' records, or delete data — causing data integrity failure and availability disruption.

## Fix
Require authentication for all non-GET endpoints. Implement ownership checks before allowing modification or deletion. Return HTTP 401 / HTTP 403 appropriately.
