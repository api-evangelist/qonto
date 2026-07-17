---
name: Issue a Qonto card
description: List existing cards and issue a new virtual or physical card idempotently.
api: openapi/qonto-openapi.yml
operations: [getOrganization, listCards, createCard]
---

# Issue a Qonto card

Use this to provision a virtual or physical card for a member.

## Auth
- Bearer OAuth access token or API key.
- Required OAuth scope: `card.write` (and `card.read` / `organization.read` to inspect state).
- Base URL: `https://thirdparty.qonto.com`.

## Steps
1. **Check context** — `getOrganization` (`GET /v2/organization`) for the account and `listCards` (`GET /v2/cards`) to see existing cards.
2. **Create the card** — `createCard` (`POST /v2/cards`) specifying the card type (virtual or physical), holder membership, and limits.
   - Send an `X-Qonto-Idempotency-Key` header (V4 UUID) so a retry does not issue a duplicate card.

## Rules
- Idempotency keys expire after 30 minutes.
- Handle `429` with backoff; handle `422` by correcting the request.
- See conventions/qonto-conventions.yml.
