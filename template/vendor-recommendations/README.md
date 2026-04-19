> This repository is a template provided as part of the [New Repo From Template Plugin](https://github.com/danielrosehill/New-Repo-From-Template-Plugin) for Claude Code.

# Claude Recommendation Workspace Template

A Claude Code workspace for AI-assisted content recommendations. Set it up once, feed it your preferences and listening/watching/reading history, then ask for recommendations that get sharper over time as you log feedback.

## What it does

- Holds your taste profile in `memory/preferences.md`
- Generates targeted recommendations grounded in that profile
- Tracks what you liked, disliked, and have already been shown so suggestions don't repeat or miss
- Optionally pulls metadata from MCP servers (TMDB for films/TV, Open Library for books, etc.)

## Format flexibility

Run as a general-purpose recommender or specialise it to one format (podcasts, books, films, TV, articles, music, games, papers, newsletters, YouTube, etc.). The format is chosen during `/onboard` and shapes the folder layout and which ingest commands are most useful.

## Getting started

After cloning, run:

```
/onboard
```

This interactive flow will:

1. Ask whether the workspace is general-purpose or format-specific
2. Capture initial preference notes (favourite creators, genres, no-go topics, etc.)
3. Offer to ingest existing data — OPML for podcasts, Goodreads CSV for books, Letterboxd/Trakt export for films, etc.
4. Build the folder structure under `recommendations/` and `ingest/` to suit the format
5. Recommend MCPs to install for richer metadata

Then any of:

- `/recommendations` — list and review past suggestions
- `/log-feedback` — close the loop on a previous recommendation
- `/opml-ingest`, `/watch-history-ingest`, `/reading-list-ingest` — bulk-import existing history

## Folder map

```
memory/             preferences.md — your taste profile
recommendations/    one .md per recommendation, dated
feedback/           likes/dislikes/notes logged against recs
ingest/             OPML, CSV, JSON drops awaiting parse
context/            anything captured during /onboard
outputs/            digests, summaries, exports
.claude/            commands + agents
```

## Suggested MCPs

See `mcp.md` for per-format MCP suggestions (TMDB, Open Library, Listen Notes, Goodreads, etc.).
