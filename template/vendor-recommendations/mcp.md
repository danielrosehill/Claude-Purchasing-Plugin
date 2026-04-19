# Suggested MCP Servers

MCPs are optional but strongly recommended — they let the `recommender` agent pull canonical metadata, IDs, and cross-references rather than guessing from training data.

## By format

### Films & TV
- **TMDB** — comprehensive film/TV metadata, cast, ratings, watch providers
- **Trakt** — personal watch history sync if you maintain a Trakt account
- **Letterboxd** (via web fetch) — film-buff reviews and lists

### Books
- **Open Library** — ISBNs, editions, subjects, work-level metadata
- **Google Books** — covers, previews, descriptions
- **Goodreads** (via web fetch / CSV import) — reviews and shelf data

### Podcasts
- **Listen Notes** — podcast/episode search and metadata
- **Podchaser** — podcast database with credits and reviews
- **iTunes Search API** (via fetch) — basic show lookup

### Music
- **MusicBrainz** — open music metadata
- **Last.fm** — listening history and similar-artist data
- **Spotify** (via Web API MCP) — your library, playlists, audio features

### Articles & long-form
- **Pinecone** or another vector store — semantic search over your saved articles
- **Pocket / Instapaper / Readwise** exports — bulk import history
- **Hacker News API** (via fetch) — surface recent technical writing

### YouTube
- **YouTube Data API MCP** — channel/video metadata, your subscriptions
- **yt-dlp** (via shell) — pull metadata for any URL

### Academic papers
- **arXiv MCP** — search and fetch preprints
- **Semantic Scholar** — citation graph and recommendations
- **Hugging Face papers** — ML/AI paper discovery

### Games
- **IGDB** — comprehensive game metadata
- **Steam Web API** — your library, playtime, wishlist

## General-purpose

- **Web fetch / Tavily** — fall back to web search when no specialised MCP exists
- **Fetch-and-convert** — turn any URL into clean markdown for ingestion

## Installing

Most of these are available in the user's MCP Jungle or as Claude Code plugins. Run `/onboard` and the preference-curator agent will suggest specific servers based on the chosen format.
