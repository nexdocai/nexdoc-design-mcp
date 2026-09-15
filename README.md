# NexDoc Design MCP

[Model Context Protocol](https://modelcontextprotocol.io) server for [NexDoc Design](https://www.nexdoc.design) — generate, update, export, and publish production-ready designs from Claude, ChatGPT, Cursor, and other MCP clients.

**Source for this package lives in a private monorepo.** This public repo is the registry / docs surface. Install from npm or connect to the hosted endpoint below.

## Quick start (recommended)

### Remote HTTP + OAuth (ChatGPT, Claude, Cursor)

Add this MCP URL and complete the browser login. Do **not** paste an API key.

```
https://mcp.nexdoc.design/mcp
```

If a client offers **OAuth** vs **Token / API key**, choose **OAuth**.

### Local stdio (API key)

```json
{
  "mcpServers": {
    "nexdoc": {
      "command": "npx",
      "args": ["-y", "@nexdoc/mcp-server"],
      "env": {
        "NXD_API_KEY": "nxd_live_...",
        "NXD_API_URL": "https://api.nexdoc.design"
      }
    }
  }
}
```

Create an API key in your NexDoc account settings. Package: [`@nexdoc/mcp-server`](https://www.npmjs.com/package/@nexdoc/mcp-server).

## Tools

| Tool | Purpose |
|------|---------|
| `create_design` | Create/reuse a job and start a run |
| `update_design` | New run with edit instructions |
| `request_file_upload` | Presigned URL for a photo/logo (PUT original bytes, then pass `file_ids`) |
| `check_file` | Confirm an uploaded file is `ready` |
| `upload_file` | stdio only: read a local path and upload |
| `check_run` | One-shot status (fresh `viewer_url`) |
| `refresh_preview` | New preview link if the old one expired |
| `wait_for_run` | Short poll after create/update (default ~45s). Do not loop |
| `notify_run_email` | Email when the run finishes |
| `list_runs` | Runs for a job |
| `export_design` | `pdf`, `html`, or `png` → download URL |
| `publish_design` / `unpublish_design` | Public URL — only when the user asks |
| `list_formats` | Format catalog |
| `get_balance` | Wallet summary |

## Example prompt

> Create a business card for Jane Doe, Founder at Acme. Dark minimal layout. Give me the job id as soon as it starts, then the viewer URL and a PDF when it is ready.

## Links

- Product: [nexdoc.design](https://www.nexdoc.design)
- npm: [`@nexdoc/mcp-server`](https://www.npmjs.com/package/@nexdoc/mcp-server)
- Hosted MCP: [mcp.nexdoc.design/mcp](https://mcp.nexdoc.design/mcp)

## License

MIT
