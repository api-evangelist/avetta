---
name: avetta-supplier-compliance-review
description: Review a connected supplier's compliance posture in Avetta One - profile, flags, scorecards, ESG metrics and forms - through the Avetta Connect Client API.
api: avetta:avetta-connect-client-api
operations:
- getConnectedSupplierProfile
- getSupplierProfile
- getSupplierFlags
- getSupplierScorecards
- getEsgScores
- getSupplierFormsAndAnswers
generated: '2026-10-20'
method: generated
source: openapi/avetta-connect-openapi.yml
---
1. Obtain a token from `POST /auth/v1/token` on https://api.avetta.com (see authentication/avetta-authentication.yml).
2. List connected suppliers with `getConnectedSupplierProfile`, paging with `start`/`limit` (500 records per call by default).
3. For a supplier, read `getSupplierProfile`, then its compliance flags with `getSupplierFlags` and overall scores with `getSupplierScorecards`.
4. Read ESG subcategory scores with `getEsgScores` and questionnaire answers with `getSupplierFormsAndAnswers` (Forms V2; pass multiple `questionIds`).
5. Respect the rate limit: 60 calls per minute per IP (20 for unfiltered supplier/insurance/forms/audits listing); a 1015 status means wait one hour. No idempotency key exists.
