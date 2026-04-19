# data — Structured caches

## Layout

```
data/
├── extracted/
│   └── products.csv       # Output of /extract — products pulled from screenshots/PDFs
└── products/
    └── [brand]-[model-slug].json   # Per-product cached specs + pricing (for re-runs)
```

One repo = one purchase, so no per-purchase nesting.

## `extracted/products.csv` schema

| Column | Description |
|--------|-------------|
| `product_name` | Full product name / model |
| `brand` | Manufacturer |
| `price` | Raw text with currency symbol |
| `price_numeric` | Number only (sortable) |
| `currency` | Code (USD, EUR, ILS, GBP, …) |
| `sku` | SKU / model number |
| `source` | Source filename |
| `page` | PDF page or "1" |
| `notes` | Stock, warranty, sale, flags |

## `products/` cache format

`[brand]-[model-slug].json`:

```json
{
  "brand": "Sony",
  "model": "WH-1000XM5",
  "category": "headphones",
  "fetched": "2026-04-16",
  "specs": {...},
  "pricing": [
    {"vendor": "Amazon", "price": 349.99, "currency": "USD", "url": "...", "checked": "2026-04-16"}
  ],
  "reviews": {...}
}
```

Cache behaviour:

1. Check before fetching
2. If <7 days old → reuse
3. Always refresh pricing (changes often), specs can stay cached longer

## Usage

- `/extract` writes to `extracted/products.csv`
- `/research` reads both `extracted/` and `products/`, writes new fetches back into `products/`
