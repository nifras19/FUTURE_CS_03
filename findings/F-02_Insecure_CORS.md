# F-02 — Insecure CORS — Wildcard Origin with Credentials Enabled

| Field | Details |
|-------|---------|
| **Risk Level** | 🔴 HIGH |
| **CVSS Score** | 8.2 |
| **OWASP** | API7:2023 – Security Misconfiguration |
| **Priority** | Week 1 |

## Description
The API reflects the caller's Origin header verbatim combined with Access-Control-Allow-Credentials: true — allowing any website to make credentialed cross-origin requests and read the full response.

## Evidence
```
curl -sI -H "Origin: https://evil-attacker.com" https://jsonplaceholder.typicode.com/posts
→ access-control-allow-origin: https://evil-attacker.com  ← REFLECTED
→ access-control-allow-credentials: true  ← DANGEROUS COMBINATION
```

## Business Impact
An attacker's website can silently send authenticated API requests on behalf of visiting users — exposing private data without the user's knowledge.

## Fix
Replace reflected origin with a strict allowlist:
Access-Control-Allow-Origin: https://yourdomain.com
Never combine wildcard/reflected origin with Access-Control-Allow-Credentials: true.
