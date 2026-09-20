---
name: basecite-evidence
version: 1.0.1
description: Use BaseCite to discover public evidence-infrastructure capabilities and, when authorized, create, track, and withdraw a tenant-scoped evidence record through its documented API and MCP server.
---

# BaseCite evidence

Use BaseCite only for an explicitly selected organization and upload. Keep credentials server-side and never place API keys, OAuth tokens, customer documents, or derived context in prompts, logs, commits, or public artifacts.

## Public resources

- Company profile: https://basecite.com/company
- Agent guide: https://basecite.com/llms.txt
- Developer API guide: https://basecite.com/docs/developers
- Authentication guide: https://basecite.com/auth.md
- OpenAPI: https://api.basecite.com/openapi.json
- MCP server card: https://mcp.basecite.com/.well-known/mcp/server-card.json
- MCP endpoint: https://mcp.basecite.com/mcp

## Required workflow

1. Confirm the organization identifier and the caller's authorization before any customer-data action.
2. Authenticate with the documented OAuth or tenant-scoped API-key flow. Use an idempotency key for an upload creation request.
3. Upload the original through the documented API, then read the canonical status and SHA-256 completion result.
4. Poll the canonical status for security scan, extraction/OCR, controlled summary, and AI context. Never infer completion from elapsed time.
5. On withdrawal, request deletion for the same organization and upload, then verify the server-confirmed terminal status and deletion receipt.

## Safety boundaries

- Public discovery tools and resources are read-only and expose no customer data.
- Raw customer files, OCR full text, bulk exports, and list-all endpoints are not public MCP outputs.
- BaseCite records customer-submitted material; it does not verify truth, authority, endorsement, company quality, rankings, or certifications.

Prefer the OpenAPI contract and MCP server card over guessed endpoints. Never claim a file was uploaded, processed, or withdrawn without a server-confirmed result.
