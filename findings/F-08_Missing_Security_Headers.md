# F-08 — Missing Critical Security Response Headers

| Field | Details |
|-------|---------|
| **Risk Level** | 🔵 INFO |
| **CVSS Score** | 2.0 |
| **OWASP** | API7:2023 – Security Misconfiguration |
| **Priority** | Week 4 |

## Description
Several recommended security response headers are absent from all API responses.

## Evidence
```
curl -sI https://jsonplaceholder.typicode.com/posts

Present:  x-content-type-options: nosniff  ✅
Missing:  Content-Security-Policy          ❌
Missing:  Strict-Transport-Security        ❌
Missing:  X-Frame-Options                  ❌
Missing:  Permissions-Policy               ❌
Missing:  Referrer-Policy                  ❌
```

## Business Impact
Reduced defence-in-depth. Missing HSTS exposes connections to SSL stripping. Missing CSP allows content injection in browser-based API clients.

## Fix
Add: Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
Add: Referrer-Policy: no-referrer
Add: Permissions-Policy: geolocation=(), microphone=()
Keep: x-content-type-options: nosniff (already present - good)
