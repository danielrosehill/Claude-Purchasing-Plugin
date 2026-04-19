# Data Directory

This directory stores data retrieved by the agent or provided by the user.

## Subdirectories

- **`/pricing/`** - Cached pricing data from vendors
- **`/specs/`** - Component specifications and datasheets
- **`/benchmarks/`** - Benchmark data for comparison

## Data Sources

The agent may retrieve data from:
- Vendor websites (via web fetch)
- Price comparison APIs
- Hardware specification databases
- Benchmark databases

## Freshness

Pricing data should be considered time-sensitive. The agent will note retrieval dates on all pricing files.

## Privacy Note

This directory may contain cached web data. Review before sharing the repository publicly.
