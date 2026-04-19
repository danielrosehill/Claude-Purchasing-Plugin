---
description: User provides something they enjoyed (a film, book, podcast, video, course, etc.); the recommender suggests similar items they might also enjoy, grounded in the preference profile.
---

# /more-like-this

The user provides one specific item they enjoyed — by title, URL, or short description — and the recommender returns a curated set of similar items they might also enjoy.

## Steps

### 1. Capture the seed item

Accept the seed inline (`/more-like-this Severance`) or ask the user:

- **What did you enjoy?** — title, URL, ISBN, RSS, or short description
- **What specifically did you like about it?** — optional but very useful (the host's voice, the slow-burn pacing, the prose style, the structured exercises, etc.)
- **Format constraint:** stick to the same format only, or open to recommendations across any format covered by this workspace?

### 2. Resolve the seed

- If it's already in `recommendations/` or `feedback/`, pull the existing metadata
- Otherwise, use any installed MCPs (TMDB, Open Library, Listen Notes, YouTube Data API, etc.) to fetch canonical metadata — title, creators, themes, IDs

### 3. Read the preference profile and history

- Read `memory/preferences.md` for taste, constraints, availability
- Scan `recommendations/` and `feedback/` to avoid suggesting items already shown or already disliked

### 4. Hand off to the recommender agent

Spawn the `recommender` subagent (Agent tool) with:

- The seed item and its metadata
- What the user said they liked about it
- The full preference profile
- The exclusion list (already-recommended, already-disliked)
- The format constraint

The recommender returns 3–7 candidates. Each candidate is written to `recommendations/<format>/YYYY-MM-DD-<slug>.md` with frontmatter linking back to the seed (`seed: <path>` and `seed_reason: "more-like-this"`).

### 5. Present the results

Show the user a compact list — title, format, one-line "why this is similar in the way you cared about", availability status (where they can get it given their preferred services).

### 6. Nudge feedback

Remind the user that running `/log-feedback` against any of these will sharpen future "more like this" requests.
