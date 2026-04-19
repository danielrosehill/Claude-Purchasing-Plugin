---
description: Compare local market prices against international RRP with import-cost realism
argument-hint: [model names, optional — defaults to current shortlist]
---

# Market Check

Compare local market pricing against international RRP for the current shortlist (or the models in `$ARGUMENTS` if provided).

## Steps

1. **Identify the models:**
   - If `$ARGUMENTS` is provided, use that list.
   - Otherwise, use the top picks from the most recent file in `from-ai/recommendations/`, or the CONSIDER candidates from `from-ai/research.md`.

2. **Get local prices** from `for-ai/catalogs/[vendor]/` (or `data/extracted/products.csv` if `/extract` has been run). Fall back to the pricing in `data/products/[brand]-[model].json` if cached.

3. **Look up international RRP** for each model. Priority order for the source:
   1. Official manufacturer site
   2. Official regional distributor site
   3. Major reputable retailers (sanity check only)

   Use WebFetch/WebSearch. Never guess prices.

4. **Convert currencies** using a live rate (fetch from a current source, never hardcode). The user's local currency is in the Standing preferences snapshot in `spec.md`.

5. **Build a comparison table:**

   | Model | Local price | Local (USD eq.) | Intl RRP (USD) | Δ (USD) | Δ (%) | Verdict |
   |---|---|---|---|---|---|---|

   Verdict values:
   - `cheaper locally` — local price beats RRP
   - `parity` (±5%)
   - `mild markup` (5–20%)
   - `heavy markup` (>20%)

6. **Apply the effective markup threshold.** Read it from `spec.md` (per-purchase override first, then the Standing preferences snapshot default). Flag any model above the threshold.

7. **Factor in import realism.** An international RRP is not directly accessible to the buyer. Importing typically adds **~25–35%** for shipping + VAT/duties + customs handling, depending on country and category. Factor this into the final recommendation — a "heavy markup" locally can still be cheaper than importing.

8. **Write the result** to `from-ai/research/market-check-YYYY-MM-DD.md` and print the table inline.

9. **End with a one-line recommendation:** buy local, import, or mixed (which specific items to source where).
