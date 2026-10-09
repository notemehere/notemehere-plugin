---
name: find-notes
description: Look things up in the person's NoteMeHere notes — "what did I write about X", "find my notes on", "open the page about", "what's in my Y page", "summarise my notes on" — through the notemehere MCP server, and read a page's Markdown back.
---

# Find and read notes

Without the notemehere MCP server connected this skill does nothing: say so and point the person at Settings & members → Connect an agent in their NoteMeHere app.

Tools, as the plugin exposes them: `mcp__plugin_notemehere_notemehere__search_pages` (hybrid: words and meaning — a natural-language query works), `…__list_pages`, `…__get_page`, `…__query_pages` (a parent's children as a table with filters), `…__recent_changes` ("what changed today"), `…__list_comments`, `…__list_versions`, `…__list_workspaces`.

## Searching

`search_pages` matches titles and bodies, case-insensitively, and returns a snippet. Try the person's words first; if nothing comes back, try one or two synonyms before saying there is nothing. To browse instead of search, `list_pages` gives the roots, then the children of a page (`has_children` says which have any).

## What changed

"What did I write this week" / "what's new" → `recent_changes` with the right `hours`, then summarise per page; open the ones the person asks about.

## Reading

`get_page` returns the Markdown body and the breadcrumb. Quote the page where the exact wording matters; summarise otherwise. Name the page (its title and where it sits in the tree) so the person can open it.

## Editing from here

If the person asks to change what they found, hand over to `capture-note` for additions; a rewrite uses `update_page` with the full new body and only after they confirmed.
