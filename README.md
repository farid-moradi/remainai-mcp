# RemainAI MCP server

RemainAI is a place to capture notes, todos, saved words, feeds and rituals, filed under your own tags. This is its hosted MCP server: connect it to Claude, Claude Code or any MCP client, and every assistant you use reads and adds to the same library.

- Endpoint: `https://mcp.remainai.org/mcp`
- Transport: Streamable HTTP
- Auth: OAuth 2.1 with PKCE and dynamic client registration. No API key to copy: your client opens a RemainAI page where you approve it and choose what it may do.
- Registry: `org.remainai/remainai` in the official MCP Registry
- Website: https://remainai.org/mcp-memory

This repository holds the documentation and the registry entry. The server itself is hosted at the address above; you do not run anything locally.

## Connect

**Claude (web and desktop):** Settings, Connectors, add a custom connector with `https://mcp.remainai.org/mcp`.

**Claude Code:**

```sh
claude mcp add --transport http RemainAI https://mcp.remainai.org/mcp
```

**Any other client:** point it at the endpoint. It reads the discovery documents off the 401, registers itself and sends you to the approval page.

**Local, over stdio:** if the `remain` command line client is installed and signed in (`apt install remain`, see https://remainai.org/terminal-notes), `claude mcp add RemainAI -- remain mcp` uses its credentials and skips the browser.

## Tools

Each connection sees only the tools its permissions cover.

**Read your library** (`notes.read`): `search_notes`, `read_note`, `list_notes`, `list_todos`, `list_tags`, `read_tag`, `list_folders`, `list_posts`, `list_feeds`, `list_feed_items`, `read_article`, `list_rituals`

**Add and change** (`notes.write`): `capture`, `update_note`, `trash_note`, `restore_note`, `publish_post_update`, `update_articles`, `file_article`, `mark_ritual`. Nothing is deleted for good: the Trash keeps things for 30 days.

**Spend AI credits** (`ai`): `ask`, `summarize_article`. Reading is free.

The full, always current list with descriptions: https://mcp.remainai.org/llms.txt

## Privacy and control

Every connection is approved by you, per permission, and listed in RemainAI's Settings, where you can end it. Notes and articles are treated as data, never as instructions. Details: https://remainai.org/privacy

## Support

support@remainai.org
