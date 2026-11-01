# Tradeshift

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Tradeshift is a cloud-based business commerce network for accounts payable automation, e-invoicing compliance, procure-to-pay, supplier management, and B2B marketplace commerce, connecting buyers and sellers across more than 190 countries. The Tradeshift External API is a REST/JSON+XML interface over the same platform its own apps use, covering company accounts and branches, legal entities and tax identifiers, network connections and connection properties, business documents (invoices, orders, credit notes, quotes, requisitions, receipt advices) in the OASIS UBL / TSUBL format, document files and attachments, users and memberships, assignments and workflow, and document validation and clearance for country e-invoicing mandates. Authentication is OAuth (OAuth 1.0a two-legged for account-scoped integrations, OAuth 2.0 three-legged for apps acting on behalf of users), every call carries an X-Tradeshift-TenantId header, and apps can subscribe to platform webhooks for document, network, and user events. Tradeshift also runs a production MCP server exposing platform capability to AI agents under the same authentication, RBAC, and audit model as human sessions.

**Areas:** E-Invoicing · Accounts Payable · AP Automation · Procure-to-Pay · Supply Chain · B2B Commerce · Invoicing · UBL · PEPPOL · e-invoicing-compliance · Supplier Network · business-documents

## Tradeshift on APIs.io

