---
name: Create a Qonto SEPA transfer
description: Look up the organization and beneficiaries, then create a EUR SEPA credit transfer safely with an idempotency key and Strong Customer Authentication.
api: openapi/qonto-openapi.yml
operations: [getOrganization, listBeneficiaries, createSepaTransfer]
---

# Create a Qonto SEPA transfer

Use this to move EUR out of a Qonto account via SEPA. This is a sensitive money-movement flow.

## Auth
- Bearer OAuth access token (recommended) or API key.
- Required OAuth scope: `payment.write` (and `organization.read` to look up accounts/beneficiaries).
- Base URL: `https://thirdparty.qonto.com`.

## Steps
1. **Resolve the debit account** — `getOrganization` (`GET /v2/organization`); pick the `debit_iban` of the funding bank account.
2. **Find the payee** — `listBeneficiaries` (`GET /v2/beneficiaries`) and select a `beneficiary_id`.
3. **Create the transfer** — `createSepaTransfer` (`POST /v2/sepa/transfers`) with body `{ debit_iban, beneficiary_id, amount, currency: EUR, reference, instant }`.
   - Send an `X-Qonto-Idempotency-Key` header (V4 UUID) so a retry never double-pays.
   - Complete Strong Customer Authentication: supply `X-Qonto-Sca-Session-Token` (and `X-Qonto-MFA` when challenged). SCA can only be skipped for trusted beneficiaries (Embed partners only).

## Rules
- Idempotency keys expire after 30 minutes; reuse the same key for the same retry.
- A `422` means validation failed (e.g. insufficient limits) — do not retry blindly; fix the request.
- Never expose the client secret; run the OAuth token exchange server-side.
- See conventions/qonto-conventions.yml and errors/qonto-problem-types.yml.
