---
name: Create and list Qonto client invoices
description: Create a client (customer) invoice and list existing client invoices for accounts-receivable automation.
api: openapi/qonto-openapi.yml
operations: [createClientInvoice, listClientInvoices]
---

# Create and list Qonto client invoices

Use this to automate accounts receivable: raise a customer invoice and track invoices.

## Auth
- Bearer OAuth access token or API key.
- Required OAuth scopes: `client_invoice.write` to create, `client_invoices.read` to list.
- Base URL: `https://thirdparty.qonto.com`.

## Steps
1. **Create the invoice** — `createClientInvoice` (`POST /v2/client_invoices`) with the client, line items/products, and currency. Qonto can generate a Factur-X PDF and dispatch e-invoicing.
2. **List / verify** — `listClientInvoices` (`GET /v2/client_invoices`), paginating with `current_page` / `per_page`.

## Rules
- Send an `X-Qonto-Idempotency-Key` (V4 UUID) on the create call to avoid duplicate invoices.
- Read the `meta` pagination block when listing.
- See conventions/qonto-conventions.yml and errors/qonto-problem-types.yml.