Everything profiled for Tradeshift is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/tradeshift/](https://apis.io/providers/tradeshift/)** — or go straight to one of the APIs or properties below.

### APIs (38)

- [Tradeshift Admin API](https://apis.io/apis/tradeshift/tradeshift-admin-api/) — The Admin API from Tradeshift — 11 operation(s) for admin.
- [Tradeshift Document Validation API](https://apis.io/apis/tradeshift/tradeshift-document-validation-api/) — Manages document validators
- [Tradeshift Dx Category Accounts Branches API](https://apis.io/apis/tradeshift/tradeshift-dx-category-accounts-branches-api/) — The dx-category--accounts-branches API from Tradeshift — 4 operation(s) for dx-category--accounts-branches.
- [Tradeshift Dx Category Accounts Company API](https://apis.io/apis/tradeshift/tradeshift-dx-category-accounts-company-api/) — The dx-category--accounts-company API from Tradeshift — 5 operation(s) for dx-category--accounts-company.
- [Tradeshift Dx Category Accounts Gli Prefixes API](https://apis.io/apis/tradeshift/tradeshift-dx-category-accounts-gli-prefixes-api/) — The dx-category--accounts-gli_prefixes API from Tradeshift — 2 operation(s) for dx-category--accounts-gli_prefixes.
- [Tradeshift Dx Category Accounts Legal Entities API](https://apis.io/apis/tradeshift/tradeshift-dx-category-accounts-legal-entities-api/) — The dx-category--accounts-legal_entities API from Tradeshift — 4 operation(s) for dx-category--accounts-legal_entities.
- [Tradeshift Dx Category Accounts Taxes API](https://apis.io/apis/tradeshift/tradeshift-dx-category-accounts-taxes-api/) — The dx-category--accounts-taxes API from Tradeshift — 1 operation(s) for dx-category--accounts-taxes.
- [Tradeshift Dx Category Accounts Validations API](https://apis.io/apis/tradeshift/tradeshift-dx-category-accounts-validations-api/) — The dx-category--accounts-validations API from Tradeshift — 8 operation(s) for dx-category--accounts-validations.
- [Tradeshift Dx Category Assignments Create API](https://apis.io/apis/tradeshift/tradeshift-dx-category-assignments-create-api/) — The dx-category--assignments-create API from Tradeshift — 1 operation(s) for dx-category--assignments-create.
- [Tradeshift Dx Category Assignments Find API](https://apis.io/apis/tradeshift/tradeshift-dx-category-assignments-find-api/) — The dx-category--assignments-find API from Tradeshift — 2 operation(s) for dx-category--assignments-find.
- [Tradeshift Dx Category Assignments Logs API](https://apis.io/apis/tradeshift/tradeshift-dx-category-assignments-logs-api/) — The dx-category--assignments-logs API from Tradeshift — 2 operation(s) for dx-category--assignments-logs.
- [Tradeshift Dx Category Assignments Reassign API](https://apis.io/apis/tradeshift/tradeshift-dx-category-assignments-reassign-api/) — The dx-category--assignments-reassign API from Tradeshift — 2 operation(s) for dx-category--assignments-reassign.
- [Tradeshift Dx Category Assignments Update API](https://apis.io/apis/tradeshift/tradeshift-dx-category-assignments-update-api/) — The dx-category--assignments-update API from Tradeshift — 3 operation(s) for dx-category--assignments-update.
- [Tradeshift Dx Category Bsd Documents API](https://apis.io/apis/tradeshift/tradeshift-dx-category-bsd-documents-api/) — The dx-category--bsd-documents API from Tradeshift — 6 operation(s) for dx-category--bsd-documents.
- [Tradeshift Dx Category Document Validation Validate Document API](https://apis.io/apis/tradeshift/tradeshift-dx-category-document-validation-validate-document-api/) — The dx-category--document-validation-validate_document API from Tradeshift — 1 operation(s) for dx-category--document-validation-validate_document.
- [Tradeshift Dx Category Document Validation Validators Delete API](https://apis.io/apis/tradeshift/tradeshift-dx-category-document-validation-validators-delete-api/) — The dx-category--document-validation-validators_delete API from Tradeshift — 1 operation(s) for dx-category--document-validation-validators_delete.
- [Tradeshift Dx Category Document Validation Validators Find All API](https://apis.io/apis/tradeshift/tradeshift-dx-category-document-validation-validators-find-all-api/) — The dx-category--document-validation-validators_find_all API from Tradeshift — 1 operation(s) for dx-category--document-validation-validators_find_all.
- [Tradeshift Dx Category Document Validation Validators Find API](https://apis.io/apis/tradeshift/tradeshift-dx-category-document-validation-validators-find-api/) — The dx-category--document-validation-validators_find API from Tradeshift — 1 operation(s) for dx-category--document-validation-validators_find.
- [Tradeshift Dx Category Document Validation Validators History API](https://apis.io/apis/tradeshift/tradeshift-dx-category-document-validation-validators-history-api/) — The dx-category--document-validation-validators_history API from Tradeshift — 1 operation(s) for dx-category--document-validation-validators_history.
- [Tradeshift Dx Category Document Validation Validators Save API](https://apis.io/apis/tradeshift/tradeshift-dx-category-document-validation-validators-save-api/) — The dx-category--document-validation-validators_save API from Tradeshift — 1 operation(s) for dx-category--document-validation-validators_save.
- [Tradeshift Dx Category Documents Assignments API](https://apis.io/apis/tradeshift/tradeshift-dx-category-documents-assignments-api/) — The dx-category--documents-assignments API from Tradeshift — 9 operation(s) for dx-category--documents-assignments.
- [Tradeshift Dx Category Documents Attachments API](https://apis.io/apis/tradeshift/tradeshift-dx-category-documents-attachments-api/) — The dx-category--documents-attachments API from Tradeshift — 2 operation(s) for dx-category--documents-attachments.
- [Tradeshift Dx Category Documents Document API](https://apis.io/apis/tradeshift/tradeshift-dx-category-documents-document-api/) — The dx-category--documents-document API from Tradeshift — 28 operation(s) for dx-category--documents-document.
- [Tradeshift Dx Category Documents Document Files API](https://apis.io/apis/tradeshift/tradeshift-dx-category-documents-document-files-api/) — The dx-category--documents-document_files API from Tradeshift — 8 operation(s) for dx-category--documents-document_files.
- [Tradeshift Dx Category Documents Quotes API](https://apis.io/apis/tradeshift/tradeshift-dx-category-documents-quotes-api/) — The dx-category--documents-quotes API from Tradeshift — 1 operation(s) for dx-category--documents-quotes.
- [Tradeshift Dx Category Documents Receipt Advices API](https://apis.io/apis/tradeshift/tradeshift-dx-category-documents-receipt-advices-api/) — The dx-category--documents-receipt_advices API from Tradeshift — 2 operation(s) for dx-category--documents-receipt_advices.
- [Tradeshift Dx Category Documents Requisitions API](https://apis.io/apis/tradeshift/tradeshift-dx-category-documents-requisitions-api/) — The dx-category--documents-requisitions API from Tradeshift — 9 operation(s) for dx-category--documents-requisitions.
- [Tradeshift Dx Category Network Connection Properties API](https://apis.io/apis/tradeshift/tradeshift-dx-category-network-connection-properties-api/) — The dx-category--network-connection_properties API from Tradeshift — 3 operation(s) for dx-category--network-connection_properties.
- [Tradeshift Dx Category Network Connections API](https://apis.io/apis/tradeshift/tradeshift-dx-category-network-connections-api/) — The dx-category--network-connections API from Tradeshift — 4 operation(s) for dx-category--network-connections.
- [Tradeshift Dx Category Network Document Profiles API](https://apis.io/apis/tradeshift/tradeshift-dx-category-network-document-profiles-api/) — The dx-category--network-document_profiles API from Tradeshift — 2 operation(s) for dx-category--network-document_profiles.
- [Tradeshift Dx Category Network Requests API](https://apis.io/apis/tradeshift/tradeshift-dx-category-network-requests-api/) — The dx-category--network-requests API from Tradeshift — 4 operation(s) for dx-category--network-requests.
- [Tradeshift Dx Category Network Search API](https://apis.io/apis/tradeshift/tradeshift-dx-category-network-search-api/) — The dx-category--network-search API from Tradeshift — 7 operation(s) for dx-category--network-search.
- [Tradeshift Dx Category Users Accounts API](https://apis.io/apis/tradeshift/tradeshift-dx-category-users-accounts-api/) — The dx-category--users-accounts API from Tradeshift — 6 operation(s) for dx-category--users-accounts.
- [Tradeshift Dx Category Users Memberships API](https://apis.io/apis/tradeshift/tradeshift-dx-category-users-memberships-api/) — The dx-category--users-memberships API from Tradeshift — 9 operation(s) for dx-category--users-memberships.
- [Tradeshift Dx Category Users Profile Images API](https://apis.io/apis/tradeshift/tradeshift-dx-category-users-profile-images-api/) — The dx-category--users-profile_images API from Tradeshift — 1 operation(s) for dx-category--users-profile_images.
- [Tradeshift Health API](https://apis.io/apis/tradeshift/tradeshift-health-api/) — The Health API from Tradeshift — 2 operation(s) for health.
- [Tradeshift MCP HTTP Bridge & Management API](https://apis.io/apis/tradeshift/tradeshift-mcp-http-bridge-management-api/) — The MCP HTTP Bridge & Management API from Tradeshift — 1 operation(s) for mcp http bridge & management.
- [Tradeshift Tools API](https://apis.io/apis/tradeshift/tradeshift-tools-api/) — The Tools API from Tradeshift — 3 operation(s) for tools.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Tradeshift Webhooks](https://apis.io/asyncapis/tradeshift/tradeshift-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [tradeshift](https://apis.io/servers/tradeshift/tradeshift/)

#### JSON Schema (9)

The data models the API reads and writes.

- [json-schema/maindoc/UBL-ApplicationResponse-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-applicationresponse-2.1/)
- [json-schema/maindoc/UBL-CreditNote-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-creditnote-2.1/)
- [json-schema/maindoc/UBL-DespatchAdvice-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-despatchadvice-2.1/)
- [json-schema/maindoc/UBL-Invoice-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-invoice-2.1/)
- [json-schema/maindoc/UBL-Order-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-order-2.1/)
- [json-schema/maindoc/UBL-OrderResponse-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-orderresponse-2.1/)
- [json-schema/maindoc/UBL-Quotation-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-quotation-2.1/)
- [json-schema/maindoc/UBL-ReceiptAdvice-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-receiptadvice-2.1/)
- [json-schema/maindoc/UBL-RequestForQuotation-2.1.json](https://apis.io/schemas/tradeshift/tradeshift-ubl-requestforquotation-2.1/)

#### Collections (40)

Postman and Open Collection request collections.

- [MCP HTTP Bridge & Management Admin API](https://apis.io/collections/tradeshift/open-tradeshift-admin-api/)
- [Tradeshift External Document Validation API](https://apis.io/collections/tradeshift/open-tradeshift-document-validation-api/)
- [Tradeshift External Dx Category Accounts Branches API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-accounts-branches-api/)
- [Tradeshift External Dx Category Accounts Company API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-accounts-company-api/)
- [Tradeshift External Dx Category Accounts Gli Prefixes API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-accounts-gli-prefixes-api/)
- [Tradeshift External Dx Category Accounts Legal Entities API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-accounts-legal-entities-api/)
- [Tradeshift External Dx Category Accounts Taxes API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-accounts-taxes-api/)
- [Tradeshift External Dx Category Accounts Validations API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-accounts-validations-api/)
- [Tradeshift External Dx Category Assignments Create API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-assignments-create-api/)
- [Tradeshift External Dx Category Assignments Find API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-assignments-find-api/)
- [Tradeshift External Dx Category Assignments Logs API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-assignments-logs-api/)
- [Tradeshift External Dx Category Assignments Reassign API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-assignments-reassign-api/)
- [Tradeshift External Dx Category Assignments Update API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-assignments-update-api/)
- [Tradeshift External Dx Category Bsd Documents API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-bsd-documents-api/)
- [Tradeshift External Dx Category Document Validation Validate Document API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-document-validation-validate-document-api/)
- [Tradeshift External Dx Category Document Validation Validators Delete API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-document-validation-validators-delete-api/)
- [Tradeshift External Dx Category Document Validation Validators Find All API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-document-validation-validators-find-all-api/)
- [Tradeshift External Dx Category Document Validation Validators Find API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-document-validation-validators-find-api/)
- [Tradeshift External Dx Category Document Validation Validators History API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-document-validation-validators-history-api/)
- [Tradeshift External Dx Category Document Validation Validators Save API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-document-validation-validators-save-api/)
- [Tradeshift External Dx Category Documents Assignments API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-documents-assignments-api/)
- [Tradeshift External Dx Category Documents Attachments API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-documents-attachments-api/)
- [Tradeshift External Dx Category Documents Document API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-documents-document-api/)
- [Tradeshift External Dx Category Documents Document Files API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-documents-document-files-api/)
- [Tradeshift External Dx Category Documents Quotes API](https://apis.io/collections/tradeshift/open-tradeshift-dx-category-documents-quotes-api/)
- …and 15 more published on APIs.io

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Tradeshift External Api Overlay](https://apis.io/overlays/tradeshift/tradeshift-external-api-overlay/)
- [Tradeshift Mcp Bridge Overlay](https://apis.io/overlays/tradeshift/tradeshift-mcp-bridge-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Tradeshift Authentication](https://apis.io/security/tradeshift/tradeshift-authentication/)
- [Tradeshift Domain Security](https://apis.io/security/tradeshift/tradeshift-domain-security/)
- [Tradeshift Trust Center](https://apis.io/security/tradeshift/tradeshift-trust-center/)
- [Tradeshift Vulnerability Disclosure](https://apis.io/security/tradeshift/tradeshift-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Tradeshift Scopes](https://apis.io/scopes/tradeshift/tradeshift-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Tradeshift Plans Pricing](https://apis.io/plans/tradeshift/tradeshift-plans-pricing/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://tradeshift.com/)
- [Documentation](https://developers.tradeshift.com/docs/api)
- [Getting started](https://developers.tradeshift.com/docs/guides/get-started)
- [API reference](https://developers.tradeshift.com/docs/api)
- [Pricing](https://tradeshift.com/seller-pricing/)
- [Sign up](https://go.tradeshift.com/register)
- [Support](https://support.tradeshift.com/)
- [Changelog](https://developers.tradeshift.com/announcements/)
- [Blog](https://tradeshift.com/resources/)
- [Security](https://tradeshift.com/security/)
- [Compliance](https://tradeshift.com/security/)
- [Terms of service](https://tradeshift.com/terms-of-service/)
- [Privacy policy](https://tradeshift.com/privacy-policy/)
- [GitHub](https://github.com/Tradeshift)
- [Status](https://status.tradeshift.com/)

## API Evangelist rating

**Kin Score 64.8** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 60.5 |
| Contract governance | 18.2 |
| Operational transparency | 52.6 |
| Developer ergonomics | 35.1 |
| Access clarity | 92.1 |

**Agent readiness 49.1** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | mostly (partial credit) |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/tradeshift/](https://apis.io/providers/tradeshift/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Tradeshift: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/tradeshift/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
