# BaseCite ChatGPT plugin submission record

This repository contains the public source and review materials for the BaseCite remote MCP plugin. The plugin is not represented as publicly listed until OpenAI approves the submission.

## Submission identity

- Display name: BaseCite
- Category: Business / Developer tools
- MCP endpoint: `https://mcp.basecite.com/mcp`
- Transport: Streamable HTTP
- Company profile: https://basecite.com/company
- Developer guide: https://basecite.com/docs/developers
- Privacy policy: https://basecite.com/privacy
- Terms: https://basecite.com/terms
- Support: support@basecite.com

## Supported user outcomes

1. Discover BaseCite's public developer, API, MCP, SDK, registry, and safety-boundary information.
2. Read its machine-readable capabilities and data-access limits.
3. Retrieve one bounded AI-context record only when the caller presents a tenant-scoped credential and exact organization and upload identifiers.

## Tool inventory and data handling

| Tool | Authentication | Data returned |
| --- | --- | --- |
| `basecite_get_public_discovery` | none | Public links and explicit service boundaries |
| `basecite_get_capabilities` | none | Public capability and access-boundary metadata |
| `basecite_get_ai_context` | tenant-scoped `x-api-key` | One authorized, bounded context record for exact `org_id` and `upload_id` |

The plugin never provides raw customer files, full OCR text, bulk exports, customer lists, list-all endpoints, truth verification, authority verification, company verification, rankings, or certifications.

## Domain-verification procedure

OpenAI's plugin submission portal supplies a unique verification token. Set that exact token as the Cloudflare Worker secret `OPENAI_APPS_CHALLENGE_TOKEN` for the production MCP worker. The server then returns only that token at:

`https://mcp.basecite.com/.well-known/openai-apps-challenge`

The token is not committed to this repository, logged, reused, or served from any other path. Remove or rotate the secret after OpenAI completes verification.

## Review test cases

1. `GET https://mcp.basecite.com/mcp` returns public server metadata over HTTPS.
2. Send JSON-RPC `initialize`; verify the server declares `basecite-mcp` and public resources/tools.
3. Send JSON-RPC `tools/call` for `basecite_get_public_discovery`; verify it succeeds without credentials and returns only public links.
4. Send JSON-RPC `tools/call` for `basecite_get_ai_context` without a credential; verify the request is rejected.
5. Send malformed or enumeration-style `basecite_get_ai_context` input; verify it is rejected and does not enumerate any tenant data.
6. With a separately provisioned test tenant credential, request one exact authorized record and verify no raw file, bulk export, or list-all data is returned.

## Submission checklist

- [x] Stable public HTTPS MCP endpoint
- [x] Public tool descriptions, schemas, annotations, and safety boundaries
- [x] Privacy, terms, support, company-profile, and developer-documentation links
- [x] Public review test cases
- [x] Domain challenge endpoint implemented, token supplied only by the OpenAI portal at submission time
- [ ] OpenAI platform organization role with plugin submission write access
- [ ] Portal-issued challenge token installed and verified
- [ ] OpenAI review and public listing approval
