# Qonto (qonto)

Qonto is a European business banking / neobank platform for freelancers and SMEs, founded in Paris in 2016 and operating on an EU-passported payment institution licence. Its Business API and Onboarding API give programmatic access to business accounts, EUR transactions, SEPA and international transfers, cards, client and supplier invoices, SEPA Direct Debit, payment links, terminals, webhooks, and partner-led company onboarding, authenticated by a login+secret-key API key or OAuth 2.0.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/qonto/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/qonto/refs/heads/main/apis.yml)

## Tags

- Business Banking
- Neobank
- Fintech
- Payments
- SEPA
- Open Banking
- EUR
- Europe

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## Authentication & Base URLs

- **Production base URL:** `https://thirdparty.qonto.com/v2`
- **Sandbox base URL:** `https://thirdparty-sandbox.staging.qonto.co/v2`
- **API key:** `Authorization: {sign-in}:{secret-key}` — the organization sign-in and secret key concatenated with a colon. This resembles HTTP Basic auth but is **not** (no Base64 encoding).
- **OAuth 2.0:** authorization code flow via `POST https://thirdparty.qonto.com/oauth2/token`; access tokens valid 1 hour, refresh tokens 90 days, per-resource scopes. OAuth is the recommended method for SaaS integrations.
- **PSD2 / TPP:** regulated third parties can identify via a QSeal certificate (QSealC).
- **SCA:** Strong Customer Authentication is required for sensitive operations (e.g. transfers) via `X-Qonto-Sca-Session-Token` / `X-Qonto-MFA` headers.

## APIs

### Qonto Business API

Core Business API surface for retrieving the authenticated organization and its bank accounts, plus memberships, teams, labels, and the current subscription plan.

- **Human URL:** [https://docs.qonto.com/get-started/business-api/overview](https://docs.qonto.com/get-started/business-api/overview)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Organizations
- Accounts
- Memberships
- Teams
- Labels

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/introduction)
- [API Reference](https://docs.qonto.com/api-reference/business-api/accounts-organizations/organizations/retrieve-the-authenticated-organization-and-list-bank-accounts)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Transactions & Statements API

List and retrieve account transactions with rich filtering (status, dates, side, operation type), account statements, and cash flow category assignment.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/transactions-statements/transactions/list-transactions](https://docs.qonto.com/api-reference/business-api/transactions-statements/transactions/list-transactions)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Transactions
- Statements
- Cash Flow

#### Properties

- [API Reference](https://docs.qonto.com/api-reference/business-api/transactions-statements/transactions/list-transactions)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto SEPA Transfers API

Create single, bulk, and recurring SEPA credit transfers in EUR (standard or instant), manage SEPA beneficiaries, and run Verification of Payee (VoP) checks. Sensitive operations require Strong Customer Authentication (SCA).

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/payments-transfers/sepa-transfers/sepa-transfers/create](https://docs.qonto.com/api-reference/business-api/payments-transfers/sepa-transfers/sepa-transfers/create)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- SEPA
- Transfers
- Payments
- Beneficiaries

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/business-api/payments-transfers/sepa-transfers/introduction)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto International Transfers API

Check eligibility, list available currencies, create quotes, manage international beneficiaries, and initiate non-EUR / cross-border transfers.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/payments-transfers/international-transfers/introduction](https://docs.qonto.com/api-reference/business-api/payments-transfers/international-transfers/introduction)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- International
- FX
- Cross Border
- Beneficiaries

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/business-api/payments-transfers/international-transfers/introduction)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Internal Transfers API

Move funds between the organization's own Qonto bank accounts.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/payments-transfers/internal-transfers/create-an-internal-transfer](https://docs.qonto.com/api-reference/business-api/payments-transfers/internal-transfers/create-an-internal-transfer)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Internal Transfers
- Accounts

#### Properties

