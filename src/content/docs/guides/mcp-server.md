---
title: Configure the MCP Server
description: Connect AI assistants to your Yokoi manuscripts using the built-in Model Context Protocol server.
draft: false
---

Yokoi includes a built-in [Model Context Protocol (MCP)](https://modelcontextprotocol.io) server. This lets you connect AI assistants — like Claude — directly to your account so they can read and write manuscripts, query your story bible, manage chapters, and more.

## Prerequisites

- A Yokoi account at [editor.yokoi.app](https://editor.yokoi.app)
- An API key (see below)
- An MCP-compatible client (Claude Desktop, Cursor, etc.)

## Step 1: Create an API key

1. Log in to [editor.yokoi.app](https://editor.yokoi.app/login)
2. Go to **Settings → API Keys**
3. Click **New API Key**, give it a name (e.g. `Claude Desktop`), and choose an expiry
4. Copy the key — it is shown only once

## Step 2: Configure your MCP client

### Claude Desktop

Add the following to your Claude Desktop configuration file (`claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "yokoi": {
      "url": "https://editor.yokoi.app/mcp",
      "headers": {
        "X-API-Key": "YOUR_API_KEY"
      }
    }
  }
}
```

Replace `YOUR_API_KEY` with the key you copied in Step 1.

### Other MCP clients

Use these transport details:

| Setting | Value |
|---|---|
| Transport | Streamable HTTP |
| Endpoint | `POST https://editor.yokoi.app/mcp` |
| Auth header | `X-API-Key: YOUR_API_KEY` |
| `Accept` header | `application/json, text/event-stream` |

After the `initialize` request, the server returns an `mcp-session-id` header. Pass this header in all subsequent requests for the same session.

## Available tools

Once connected, your AI assistant can use tools such as:

- `book_list` — list your manuscripts
- `book_create` — create a new manuscript
- `chapter_list` — list chapters in a manuscript
- `chapter_create` / `chapter_update` — write or edit chapters
- `bible_character_list` — query story bible characters
- …and more

Ask your AI assistant to `list available tools` to see the full set.

## Session lifecycle

```
POST /mcp   ← initialize (include Accept header)
              ← returns mcp-session-id

POST /mcp   ← tool calls (include mcp-session-id header)

DELETE /mcp ← close session (include mcp-session-id header)
```

Sessions remain open until you explicitly close them or they expire.
