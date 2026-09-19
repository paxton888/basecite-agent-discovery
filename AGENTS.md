# BaseCite agent discovery
BaseCite is an evidence infrastructure service for controlled document intake, verification, and AI context delivery.
## Canonical resources
- Homepage: https://basecite.com/
- Agent guide: https://basecite.com/agents.md
- Authentication guide: https://basecite.com/auth.md
- OpenAPI document: https://api.basecite.com/openapi.json
- MCP server card: https://mcp.basecite.com/.well-known/mcp/server-card.json
- MCP endpoint: https://mcp.basecite.com/mcp
## Agent rules
1. Prefer the machine-readable resources above over inferred URLs.
2. Use the public discovery tools before requesting tenant credentials.
3. Never expose, log, or invent API keys, OAuth tokens, uploaded files, or private AI context.
4. Use OAuth metadata and the published authentication guide for protected actions.
5. Treat uploaded evidence as tenant-scoped and cite the returned evidence identifiers.
## Interoperability
This repository contains public discovery metadata only. It does not contain credentials, customer data, production source code, or private configuration.
