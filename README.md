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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Tradeshift is a cloud-based business commerce network for accounts payable automation, e-invoicing compliance,
procure-to-pay, supplier management, and B2B marketplace commerce, connecting buyers and sellers across more than
190 countries.

- Website — https://tradeshift.com/
- Developer Center — https://developers.tradeshift.com/
- API reference — https://developers.tradeshift.com/docs/api
- Status — https://status.tradeshift.com/
- GitHub — https://github.com/Tradeshift

## APIs

| API | Base URL | Contract |
|---|---|---|
| Tradeshift External API | `https://api.tradeshift.com/tradeshift` | OpenAPI 3.0.0, 137 paths / 172 operations |
| Tradeshift MCP Server | `https://mcp.tradeshift.com/mcp` | MCP (auth-gated) + OpenAPI 3.1.0 HTTP bridge |

## Artifacts

- `openapi/` — the harvested Tradeshift External API spec and the MCP HTTP bridge spec (originals in `_original/`)
- `json-schema/` — Tradeshift's published OASIS UBL JSON Schemas for the document types the API exchanges
- `mcp/` — MCP server manifest and the domain-level tool crosswalk
- `scopes/`, `authentication/`, `well-known/` — the OAuth surface, including the RFC 8414 / RFC 9728 metadata
- `conventions/`, `errors/`, `data-model/`, `lifecycle/`, `conformance/` — derived runtime semantics
- `asyncapi/tradeshift-webhooks.yml` — the 12-event platform webhook catalog
- `skills/` — packaged agent operating instructions grounded in verified operationIds
- `packages/`, `components/`, `sandbox/`, `changelog/`, `security/`, `overlays/`, `llms/`

Everything here was searched, probed or derived from Tradeshift's own public surface. Provenance is recorded in each
artifact's frontmatter (`method`, `source`, `x-evidence`).
