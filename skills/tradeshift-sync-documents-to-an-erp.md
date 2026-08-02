---
name: Sync Tradeshift documents into an ERP
description: >-
  Page through received documents, pull the original UBL, and mark each one as synced with a tag and a property so
  the integration is resumable and does not double-post.
api: openapi/tradeshift-external-api-openapi.yml
generated: '2026-08-02'
method: generated
operations:
  - get-rest-external-documents
  - get-rest-external-documents-documentid
  - get-rest-external-documents-documentid-original
  - get-rest-external-documents-documentid-metadata
  - get-rest-external-documents-documentid-sendercompany
  - put-rest-external-documents-documentid-tags-tag
  - put-rest-external-documents-documentid-properties-property_key
  - get-rest-external-documents-csv
---

# Sync Tradeshift documents into an ERP

Base URL: `https://api.tradeshift.com/tradeshift`. Every request carries `X-Tradeshift-TenantId`.

## Pagination contract

`get-rest-external-documents` returns an object, not a bare array:

```json
{"itemsPerPage": 25, "itemCount": 14, "indexing": false, "numPages": 1, "pageId": 0, "Document": [ ... ]}
```

Drive the loop off `numPages` / `pageId` with `page` and `limit`. Filters combine as logical **AND** unless stated
otherwise. Useful ones: `documentType`, `state`, `processState`, `minissuedate` / `maxissuedate`,
`createdAfter` / `createdBefore`, `sentBy` / `sentTo`, `tag` / `withouttag`, `stag`. Drafts are excluded unless you
pass `stag=draft`; deleted documents need `stag=deleted`. Sortable on `DueDate`, `LastEdit`, `Number`, `Amount`,
`Date`, `Type`.

## Steps

1. **Select the unsynced backlog.** `get-rest-external-documents` with `documentType=invoice`,
   `withouttag=erp-synced` and a `createdAfter` watermark. Using `withouttag` rather than a stored cursor makes the
   job restartable after a crash.

2. **Fetch the payload.** `get-rest-external-documents-documentid` returns the document in the representation you
   ask for via `Accept` — XML UBL (default), JSON, Oasis JSON, or PDF.
   `get-rest-external-documents-documentid-original` returns the original as received, which is what you want when
   you must archive exactly what the supplier sent.
   `get-rest-external-documents-documentid-metadata` gives the metadata envelope without the body.

3. **Resolve the counterparty.** `get-rest-external-documents-documentid-sendercompany` gives the sending company so
   you can map it to your ERP vendor master (pair this with the connection property you set in the
   *Connect with a trading partner* skill).

4. **Post to the ERP**, then **mark the document**, in that order:
   - `put-rest-external-documents-documentid-properties-property_key` — store your ERP document number, e.g.
     `PUT /rest/external/documents/{documentId}/properties/erp-doc-id`.
   - `put-rest-external-documents-documentid-tags-tag` — `PUT /rest/external/documents/{documentId}/tags/erp-synced`.

   Both are `PUT` on a named key, so replaying them is a no-op. Write the property before the tag: the tag is the
   thing your query filters on, so it should be the last write.

5. **Bulk reconciliation.** `get-rest-external-documents-csv` returns a CSV extract of the document list for
   period-end reconciliation against the ERP.

## Retry and idempotency rules

- Every step in this skill is a `GET` or a `PUT` on a named key. The whole loop is safe to re-run.
- If the ERP post succeeded but the tag write failed, the next run re-selects the document. Guard against
  double-posting on the ERP side using the property you write in step 4, or check for the property before posting.

## Errors

- `404` — document not visible to this tenant, or deleted (retry with `stag=deleted` if you meant to include it).
- `406` — the `Accept` header asks for a representation this document cannot be rendered as.
- `503 ObjectNotFound` — transient, a custom document profile is being refreshed; retry.

No rate limits are published and the spec declares no `429`; still, back off on `5xx` and keep page sizes modest.

## Events

Prefer `AFTER_DOCUMENT_RECEIVE` / `DOCUMENT_SAVED` webhooks over polling where you can — see
`asyncapi/tradeshift-webhooks.yml`.
