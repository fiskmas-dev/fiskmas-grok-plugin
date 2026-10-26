# Install Fiskmås MCP

Fiskmås is a **remote** Streamable HTTP MCP server. Do not clone and run a local process.

## Connect

1. Get a free API token at https://fiskmas.dev (or call MCP tool `create_account` once connected without auth for onboarding tools).
2. Set env `FISKMAS_TOKEN` to that token.
3. Add this MCP server to the client:

```json
{
  "mcpServers": {
    "fiskmas": {
      "type": "http",
      "url": "https://mcp.fiskmas.dev/mcp",
      "headers": {
        "Authorization": "Bearer ${FISKMAS_TOKEN}"
      }
    }
  }
}
```

- Claude Code: project `.mcp.json` (this repo already has it) or `claude mcp add --transport http fiskmas https://mcp.fiskmas.dev/mcp`
- Cursor: `.cursor/mcp.json`
- Grok Build: `grok plugin install` from https://github.com/fiskmas-dev/fiskmas-grok-plugin (or marketplace `fiskmas` once listed)

## Verify

Call `whoami`. Then follow the `fiskmas` skill at https://fiskmas.dev/skill.md.
