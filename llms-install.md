# Installing the Soontra MCP server

Soontra is a hosted remote MCP server. There is nothing to clone, build, or
install, and there are no API keys or environment variables. Setup is: add the
server entry for your client below, then sign in with your Soontra account
when the OAuth prompt opens and approve access.

- Server URL: https://app.soontra.com/api/mcp
- Transport: Streamable HTTP
- Auth: OAuth 2.1 with dynamic client registration. The endpoint's
  protected-resource metadata points clients at Soontra's authorization
  server automatically; the user signs in and approves, and the client
  stores the token.

## Cline (VS Code) — cline_mcp_settings.json

```json
{
  "mcpServers": {
    "soontra": {
      "url": "https://app.soontra.com/api/mcp",
      "type": "streamableHttp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

The `"type": "streamableHttp"` field is required. Without it Cline defaults
to legacy SSE and the connection fails. After saving, Cline opens the Soontra
OAuth sign-in in the browser; once approved, the Soontra tools load.

## Cursor — .mcp.json

```json
{
  "mcpServers": {
    "soontra": {
      "url": "https://app.soontra.com/api/mcp"
    }
  }
}
```

## Generic MCP clients

Any client that supports remote Streamable HTTP servers with OAuth can
connect with just the server URL above.

## What the tools do

Through the server, the client searches the same workspace the Soontra app
searches: find exact moments in recordings, pull files, folders and
transcripts, read YouTube/Instagram/TikTok analytics, and create post drafts.
Drafts only — publishing always happens in the Soontra app, never through the
MCP server.
