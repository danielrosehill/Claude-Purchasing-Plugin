---
description: Parse a watch history export (Netflix, Trakt, Letterboxd, JustWatch, etc.) from ingest/watch-history/ and use it to seed/update the preference profile.
---

# /watch-history-ingest

Process a film/TV watch history export and incorporate it into the preference profile.

## Steps

### 1. Find the file

Look in `ingest/watch-history/` for any of:

- **Netflix** — CSV from Account → Profile → Viewing activity → Download all
- **Trakt** — JSON or CSV from `https://trakt.tv/users/<you>/history`
- **Letterboxd** — ZIP from Settings → Import & Export → Export your data (contains `watched.csv`, `ratings.csv`, `diary.csv`)
- **JustWatch** — CSV export of watchlist/seen list
- **Plex / Jellyfin** — exported activity logs

If none found, prompt the user to drop one in. If multiple, process each in turn.

### 2. Parse

Use Python via Bash to load the file. Normalise to a common schema:

```
{ title, year, type (movie|series), date_watched, rating?, source }
```

For Letterboxd, prefer `ratings.csv` (gives explicit 0.5–5 star ratings) over `watched.csv`.

### 3. Enrich (optional but recommended)

If TMDB MCP is installed, look up each title to get canonical IDs, genres, cast, and watch-provider data. Cache the enriched data in `context/watch-history-enriched.json`.

### 4. Hand off to the preference-curator

Spawn the `preference-curator` subagent with the parsed/enriched history. The curator should:

- Identify clusters: directors the user returns to, genres over-indexed in their history, eras, languages, runtime patterns
- For Letterboxd ratings, weight the analysis by rating (5-star items signal strong likes; 1-star signals strong dislikes)
- Write inferences to `memory/preferences.md` under **Strong likes** and **Strong dislikes**, with attribution
- Move processed files to `ingest/watch-history/processed/`

### 5. Capture the seen-list

Write `context/seen-films.md` and `context/seen-series.md` with the de-duplicated lists. The recommender uses these as exclusion lists so it never suggests something already watched.

### 6. Confirm

Report number of items imported, taste clusters identified, and what was added to the profile.
