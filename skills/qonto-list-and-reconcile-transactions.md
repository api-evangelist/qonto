---
name: List and reconcile Qonto transactions
description: Retrieve the authenticated organization and its bank accounts, list transactions with filters, fetch a single transaction, and pull statements for reconciliation.
api: openapi/qonto-openapi.yml
operations: [getOrganization, listTransactions, getTransaction, listStatements]
---

# List and reconcile Qonto transactions

Use this to read an organization's banking activity for reconciliation or reporting.

## Auth
- Send `Authorization: {sign-in}:{secret-key}` (API key) or a Bearer OAuth access token.
- Required OAuth scope: `organization.read`.
- Base URL: `https://thirdparty.qonto.com`.

## Steps
1. **Get the organization and its accounts** — `getOrganization` (`GET /v2/organization`). Read `slug`/IBANs of each bank account; you need a `bank_account_id` or `iban` to filter transactions.
2. **List transactions** — `listTransactions` (`GET /v2/transactions`). Filter with `bank_account_id` or `iban`, `status[]` (`pending`, `declined`, `completed`), `updated_at_from`, `settled_at_from`. Paginate with `current_page` / `per_page` (max 100).
3. **Fetch details** — `getTransaction` (`GET /v2/transactions/{id}`) for a single transaction when you need the full object.
4. **Pull statements** — `listStatements` (`GET /v2/statements`) for periodic account statements to tie out balances.

## Rules
- Pagination: read the `meta` block; loop `current_page` until you reach the last page.
- Rate limits: 1000 req/10s and 10000 req/10min per IP; back off on `429` (see conventions/qonto-conventions.yml).
- These are read-only operations; no idempotency key needed.
