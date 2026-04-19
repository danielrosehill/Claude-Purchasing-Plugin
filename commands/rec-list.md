---
description: List recent recommendations from the recommendations/ folder with their feedback status (liked, disliked, no-response, queued).
---

# /recommendations

Surface the recommendation history so the user can see what's been suggested, what they engaged with, and what's still open.

## Steps

1. Read all `.md` files under `recommendations/` (recurse subfolders for multi-format workspaces).
2. For each recommendation, look up matching feedback in `feedback/` (match by recommendation slug or filename).
3. Group by status: **Liked**, **Disliked**, **Mixed/Notes**, **No feedback yet** (queued).
4. Within each group, sort by date desc.
5. Render a compact table per group: date, title, format, link/ID, one-line "why recommended".
6. At the end, summarise:
   - Total recommendations to date
   - Hit rate (likes / items with any feedback)
   - Suggest the user run `/log-feedback` if there are stale "no feedback yet" items older than ~2 weeks

## Args

- Optional filter: format (`movies`, `books`, `podcasts`, etc.) — if provided, restrict to that subfolder
- Optional filter: `--unrated` to show only items with no feedback yet
