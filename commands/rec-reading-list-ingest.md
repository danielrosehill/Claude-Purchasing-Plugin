---
description: Parse a reading list export (Goodreads, StoryGraph, Pocket, Instapaper, Readwise, etc.) from ingest/reading-list/ and use it to seed/update the preference profile.
---

# /reading-list-ingest

Process a books or articles reading-list export and incorporate it into the preference profile.

## Steps

### 1. Find the file

Look in `ingest/reading-list/` (or the `ingest/goodreads/` subfolder if present) for any of:

- **Goodreads** — `goodreads_library_export.csv` from My Books → Import and export
- **StoryGraph** — CSV export from account settings
- **Pocket** — `ril_export.html` or CSV
- **Instapaper** — CSV export
- **Readwise** — JSON or CSV export of saved articles/highlights
- **Calibre library** — CSV export of metadata
- **Kindle "Your Books"** — manual scrape or CSV

If none found, prompt the user to drop one in.

### 2. Parse

Use Python via Bash to normalise to a common schema:

```
{ title, author, year?, type (book|article), status (read|to-read|reading), rating?, shelves?, date_added, source }
```

For Goodreads, partition by `Exclusive Shelf` (`read`, `to-read`, `currently-reading`).

### 3. Enrich (optional)

If Open Library or Google Books MCP is installed, fetch ISBNs, subjects, and cover URLs. Cache in `context/reading-history-enriched.json`.

### 4. Hand off to the preference-curator

Spawn the `preference-curator` subagent. The curator should:

- For **read** items with high ratings (4+ stars), surface authors/subjects to lean into → **Strong likes**
- For **read** items with low ratings (1–2 stars), surface patterns to avoid → **Strong dislikes** (only generalise from clusters, not single books)
- For **to-read** items, treat as the user's existing wishlist — recommendations should complement it, not duplicate it
- Update `memory/preferences.md` with attributed inferences
- Move processed files to `ingest/reading-list/processed/`

### 5. Capture the lists

Write three context files:

- `context/books-read.md` — exclusion list for recommendations (don't recommend already-read books)
- `context/books-to-read.md` — the existing wishlist (for context, not exclusion — the recommender can endorse or extend it)
- `context/articles-saved.md` — for article-format workspaces

### 6. Confirm

Report counts per shelf, clusters identified, and updates to the profile.