- [API Reference](https://docs.qonto.com/api-reference/business-api/payments-transfers/internal-transfers/create-an-internal-transfer)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Cards API

Issue single or bulk virtual and physical cards, set and update limits, lock/unlock, discard, report lost/stolen, manage options and restrictions, and retrieve a card iframe URL.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/cards/list-cards](https://docs.qonto.com/api-reference/business-api/cards/list-cards)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Cards
- Virtual Cards
- Physical Cards

#### Properties

- [API Reference](https://docs.qonto.com/api-reference/business-api/cards/list-cards)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Client Invoices & Quotes API

Create, finalize, send, and manage client (customer) invoices, quotes, and credit notes, including bulk import, e-invoicing dispatch, and Factur-X PDF generation. Manage clients (customers) and products.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/expense-management/client-quotes-notes/client-invoices/list-client-invoices](https://docs.qonto.com/api-reference/business-api/expense-management/client-quotes-notes/client-invoices/list-client-invoices)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Invoicing
- Accounts Receivable
- Quotes
- Credit Notes
- Factur-X

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/business-api/expense-management/client-quotes-notes/introduction-factur-x)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Supplier Invoices API

Bulk-create, list, retrieve, and mark supplier (vendor) invoices as paid or rejected, and attach supporting documents to transactions.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/expense-management/supplier-invoices/list-supplier-invoices](https://docs.qonto.com/api-reference/business-api/expense-management/supplier-invoices/list-supplier-invoices)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Invoicing
- Accounts Payable
- Attachments

#### Properties

- [API Reference](https://docs.qonto.com/api-reference/business-api/expense-management/supplier-invoices/list-supplier-invoices)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto SEPA Direct Debit API

Collect EUR payments from customers via SEPA Direct Debit - manage mandates, one-off collections, and recurring subscriptions.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/payments-transfers/sepa-direct-debit/introduction](https://docs.qonto.com/api-reference/business-api/payments-transfers/sepa-direct-debit/introduction)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- SEPA Direct Debit
- SDD
- Collections
- Mandates

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/business-api/payments-transfers/sepa-direct-debit/introduction)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Payment Links API

Connect a payment links provider and create, list, and deactivate secure customizable payment links, with available payment methods and per-link payments.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/payments-transfers/payment-links/introduction](https://docs.qonto.com/api-reference/business-api/payments-transfers/payment-links/introduction)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Payment Links
- Checkout
- Getting Paid

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/business-api/payments-transfers/payment-links/introduction)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Terminals API

Push payments from your POS system directly to physical Qonto payment terminals and retrieve terminal payment status.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/terminals/introduction](https://docs.qonto.com/api-reference/business-api/terminals/introduction)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Terminals
- In-Person Payments
- POS

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/business-api/terminals/introduction)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Webhooks API

Create, list, update, and delete webhook subscriptions to receive real-time signed HTTP callbacks for transactions, cards, invoices, SEPA Direct Debit, payment links, terminals, memberships, and consent revocations.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/webhooks/overview](https://docs.qonto.com/api-reference/business-api/webhooks/overview)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Webhooks
- Events
- Real Time

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/business-api/webhooks/overview)
- [API Reference](https://docs.qonto.com/api-reference/business-api/webhooks/supported-webhooks/v1-transactions)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Onboarding API

Partner-facing API to create and track organization registrations (including company creation flows), upload and manage KYC files, and subscribe to onboarding webhook events.

- **Human URL:** [https://docs.qonto.com/get-started/onboarding-api/overview](https://docs.qonto.com/get-started/onboarding-api/overview)
- **Base URL:** `https://thirdparty.qonto.com`

#### Tags

- Onboarding
- KYC
- Company Creation
- Partners

#### Properties

- [API Reference](https://docs.qonto.com/api-reference/onboarding-api/endpoints/registrations/create-a-registration)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Qonto Embed SDK & Hosted Pages API

Create Embed Auth Links to authenticate end customers into Qonto Hosted Pages and proxy encoded API requests dispatched by the Embed SDK for embedded banking experiences.

- **Human URL:** [https://docs.qonto.com/api-reference/business-api/endpoints/embed-auth-links/introduction](https://docs.qonto.com/api-reference/business-api/endpoints/embed-auth-links/introduction)
- **Base URL:** `https://thirdparty.qonto.com/v2`

#### Tags

- Embedded Finance
- Embed SDK
- Hosted Pages

#### Properties

- [Documentation](https://docs.qonto.com/api-reference/sdk-libraries/doc-pages/overview)
- [API Reference](https://docs.qonto.com/api-reference/business-api/endpoints/encoded-requests/introduction)
- [OpenAPI](openapi/qonto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qonto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

## Common Properties

- [GitHub Organization](https://github.com/qonto)
- [LinkedIn](https://www.linkedin.com/company/qonto)
- [Website](https://qonto.com/)
- [Documentation](https://docs.qonto.com/)
- [Plans](plans/qonto-plans-pricing.yml)
- [Rate Limits](rate-limits/qonto-rate-limits.yml)
- [Fin Ops](finops/qonto-finops.yml)

## Notes

- **Company:** French B2B fintech founded 2016, HQ Paris; 600,000+ business customers. Operates on an EU-passported payment institution licence (obtained 2018) and filed for a French banking licence in 2025.
- **Markets:** France (largest), Germany, Spain, Italy, plus Austria, Belgium, Netherlands, and Portugal (entered late 2024).
- **Acquisitions:** Penta (German business-banking competitor, 2022) and Regate (accounting / financial automation, 2024). Regate operates its own separate public API at docs.regate.io.
- **Currency:** EUR.
- **Deprecations:** the `/v1/organizations/{slug}` and `/v2/organizations/{slug}` endpoints are deprecated with sunset on 2026-11-15; migrate to `GET /v2/organization`.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
