---
name: avetta-register-supplier
description: Invite and register a new supplier or contractor into Avetta on behalf of a client organization and map it to the client's ERP id.
api: avetta:avetta-connect-client-api
operations:
- register-supplier
- getExternalIds
- deleteExternalIds
generated: '2026-10-20'
method: generated
source: openapi/avetta-connect-openapi.yml
---
1. Authenticate via `POST /auth/v1/token`.
2. Submit `register-supplier` with the required fields, including `requestedBySiteIds`; 200 means the registration was submitted, 400/500 means check the data. Duplicate registrations are rejected, and there is no idempotency key, so do not blindly retry.
3. Confirm ERP mappings with `getExternalIds`; remove a wrong mapping with `deleteExternalIds` (no reversal window is documented).
