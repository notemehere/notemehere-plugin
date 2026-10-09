---
name: capture-note
description: Save something into the person's NoteMeHere notes — a thought, a decision, a snippet, meeting notes — when they say "note this", "save this to my notes", "add to the X page", "remember that…". Finds the right page first, appends to it or creates a new one, through the notemehere MCP server.
---

# Capture a note

Without the notemehere MCP server connected this skill does nothing: say so and point the person at Settings & members → Connect an agent in their NoteMeHere app.

Tools, as the plugin exposes them: `mcp__plugin_notemehere_notemehere__search_pages` (hybrid: words and meaning), `…__list_pages`, `…__get_page`, `…__append_to_page`, `…__create_page`, `…__add_comment`, `…__set_properties`, `…__list_workspaces`.

## Where it goes

1. If the person names a page, `search_pages` for it (title match first). One clear hit → use it. Several → ask which, in one question.
2. If they do not name one, search for the subject. A page that is obviously about it → append there. Nothing fitting → create a page: a short title a stranger understands, at the root unless a parent is obvious.
3. More than one workspace (`list_workspaces`) and no hint which → ask once, then remember for the conversation.

## What to write

Markdown, in the person's own words where they gave them, tidied: headings for sections, `- [ ]` for things to do, `>` for quotes, `<aside data-callout="💡">…</aside>` for a highlight. Start an appended note with a `##` line that dates or names it when the page already has content. Never rewrite what is already on the page; `append_to_page` adds, `update_page` replaces the whole body — use it only when the person asks to rewrite.

## Suggesting instead of writing

When the person asks for an opinion on a page, or you want to propose a change you are not sure about, use `add_comment` on that page — it appears under the page signed as the agent — rather than editing the body. If the page sits in a table (its parent has `child_schema`), set the fields with `set_properties` (e.g. status, due date) instead of writing them into the text.

## Report back

One line: what you added, to which page (its title), and that it is saved. No need to paste the note back.
