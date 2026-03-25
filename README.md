# FUTURE_CS_03 — API Security Risk Analysis

**Internship Task 03 | CyberSecurity Domain**

## Overview
A professional, consultant-grade **API Security Risk Analysis** performed on the JSONPlaceholder public REST API.

## What Was Done
- Live testing of public API endpoints using HTTP inspection
- Analyzed authentication, CORS, headers, data exposure, and input validation
- Identified **6 security risks** mapped to the OWASP API Security Top 10
- Generated a full professional PDF report with findings, business impact, and remediation steps

## Findings Summary

| # | Finding | Severity |
|---|---------|----------|
| 1 | No Authentication on Any Endpoint | 🔴 Critical |
| 2 | Unauthenticated Write and Delete Access | 🔴 Critical |
| 3 | Excessive Data Exposure in API Responses | 🟠 High |
| 4 | Wildcard CORS Policy (Reflects Any Origin) | 🟠 High |
| 5 | Missing Critical HTTP Security Headers | 🟡 Medium |
| 6 | No Input Size / Payload Validation | 🟡 Medium |

**Overall Risk Rating: HIGH**

## Files
- `API_Security_Risk_Analysis_Report.pdf` — Full professional report (PDF)
- `API_Security_Risk_Analysis_Report.md` — Report in Markdown format

## Tools Used
- cURL — HTTP request inspection and header analysis
- Python 3 — Response parsing and data extraction
- OWASP API Security Top 10 — Risk classification framework

## Scope & Ethics
All testing was **read-only and non-exploitative**. Limited to publicly accessible demo APIs. No systems were harmed or exploited.

---
*Analyst: SecureAgent | Date: March 2026 | Internship: CyberSecurity*
