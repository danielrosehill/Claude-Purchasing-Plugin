---
description: Re-run the shortlist against the current spec and write a new dated recommendations file
---

# Recompare

Re-run the candidate shortlist against the current `spec.md`. Useful when the spec has changed, pricing has moved, or new candidates have appeared since the last recommendation.

## Steps

1. **Read the current state:**
   - `spec.md` — including per-purchase overrides and the Standing preferences snapshot
   - The most recent file in `from-ai/recommendations/` (if any)

   Note any changes since the most recent recommendations file — spec edits, added/removed must-haves or hard nos, updated priorities.

2. **Refresh the candidate set.**
   - Re-read everything in `for-ai/` (especially `for-ai/catalogs/` if organised by vendor)
   - Re-read `from-ai/research.md` if it exists
   - Do NOT assume the previous shortlist is still valid — a spec change (e.g. new budget cap, new hard no) can disqualify previous picks

3. **Refresh pricing.** Any price in `data/products/[brand]-[model].json` older than 7 days must be re-fetched.

4. **Score each candidate** against the current spec. Explicitly call out any previously-recommended models that no longer fit, and why.

5. **Write a NEW dated file** at `from-ai/recommendations/recommendations-YYYY-MM-DD.md`. **Never overwrite** an existing dated file — history matters.

   Structure:
   - Top pick
   - Runner-up
   - Budget alternative (if applicable)
   - Also considered (and why not)
   - One-line final recommendation
   - **Changes vs. previous recommendations file** (required if one exists)

6. **Offer to regenerate the PDF.** Ask: "Recommendations updated. Regenerate the PDF report? (/recommend)"
