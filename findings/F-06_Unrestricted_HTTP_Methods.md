# F-06 — All HTTP Methods Permitted on All Endpoints

| Field | Details |
|-------|---------|
| **Risk Level** | 🟡 LOW |
| **CVSS Score** | 4.0 |
| **OWASP** | API5:2023 – Broken Function Level Authorization |
| **Priority** | Week 3 |

## Description
OPTIONS response reveals GET, HEAD, PUT, PATCH, POST, and DELETE are all globally permitted. No method-level restrictions are applied per endpoint or resource type.

## Evidence
```
curl -sI -X OPTIONS https://jsonplaceholder.typicode.com/posts
→ access-control-allow-methods: GET,HEAD,PUT,PATCH,POST,DELETE

GET /posts/1  → 200   PUT /posts/1   → 200
PATCH /posts/1 → 200  DELETE /posts/1 → 200
```

## Business Impact
Unnecessarily large attack surface. Violates principle of least privilege — only required methods should be allowed per endpoint.

## Fix
Restrict HTTP methods per endpoint using an allowlist. Return HTTP 405 Method Not Allowed for disallowed methods.
