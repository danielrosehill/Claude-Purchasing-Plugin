# Compare — Side-by-Side Product Comparison

Generate a focused comparison of 2–4 specific products without going through the full research/recommend flow. Useful when the user has narrowed down candidates and wants to scan them side by side.

## Usage

The user may invoke with products inline ("compare the TP-Link AX3000 vs Netgear Nighthawk") or just run `/compare` and be prompted.

## Before comparing

1. Read `spec.md` — to apply priorities when declaring a winner
2. Check `for-ai/` — user may have dropped sources for these specific products

## Process

1. **Identify products** — ask if not specified
2. **Gather per product**:
   - Full specifications
   - Current price in the spec's currency
   - International RRP for markup calc
   - Review aggregate
   - Manufacturer reputation (quick)
   - Must-haves satisfied (from spec)
   - Hard nos clear (from spec)

## Output

Write `from-ai/compare.md`:

```markdown
# Comparison: [Category]

**Date**: [Date]
**Products**: [Count]
**Spec priorities**: [From spec.md]

## Quick summary

| | [Product A] | [Product B] | [Product C] |
|---|---|---|---|
| **Price** | [Amount] | [Amount] | [Amount] |
| **vs RRP** | +X% | +X% | +X% |
| **Reviews** | X.X/5 | X.X/5 | X.X/5 |
| **Best for** | [1–2 words] | [1–2 words] | [1–2 words] |

## Must-haves

| Must-have | [A] | [B] | [C] |
|-----------|-----|-----|-----|

## Hard nos

| Hard no | [A] | [B] | [C] |
|---------|-----|-----|-----|

## Specs

| Spec | [A] | [B] | [C] |
|------|-----|-----|-----|

## Build quality

| Product | Assessment |
|---------|------------|

## Value analysis

| Product | Price | RRP | Markup | Verdict |
|---------|-------|-----|--------|---------|

## Winner by category

- **Best value**: [Product]
- **Best build**: [Product]
- **Best spec match**: [Product]
- **Best for [spec use case]**: [Product]

## Bottom line

[1–2 sentences naming the winner and why, referencing the spec's priorities]
```

## Guidelines

- Use tables — this is a scan tool
- Highlight meaningful differences, not just list specs
- Apply spec priorities when calling winners
- Be opinionated — the user wants guidance

## After comparison

Ask: "Want me to run a full `/research` + `/recommend` flow for the PDF report, or dig deeper on any of these?"
