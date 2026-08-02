---
name: Connect with a trading partner on Tradeshift
description: >-
  Find a company on the Tradeshift network, send a connection request, accept an inbound one, and store your own
  vendor or customer ID against the connection.
api: openapi/tradeshift-external-api-openapi.yml
generated: '2026-08-02'
method: generated
operations:
  - get-rest-external-network-companies
  - get-rest-external-network-suggest
  - get-rest-external-network-connections
  - post-rest-external-network-connect-companyid
  - get-rest-external-network-requests
  - post-rest-external-network-requests-connectionid-accept
  - get-rest-external-network-connections-connectionid
  - put-rest-external-network-connections-connectionid-properties-key
  - post-rest-external-network-connections-connectionid-verify
---

# Connect with a trading partner on Tradeshift

Base URL: `https://api.tradeshift.com/tradeshift`. Every request carries `X-Tradeshift-TenantId`.

A connection must be **mutual and active** before two accounts can exchange documents. A connection you create for a
partner who has not yet accepted is an *external* (manual) connection — a placeholder account whose profile you may
still edit. Once they activate, it becomes a Tradeshift connection and you can no longer change their account info.

## Steps

1. **Look for the company.** `get-rest-external-network-companies` searches the network;
   `get-rest-external-network-suggest` returns suggested companies. Search by name, country or a scheme-qualified
   business identifier.

2. **Check you are not already connected.** `get-rest-external-network-connections` — filter and look for a
   connection whose `State` is `ACCEPTED`.

3. **Send the connection request.** `post-rest-external-network-connect-companyid` —
   `POST /rest/external/network/connect/{companyId}`.

4. **Handle inbound requests.** `get-rest-external-network-requests` lists requests received;
   `post-rest-external-network-requests-connectionid-accept` accepts one.
   Note that `NETWORK_REQUEST_RECEIVED` fires even when the connection already exists.

5. **Read the connection.** `get-rest-external-network-connections-connectionid` (and
   `get-rest-external-network-connections-connectionid-detail` for the fuller record) confirm the state.

6. **Store your own identifier on the connection.**
   `put-rest-external-network-connections-connectionid-properties-key` —
   `PUT /rest/external/network/connections/{connectionId}/properties/{key}`. This is the documented place for an
   integrator's internal vendor ID (buyer side) or customer ID (supplier side). It is a `PUT` on a named key, so it
   is idempotent — replay it freely.

7. **Optionally verify.** `post-rest-external-network-connections-connectionid-verify`.

## Retry and idempotency rules

- `post-rest-external-network-connect-companyid` and the accept call are POSTs and are not idempotent. Read
  `get-rest-external-network-connections` before retrying so you do not send a duplicate request.
- Property writes are `PUT` on a named key and are safe to replay.

## Errors

- `401` / `403` — the acting user lacks access, or the feature is not enabled on the account.
- `404` — the company or connection UUID is unknown to this tenant.
- `412` — no active connection exists between you and the specified company (raised when you try to act on an
  inactive relationship).

Full catalog: `errors/tradeshift-problem-types.yml`.

## Events

`NETWORK_REQUEST_RECEIVED`, `NETWORK_REQUEST_ACCEPTED`, `NETWORK_RESPONSE_RECEIVED`, `NETWORK_CONNECTION_BROKEN` and
`NETWORK_CONNECTION_DELETED` — see `asyncapi/tradeshift-webhooks.yml`.
