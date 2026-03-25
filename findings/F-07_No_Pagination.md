# F-07 — Bulk Data Retrieval — No Pagination Enforcement

| Field | Details |
|-------|---------|
| **Risk Level** | 🟡 LOW |
| **CVSS Score** | 3.5 |
| **OWASP** | API4:2023 – Unrestricted Resource Consumption |
| **Priority** | Week 3 |

## Description
Collection endpoints return all records in a single response with no default pagination. GET /posts returns 100 records, /comments returns 500, /photos returns 5,000 in one call.

## Evidence
```
curl -s https://jsonplaceholder.typicode.com/posts    → 100 records
curl -s https://jsonplaceholder.typicode.com/comments → 500 records
curl -s https://jsonplaceholder.typicode.com/photos   → 5,000 records
All returned in a single API call with no limit enforced.
```

## Business Impact
Enables resource exhaustion via large dataset requests, increased server load, and complete dataset extraction in a single request.

## Fix
Enforce server-side pagination with a maximum page size (20-50 records). Require ?_page and ?_limit parameters. Return pagination metadata in all collection responses.
