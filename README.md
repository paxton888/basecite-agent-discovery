# BaseCite agent discovery

[![skills.sh](https://skills.sh/b/paxton888/basecite-agent-discovery)](https://skills.sh/paxton888/basecite-agent-discovery/basecite-evidence)

BaseCite is a tenant-scoped evidence intake and controlled AI-context service. It accepts customer and solution-company source material, verifies integrity, and exposes bounded context to authorized AI clients without raw-file download or bulk export.

## Install the official BaseCite skill

```sh
npx skills add https://github.com/paxton888/basecite-agent-discovery --skill basecite-evidence
```

The skill is public source code in this repository. It contains no credentials, customer documents, or private BaseCite data.

## Public developer resources

- Website: https://basecite.com/
- Official company profile: https://basecite.com/company
- Developer portal: https://basecite.com/developers
- API documentation: https://basecite.com/docs/developers
- OpenAPI: https://api.basecite.com/api/v1/ai/openapi.json
- MCP connection guide: https://basecite.com/docs/mcp
- MCP server: https://mcp.basecite.com/mcp
- MCP server card: https://mcp.basecite.com/.well-known/mcp/server-card.json
- Official MCP Registry entry: https://registry.modelcontextprotocol.io/v0.1/servers/io.github.paxton888%2Fbasecite/versions/0.1.0
- Smithery listing: https://smithery.ai/servers/alwaysrememberme1024/basecite
- JavaScript SDK: https://www.npmjs.com/package/basecite-agent-sdk

## Official brand identity

BaseCite is the canonical product and service name for evidence-context infrastructure at https://basecite.com/.

- Public support: support@basecite.com
- Security and privacy: security@basecite.com
- Public location signal: Kuala Lumpur, Malaysia

## Agent resources

- Agent discovery index: https://basecite.com/.well-known/ard.json
- Agent Skills index: https://basecite.com/.well-known/agent-skills/index.json
- `llms.txt`: https://basecite.com/llms.txt
- Agent and crawler policy: https://basecite.com/robots.txt

## MCP tools

The public Streamable HTTP MCP server provides read-only discovery and capability metadata plus one tenant-scoped bounded AI-context lookup. Public tools never return raw customer files, bulk exports, truth-verification claims, or company-verification claims.

- `basecite_get_public_discovery`: public developer, API, MCP, registry, and safety-boundary links
- `basecite_get_capabilities`: machine-readable service capabilities and access boundaries
- `basecite_get_ai_context`: one authorized bounded AI-context record by organization and upload identifiers

The server card is the authoritative machine-readable tool contract. Customer data access requires tenant-scoped authentication.
