# Security Policy

## Reporting a vulnerability

Email **security@fiskmas.dev** with a description of the issue and, if possible,
a reproduction or proof of concept. We aim to acknowledge reports within 2
business days and to give a fix or an assessment within 7 days.

Please do not open a public issue for a security report.

## What this plugin touches

The plugin is a thin MCP client. It does not execute arbitrary code on your
machine beyond the MCP connection the agent makes. The plugin itself ships:

- An MCP server pointer (`.mcp.json` / `.grok-plugin/mcp.json`) pointing at
  `https://mcp.fiskmas.dev/mcp`, which carries the `FISKMAS_TOKEN` header
  from the `FISKMAS_TOKEN` environment variable.
- A static `skills/` directory — plain-text `SKILL.md` files the agent reads.
- No build step, no postinstall, no network access beyond the MCP server, no
  file reads outside the plugin directory.

The only credential it uses is the `FISKMAS_TOKEN` environment variable at
runtime. The plugin never reads tokens or environment variables that it does
not document, and it never sends data to any endpoint other than the MCP
server, the registry (only when a human runs `docker login`/`docker push` on
the agent's behalf), and the landing page.

## Network endpoints

| Endpoint | Purpose |
|---|---|
| `https://mcp.fiskmas.dev/mcp` | The MCP server itself |
| `registry.fiskmas.dev` | Docker registry — `docker login` / `docker push` only |
| `https://fiskmas.dev` | Human-facing landing page (account creation, upgrade) |
| `https://<slug>-app.fiskmas.dev` | A customer's app, after deployment |
| `https://fiskmas.dev/api/dumps/<dump_id>/<token>` | Presigned dump download URL handed to the human |

## License

MIT. See `LICENSE`.
