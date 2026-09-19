---
name: basecite-evidence
version: 1.0.0
description: Use BaseCite to discover, upload, verify, process, and withdraw tenant-scoped evidence through the public API and MCP server.
---

# BaseCite evidence

Use BaseCite only for an explicitly selected organization and upload. Keep credentials server-side and never place API keys, OAuth tokens, customer documents, or derived context in prompts, logs, commits, or public artifacts.

## Public resources

- Agent guide: https://basecite.com/agents.md
- Authentication: https://basecite.com/auth.md
- OpenAPI: https://api.basecite.com/openapi.json
- MCP server card: https://mcp.basecite.com/.well-known/mcp/server-card.json
- MCP endpoint: https://mcp.basecite.com/mcp

## Required workflow

1. Authenticate with the documented OAuth flow.
2. Select the organization and use an idempotency key for upload creation.
3. Upload the original and verify the canonical status and SHA-256 completion.
4. Poll status for security scan, extraction/OCR, controlled summary, and AI context. Do not infer completion from a timer.
5. On withdrawal, remove the original and all derived context for the same upload, then verify the terminal status.

Prefer the OpenAPI contract and MCP server card over guessed endpoints. Never claim a file was uploaded, processed, or withdrawn without a server-confirmed result.
