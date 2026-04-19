---
description: Parse an OPML file (typically a podcast subscription export) from ingest/opml/ and use it to seed/update the preference profile.
---

# /opml-ingest

Parse OPML files dropped in `ingest/opml/` and incorporate the user's existing podcast subscriptions into the preference profile.

## Steps

### 1. Find the file

- Look in `ingest/opml/` for `.opml` files
- If none, prompt the user to drop one in (most podcast apps export OPML — Pocket Casts, Apple Podcasts, Overcast, AntennaPod, etc.)
- If multiple, ask which to use (or process all)

### 2. Parse

Use a small Python or node one-liner via Bash to extract from each `<outline>`:

- Show title (`text` or `title` attribute)
- Feed URL (`xmlUrl`)
- Category (parent `<outline>` text, if any)

### 3. Hand off to the preference-curator

Spawn the `preference-curator` subagent (Agent tool) with the parsed list. The curator should:

- Group shows by inferred theme/genre (using MCPs like Listen Notes or Podchaser if available)
- Identify clusters that reveal taste (e.g. "lots of long-form interviews on history", "heavy on tech/business commentary")
- Write inferences into `memory/preferences.md` under **Strong likes** with attribution (e.g. "inferred from OPML ingest 2026-04-15 — N shows in this cluster")
- Move the processed OPML to `ingest/opml/processed/` with the date in the filename

### 4. Capture the raw subscription list

Write `context/subscriptions-podcasts.md` listing all imported shows with their feed URLs — useful for the recommender to know what's already in the user's regular rotation (so it doesn't recommend shows they already follow).

### 5. Confirm

Tell the user how many shows were imported, what taste clusters were inferred, and what was added to the profile.
