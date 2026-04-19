# Preference Profile

This file is the canonical source of truth for the user's taste. The `recommender` agent reads it before every recommendation; the `preference-curator` agent updates it whenever new feedback arrives or new history is ingested.

> Replace this scaffold during `/onboard`. Keep it human-editable and well-structured — the agents read it as plain markdown.

## Format scope

- **Format(s):** _e.g. podcasts; or "general-purpose across podcasts, books, films"_
- **Recommendation cadence:** _e.g. "weekly digest of 5", "on-demand only"_

## Strong likes

- _List specific creators, genres, themes, styles you actively want more of_

## Strong dislikes / no-go

- _List anything to actively avoid — topics, formats, voices, tones_

## Recently enjoyed (seed examples)

- _2–10 items you've genuinely loved, with one-line "why" each_

## Recently disliked

- _A few items you bounced off, with one-line "why" each_

## Availability context

The recommender uses these to filter out items the user can't actually access.

- **Geographical area:** _e.g. "Israel", "UK", "US — west coast"_
- **Streaming services:** _e.g. "Netflix, Disney+, Apple TV+; not Prime"_
- **Reading formats:** _e.g. "Kindle preferred; physical for art books; library ebook ok"_
- **Podcast app:** _e.g. "Pocket Casts", "Apple Podcasts"_
- **Course platforms:** _e.g. "Coursera, O'Reilly, free YouTube"_
- **YouTube context:** _e.g. "Premium; happy to subscribe to new channels"_

## Constraints

- **Length:** _e.g. "podcast episodes under 60 min", "books under 400 pages", "courses under 10 hours"_
- **Language:** _e.g. "English; Hebrew okay; subtitles fine for film/TV"_
- **Other:** _anything else that filters the candidate pool_

## Open questions / experiments

- _Things you're curious to explore — the recommender can lean into these_

## Update log

- _The preference-curator appends dated lines here when it changes the profile based on feedback or ingest_
