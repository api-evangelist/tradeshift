# Tradeshift

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
