# {{PROJECT_NAME}}

{{DESCRIPTION}}

This is a Claude Code workspace for AI-assisted content recommendations. It learns the user's preferences over time, generates targeted recommendations, and tracks feedback so future suggestions improve.

## Format

**Format(s):** {{FORMAT}}

The workspace can be general-purpose or specialised for any combination of these supported formats (non-exclusive — pick one, several, or all):

- Movies
- Netflix Series (and other streaming series)
- Podcasts
- Books
- YouTube Videos
- Online Courses

The format set is chosen during `/onboard` and shapes which ingest commands, MCPs, and recommendation fields are most relevant. Other formats (music, games, papers, newsletters, etc.) can be added as custom formats during onboarding.

## Availability context

Recommendations are useless if the user can't actually access them. The preference profile must capture availability constraints so the recommender filters accordingly:

- **Geographical area** (country, region) — affects streaming catalogues, library access, course availability
- **Preferred streaming services** (Netflix, Prime, Disney+, Apple TV+, etc.) — for film/TV
- **Preferred reading formats** (physical, Kindle, Audible, library ebook, web) — for books
- **Preferred podcast app / platform** — affects feed availability
- **Preferred course platforms** (Coursera, edX, Udemy, O'Reilly, YouTube) — for online courses
- **Preferred YouTube viewing context** (subscriptions vs discovery, Premium status) — for video

## Folder structure

| Folder | Purpose |
|--------|---------|
| `memory/` | The user's preference profile — `preferences.md` is the authoritative source of taste |
| `recommendations/` | One markdown file per recommendation, dated, with metadata and reasoning |
| `feedback/` | Likes/dislikes/notes logged against past recommendations |
| `ingest/` | Drop zone for OPML, watch history exports, reading list exports, etc. |
| `context/` | User-provided context captured during `/onboard` |
| `outputs/` | General agent work product (digests, summaries, exports) |

The exact subfolder layout under `recommendations/` and `ingest/` is created dynamically by `/onboard` based on the chosen format and use case.

## Working conventions

- **Memory is canonical.** `memory/preferences.md` is the source of truth for the user's taste. Never recommend something without consulting it first.
- **Every recommendation is a file.** Write one markdown file per recommendation under `recommendations/`, named `YYYY-MM-DD-<short-slug>.md`. Include the title, a 1–3 sentence reasoning grounded in the preference profile, and links/identifiers (ISBN, IMDb ID, RSS URL, etc.).
- **Feedback closes the loop.** When the user logs feedback via `/log-feedback`, update `memory/preferences.md` with the learning (what to lean into, what to avoid). Don't just append to `feedback/` — update the profile.
- **Avoid repeats.** Before recommending, scan `recommendations/` and `feedback/` to make sure the item hasn't already been suggested or rejected.
- **Cite sources.** When using an MCP (TMDB, Open Library, Listen Notes, etc.) to pull metadata, include the source and any IDs in the recommendation file so it can be verified.

## Commands

- `/onboard` — first-run setup: pick format(s), capture initial preferences and availability, build the folder structure
- `/recommendations` — view recent recommendations and their feedback status
- `/more-like-this` — user provides something they enjoyed; recommender suggests similar items they might also enjoy
- `/log-feedback` — record a like / dislike / nuanced reaction against a past recommendation
- `/opml-ingest` — import an OPML file (e.g. existing podcast subscriptions) into the preference profile
- `/watch-history-ingest` — import a watch history export (e.g. Netflix, Trakt, Letterboxd)
- `/reading-list-ingest` — import a reading list export (e.g. Goodreads, Pocket, Instapaper)

## Agents

- `preference-curator` — interviews the user, parses ingested history, and maintains `memory/preferences.md`
- `recommender` — generates new recommendations grounded in preferences and feedback history

## MCPs

See `mcp.md` for suggested MCP servers per format (TMDB, Open Library, etc.). MCPs are optional but greatly improve recommendation quality.
