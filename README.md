# NoteMeHere plugin

Capture, find and edit the pages of your NoteMeHere workspace from Claude Code or Codex. The plugin adds the NoteMeHere MCP server and two skills; approving the connection happens in your browser the first time — no keys to paste.

## Claude Code

```
/plugin marketplace add notemehere/notemehere-marketplace
/plugin install notemehere@notemehere
```

Then `/mcp`, pick `notemehere`, and approve the connection when it opens your NoteMeHere app.

## Codex

```
codex plugin marketplace add notemehere/notemehere-marketplace
codex plugin add notemehere@notemehere
codex mcp login notemehere
```

## Skills

- `capture-note` — saves a thought, a decision or meeting notes into the right page, or a new one.
- `find-notes` — searches your pages and reads one back.

## Without the plugin

`claude mcp add --transport http --scope user notemehere <url>` or `codex mcp add notemehere --url <url>` then `codex mcp login notemehere`, with the URL shown on Settings & members → Connect an agent.

`.mcp.json` points at the local Worker until the production Worker is deployed; set the production URL there and bump `version` in both manifests when it goes live.
