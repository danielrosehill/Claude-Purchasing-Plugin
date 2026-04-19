# Extract — Screenshots & Catalogs to CSV

Extract product information from screenshots, PDFs, and catalog images in `for-ai/` into a structured CSV at `data/extracted/products.csv`.

## Before starting

1. Read `spec.md` — note the category and currency for labelling
2. List all files in `for-ai/`:
   - Screenshots (.png, .jpg, .jpeg, .webp)
   - PDFs
   - Other image formats

## Process

### For each file

Use the Read tool (supports images + PDFs). Extract every distinct product visible with:

- `product_name` — full name / model as displayed
- `brand` — manufacturer
- `price` — raw text including currency symbol (e.g. "$299.99", "€1,299")
- `price_numeric` — just the number (for sorting)
- `currency` — code (USD, EUR, GBP, ILS, …)
- `sku` — model / SKU number if visible
- `source` — filename the product came from
- `page` — PDF page number or "1" for single images
- `notes` — sale info, stock status, warranty, anything else relevant

### What to extract

- Every distinct product with a visible price
- All pricing tiers if multiple shown
- Bundle items as separate entries
- Variants (size, colour) as separate rows if priced differently

### What NOT to extract

- Navigation / UI elements
- Ads / banners (unless they contain products)
- Products without prices (unless the user asked)
- Duplicates from the same source

### Handling ambiguity

- Cut-off name → append "[partial]"
- Unclear price → best guess + "(unclear)" in notes
- Missing brand → "Unknown"
- Unclear currency → infer from context, flag in notes

## Output

Save as `data/extracted/products.csv`. If the file exists, ask "Append or replace?"

CSV header:

```
product_name,brand,price,price_numeric,currency,sku,source,page,notes
```

## Quality checks

Before saving:

- No duplicates from the same source
- All prices have both display and numeric versions
- Currency codes consistent
- Source filenames accurate

## Summary output

```markdown
## Extraction Summary

**Sources processed**: X files
**Products extracted**: Y items

### By source
- [filename]: N products

### Price range
- Lowest: [price]
- Highest: [price]
- Currency: [primary]

### Saved to
`data/extracted/products.csv`

**Next**: Run `/research` to evaluate these against `spec.md`.
```

## Error handling

If a file can't be read:

1. Note which file failed
2. Continue with the rest
3. Report failures in the summary
4. Suggest the user re-export or re-upload
