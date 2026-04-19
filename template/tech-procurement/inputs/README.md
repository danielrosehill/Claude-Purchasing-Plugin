# User Inputs

Place files here for the agent to process.

## Supported Input Types

### Screenshots
- Shopping cart screenshots from vendor websites
- Hardware specification screenshots
- Error messages or system information dialogs
- Benchmark result screenshots

### Documents
- Existing quotes or invoices (PDF, images)
- Hardware inventories
- Specification sheets

### Data Files
- Exported system information (JSON, CSV, TXT)
- Hardware detection tool outputs
- Price lists from vendors

## How to Use

1. Drop files into this directory (or subdirectories you create)
2. Tell the agent: "Process the files in /inputs"
3. The agent will analyze and incorporate the data

## File Organization

You may organize files into subdirectories:
```
inputs/
├── screenshots/
│   ├── amazon-gpu-prices.png
│   └── newegg-motherboard.png
├── quotes/
│   └── vendor-quote-2024.pdf
└── system-info/
    └── hwinfo-export.json
```

## Privacy Note

This directory may contain personal data (pricing, account info in screenshots). Review before sharing publicly.
