---
name: Send an invoice on Tradeshift
description: >-
  Create a UBL invoice with a client-assigned UUID, dispatch it to a connected trading partner, and confirm delivery
  by reading the latest dispatch.
api: openapi/tradeshift-external-api-openapi.yml
generated: '2026-08-02'
method: generated
operations:
  - get-rest-external-account-info
  - get-rest-external-network-connections
  - put-rest-external-documents-documentid
  - post-rest-external-documents-dispatcher
  - get-rest-external-documents-documentid-dispatches-latest
  - get-rest-external-documents-documentid
---

# Send an invoice on Tradeshift

Base URL: `https://api.tradeshift.com/tradeshift` (sandbox: `https://api-sandbox.tradeshift.com/tradeshift`).

## Before you start

- Authenticate with OAuth 2.0 (three-legged, for apps acting for a user) or OAuth 1.0a two-legged. See
  `authentication/tradeshift-authentication.yml`.
- **Every request must carry `X-Tradeshift-TenantId`** with the UUID of the company account you are acting as.
- Set `Accept: application/json` if you want JSON; the default document representation is XML (UBL/TSUBL).
- Confirm the credentials work: `get-rest-external-account-info` returns your own company.

## Steps

1. **Verify the recipient is connected.** Call `get-rest-external-network-connections` and find a connection whose
   `State` is `ACCEPTED` and whose `ConnectionType` is `TradeshiftConnection`. A document sent over a connection that
   is not yet mutual will be queued, not delivered (see the `DOCUMENT_VALIDATING` webhook event). If there is no
   connection, run the *Connect with a trading partner* skill first.

2. **Generate the document UUID yourself.** Tradeshift lets the client choose the document id, and that is what makes
   the write idempotent: *"The client can decide on the UUID for the new element defined by the `documentId`
   parameter."* Generate one RFC 4122 UUID per invoice and store it before the first attempt.

3. **Store the invoice.** `put-rest-external-documents-documentid` —
   `PUT /rest/external/documents/{documentId}` with the UBL invoice as the request body.
   - `Content-Type: application/xml` for UBL/TSUBL, or JSON if you are posting the JSON representation.
   - Saving as a draft lets Tradeshift re-derive TSUBL content and run extra connection checks; saving as non-draft
     keeps your UBL exactly as supplied and makes it the primary source.
   - Validate against the JSON Schema in `json-schema/tradeshift-ubl-invoice-2.1.json` before sending if you build
     the payload yourself.

4. **Dispatch it.** `post-rest-external-documents-dispatcher` — `POST /rest/external/documents/dispatcher`.

5. **Confirm delivery.** `get-rest-external-documents-documentid-dispatches-latest` returns the latest dispatch for
   the document. `get-rest-external-documents-documentid` returns the document with its current `State`.

## Retry and idempotency rules

- On a network error or timeout, **replay the same `PUT` with the same `documentId`**. Do not mint a new UUID — that
  creates a second invoice.
- `post-rest-external-documents-dispatcher` is a POST and is **not** idempotent. Before retrying a dispatch, read
  `get-rest-external-documents-documentid-dispatches-latest` to check whether the first attempt landed.
- A `409` on a create means the document already exists — treat it as the successful outcome of a replay.

## Errors

Tradeshift does not use RFC 9457. The envelope is `{"ErrorCode": ..., "Message": ..., "ErrorDetail": [{"Key",
"Value"}]}`. Full catalog in `errors/tradeshift-problem-types.yml`.

- `400 BadRequest` — the body names the invalid or blank parameters.
- `401 Unauthorized` — credentials or `X-Tradeshift-TenantId` do not grant access to the object.
- `406` — the `Accept` header asks for a representation Tradeshift cannot produce.
- `412` — no active connection exists between you and the specified company.
- `503 ObjectNotFound` — a custom document profile is being refreshed asynchronously; retry the same request shortly.

## Events

Subscribe your app to `DOCUMENT_SENDING`, `DOCUMENT_SENT` and `DOCUMENT_VALIDATING` rather than polling. See
`asyncapi/tradeshift-webhooks.yml`.
