---
name: Validate a document before sending on Tradeshift
description: >-
  Run a UBL business document through Tradeshift's validation and clearance surface, manage validator groups, and
  read the account's dynamic validations before you dispatch.
api: openapi/tradeshift-external-api-openapi.yml
generated: '2026-08-02'
method: generated
operations:
  - post-rest-external-documents-validate
  - put-rest-external-document-validation-validation-validate-document
  - get-rest-external-document-validation-validation-groups
  - get-rest-external-document-validation-validation-groups-groupid
  - put-rest-external-document-validation-validation-groups-groupid
  - get-rest-external-document-validation-validation-groups-groupid-history
  - get-rest-external-account-validations
  - get-rest-external-account-validations-valuesets
  - get-rest-external-account-validations-values
---

# Validate a document before sending on Tradeshift

Base URL: `https://api.tradeshift.com/tradeshift`. Every request carries `X-Tradeshift-TenantId`.

Validating before dispatch is how you avoid a document being rejected downstream by a country e-invoicing mandate or
by the buyer's own coding rules. Two surfaces exist and they are not the same thing.

## Surfaces

- **Document validation on the document API** — `post-rest-external-documents-validate`
  (`POST /rest/external/documents/validate`). Validates a document payload you supply.
  Query flags of note: `schemaValidate`, `schemaValidateUbl`, `validateDocumentProfile`.
- **The document-validation service** — `put-rest-external-document-validation-validation-validate-document`
  (`PUT /rest/external/document-validation/validation/validate-document`). The newer validation-and-clearance
  surface, driven by validator groups.

## Steps

1. **Check what rules apply to the account.** `get-rest-external-account-validations` lists the account's dynamic
   validations. `get-rest-external-account-validations-valuesets` and
   `get-rest-external-account-validations-values` give the allowed value sets those rules check against — resolve
   these before you build the payload rather than after a rejection.

2. **List the validator groups.** `get-rest-external-document-validation-validation-groups`;
   `get-rest-external-document-validation-validation-groups-groupid` reads one.

3. **Create or update a validator group** with `put-rest-external-document-validation-validation-groups-groupid` —
   a `PUT` on a named `groupId`, so it is idempotent. `...-groupid-history` returns the change history for audit.

4. **Validate the document.** Call `put-rest-external-document-validation-validation-validate-document` (or
   `post-rest-external-documents-validate` for schema/profile checks on the document API).

5. **Only then dispatch** — see the *Send an invoice* skill.

## Retry and idempotency rules

- Validation calls are read-only in effect; retrying is safe.
- Validator-group writes are `PUT` on a named id and are safe to replay.

## Errors

- `400 BadRequest` — the payload failed schema or profile validation; the body names what.
- `404` — "If no dynamic validations are found." A 404 here is a legitimate "nothing configured", not a failure.
- `503 ObjectNotFound` — *"The error occurs due to the expired custom document profile that is used for validation.
  The system requests a new one, but it is retrieved asynchronously."* This is a temporary state; **retry the same
  request later** rather than treating it as a hard failure.

Full catalog: `errors/tradeshift-problem-types.yml`.

## Schemas

Validate locally first against the harvested Tradeshift UBL JSON Schemas in `json-schema/` (Invoice, CreditNote,
Order, OrderResponse, Quotation, RequestForQuotation, ReceiptAdvice, DespatchAdvice, ApplicationResponse). Code lists
follow ISO 4217 (currency), ISO 3166 (country), UN/ECE 5305 (tax category), UN/ECE 5153 subset (tax scheme) and
UN/ECE rec 20 (units).
