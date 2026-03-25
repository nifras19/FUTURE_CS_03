# 🔐 FUTURE_CS_03 — API Security Risk Analysis

<div align="center">

![API Security](https://img.shields.io/badge/API-Security%20Audit-red?style=for-the-badge&logo=shield&logoColor=white)
![OWASP](https://img.shields.io/badge/OWASP-API%20Top%2010%202023-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![Task](https://img.shields.io/badge/Task-03-orange?style=for-the-badge)

**Mohammed Nifras | CIN: FIT/FEB26/CS6509**
*Future Interns — Cyber Security Internship Program*

</div>

---

## 📋 Task Overview

This repository contains all deliverables for **Task 03** of the Future Interns Cyber Security Internship.
The objective was to perform a professional **API Security Risk Analysis** on a public REST API, identify common API security vulnerabilities, classify risks using the **OWASP API Security Top 10 (2023)** framework, and produce a formal security report — mirroring real-world work done by AppSec consultants and security agencies.

> ⚠️ **Ethical Notice:** All testing was passive and read-only. No exploitation, authentication bypass, brute-force, or denial-of-service techniques were used. This assessment fully complies with OWASP ethical testing guidelines.

---

## 🎯 Target API

| Field | Details |
|-------|---------|
| **API Name** | JSONPlaceholder Public REST API |
| **Base URL** | `https://jsonplaceholder.typicode.com` |
| **Type** | Public demo REST API (Express.js / Node.js) |
| **CDN / Proxy** | Cloudflare |
| **Resources Tested** | /posts /comments /albums /photos /todos /users |
| **Assessment Date** | March 24, 2026 |

---

## 🔍 Findings Summary

| ID | Finding | Risk | CVSS | OWASP API Top 10 |
|----|---------|------|------|-----------------|
| F-01 | No Authentication Required on Any Endpoint | 🔴 CRITICAL | 9.1 | API1:2023 |
| F-02 | Insecure CORS — Wildcard with Credentials Enabled | 🔴 HIGH | 8.2 | API7:2023 |
| F-03 | Unauthenticated Write & Delete Operations | 🟠 HIGH | 7.5 | API5:2023 |
| F-04 | Excessive Data Exposure / IDOR via User Enumeration | 🟠 MEDIUM | 6.5 | API3:2023 |
| F-05 | Missing Rate Limiting on Write Endpoints | 🟡 MEDIUM | 5.3 | API4:2023 |
| F-06 | All HTTP Methods Permitted on All Endpoints | 🟡 LOW | 4.0 | API5:2023 |
| F-07 | Bulk Data Retrieval — No Pagination Enforcement | 🟡 LOW | 3.5 | API4:2023 |
| F-08 | Missing Critical Security Response Headers | 🔵 INFO | 2.0 | API7:2023 |

**Total: 8 Findings — 1 Critical | 2 High | 2 Medium | 2 Low | 1 Info**
**API Security Score: 17 / 100 — MODERATE-HIGH RISK**

---

## 🛠️ Tools & Standards Used

| Tool / Standard | Purpose |
|----------------|---------|
| `cURL` | HTTP endpoint testing, header inspection, method testing |
| Python (json) | API response parsing and data analysis |
| Browser DevTools | Request/response inspection |
| OWASP API Security Top 10 (2023) | Vulnerability classification framework |
| CVSS v3.1 | Severity scoring |
| OWASP Testing Guide | Methodology reference |

---

## 📁 Repository Structure

```
FUTURE_CS_03/
├── README.md                            # This file
├── API_Security_Risk_Analysis_Report.pdf  # Full professional report
├── findings/
│   ├── F-01_No_Authentication.md
│   ├── F-02_Insecure_CORS.md
│   ├── F-03_Unauthenticated_Writes.md
│   ├── F-04_Excessive_Data_Exposure.md
│   ├── F-05_Missing_Rate_Limiting.md
│   ├── F-06_Unrestricted_HTTP_Methods.md
│   ├── F-07_No_Pagination.md
│   └── F-08_Missing_Security_Headers.md
└── evidence/
    ├── headers_raw.txt
    ├── unauthenticated_access.txt
    └── cors_test.txt
```

---

## 🗺️ Remediation Roadmap

```
Immediate  → F-01: Implement JWT / OAuth 2.0 authentication globally
Week 1     → F-02: Fix CORS — strict origin allowlist, remove credentials flag
Week 1     → F-03: Require auth + ownership check on all write operations
Week 2     → F-04: Use UUIDs, restrict PII fields, apply object-level auth
Week 2     → F-05: Rate limit all endpoints — return HTTP 429 on abuse
Week 3     → F-06: Restrict HTTP methods per endpoint — return 405 otherwise
Week 3     → F-07: Enforce pagination — max 50 records, require page params
Week 4     → F-08: Add HSTS, Referrer-Policy, Permissions-Policy headers
```

---

## 🔐 Ethical Statement

- ✅ Passive only — no active exploitation or attacks
- ✅ Read-only — no data modification or deletion
- ✅ No brute-force or credential guessing
- ✅ No denial-of-service or traffic flooding
- ✅ OWASP ethical testing guidelines followed throughout

---

## 👤 About

**Mohammed Nifras**
Cyber Security Intern @ Future Interns
Internship ID: FIT/FEB26/CS6509

[![GitHub](https://img.shields.io/badge/GitHub-nifras19-black?style=flat&logo=github)](https://github.com/nifras19)

---

<div align="center">

*Future Interns Cyber Security Internship — Task 03*
*March 2026*

</div>
