# BaseCite ChatGPT plugin submission record

This repository contains the public source and review materials for the BaseCite remote MCP plugin. The plugin is not represented as publicly listed until OpenAI approves the submission.

## Submission identity

- Display name: BaseCite
- Short description: Controlled evidence context
- Category: Business / Developer tools
- MCP endpoint: `https://mcp.basecite.com/mcp`
- MCP URL type: Universal
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

## Tool inventory and annotation justifications

| Tool | Authentication | Data returned | Annotation justification |
| --- | --- | --- | --- |
| `basecite_get_public_discovery` | none | Public links and explicit service boundaries | `readOnlyHint=true` because it only returns static public metadata; `openWorldHint=false` because it reads no arbitrary external URL and is bounded to BaseCite-owned metadata; `destructiveHint=false` because it changes no state. |
| `basecite_get_capabilities` | none | Public capability and access-boundary metadata | `readOnlyHint=true` because it only retrieves declared capabilities; `openWorldHint=false` because the result is bounded to BaseCite's own service metadata; `destructiveHint=false` because it changes no state. |
| `basecite_get_ai_context` | tenant-scoped `x-api-key` | One authorized, bounded context record for exact `org_id` and `upload_id` | `readOnlyHint=true` because it reads one existing record; `openWorldHint=false` because access is limited to a private tenant-scoped record; `destructiveHint=false` because it cannot upload, update, withdraw, delete, or trigger processing. |

The plugin never provides raw customer files, full OCR text, bulk exports, customer lists, list-all endpoints, truth verification, authority verification, company verification, rankings, or certifications.

## Starter prompts

- Show me BaseCite's public developer resources and integration boundaries.
- Explain what BaseCite exposes to AI clients and what it keeps private.
- Retrieve the authorized BaseCite context for my exact organization and upload identifiers.

## Positive review cases

1. Call `basecite_get_public_discovery` with an empty object; expect BaseCite-owned public developer, OpenAPI, MCP, registry, and SDK links only.
2. Call `basecite_get_public_discovery` with `include_registry=false`; expect registry links to be omitted while other public links remain.
3. Call `basecite_get_capabilities` with `include_boundaries=true`; expect bounded capability and non-claim metadata with no customer data.
4. Initialize the MCP session and list tools; expect exactly the three documented tools with complete input/output schemas and annotation values.
5. With the separately provisioned review tenant credential, call `basecite_get_ai_context` for the supplied exact `org_id` and `upload_id`; expect one bounded record with provenance and `not_evaluated`, without raw file or full OCR text.

## Negative review cases

1. Call `basecite_get_ai_context` without a credential; expect an authorization rejection and no record data.
2. Call `basecite_get_ai_context` with invalid or cross-tenant identifiers; expect validation/authorization rejection and no enumeration signal.
3. Add list, cursor, wildcard, raw, export, URL, or path-style parameters to `basecite_get_ai_context`; expect `enumeration_or_export_parameters_rejected` and no customer data.

## Domain-verification procedure

OpenAI's plugin submission portal supplies a unique verification token. Set that exact token as the Cloudflare Worker secret `OPENAI_APPS_CHALLENGE_TOKEN` for the production MCP worker. The server then returns only that token at:

`https://mcp.basecite.com/.well-known/openai-apps-challenge`

The token is not committed to this repository, logged, reused, or served from any other path. Remove or rotate the secret after OpenAI completes verification.

## Submission checklist

- [x] Stable public HTTPS MCP endpoint
- [x] Universal production MCP URL
- [x] Public tool descriptions, input/output schemas, annotations, and annotation justifications
- [x] Five positive and three negative review cases
- [x] Privacy, terms, support, company-profile, and developer-documentation links
- [x] Domain challenge endpoint implemented; token is supplied only by the OpenAI portal at submission time
- [ ] OpenAI Platform organization role with `api.apps.write`
- [ ] Verified individual or business developer identity
- [ ] Portal-issued challenge token installed and verified
- [ ] OpenAI review approval and public publication