# Generate Formal Estimate

You are creating a formal cost estimate document that can be used for internal approval, accountant review, or VAT deduction purposes.

## Prerequisites

Check for:
- Recommendations in `/outputs/recommendations/`
- User context (especially business name, currency, VAT requirements)

## Estimate Types

### Standard Estimate
For personal use - clean, professional format

### VAT-Compliant Estimate
For business use - includes:
- Separate net/gross amounts
- VAT rate and amount
- Business name prominently displayed
- Format suitable for accountant submission

---

## Process

### 1. Gather Information

Confirm with user:
- Which components to include
- Preferred vendors (for sourcing)
- Estimate validity period (default: 7 days due to price fluctuations)
- Business name if applicable
- VAT rate if applicable

### 2. Verify Current Pricing

For each component:
- Fetch current price from vendor
- Confirm availability
- Note product URLs

### 3. Generate Estimate

---

## Standard Estimate Format

```markdown
# Hardware Upgrade Estimate

**Date:** YYYY-MM-DD
**Valid Until:** YYYY-MM-DD
**Prepared For:** {User/Business Name}
**Currency:** {Currency Code}

---

## Components

| Item | Description | Vendor | Unit Price | Qty | Total |
|------|-------------|--------|------------|-----|-------|
| GPU | NVIDIA RTX 4070 Super | Amazon | $599.00 | 1 | $599.00 |
| RAM | Corsair Vengeance 32GB DDR5-6000 | Newegg | $129.99 | 1 | $129.99 |

---

## Summary

| | Amount |
|---|--------|
| Subtotal | $728.99 |
| Shipping (estimated) | $15.00 |
| **Total** | **$743.99** |

---

## Notes
- Prices verified on {date}
- Prices subject to change
- Shipping costs may vary

## Vendor Links
- GPU: [Amazon Link](url)
- RAM: [Newegg Link](url)
```

---

## VAT-Compliant Format

```markdown
# Hardware Upgrade Estimate

**Estimate Number:** EST-YYYYMMDD-001
**Date:** YYYY-MM-DD
**Valid Until:** YYYY-MM-DD

---

**Prepared For:**
{Business Name}
{Address if provided}

---

## Line Items

| Item | Description | Vendor | Net Price | VAT ({rate}%) | Gross Price |
|------|-------------|--------|-----------|---------------|-------------|
| GPU | NVIDIA RTX 4070 Super | Amazon | $599.00 | $XX.XX | $XXX.XX |
| RAM | Corsair Vengeance 32GB | Newegg | $129.99 | $XX.XX | $XXX.XX |

---

## Totals

| | Amount |
|---|--------|
| Net Subtotal | $XXX.XX |
| VAT ({rate}%) | $XX.XX |
| Shipping (estimated) | $XX.XX |
| **Gross Total** | **$XXX.XX** |

---

## For Accounting Purposes
- This is an estimate, not an invoice
- VAT amounts shown are estimates based on {rate}% rate
- Actual VAT may vary by vendor and jurisdiction
- Retain vendor invoices for VAT reclaim

## Vendor Information
[Vendor names and order links]
```

---

## Output Location

Save to `/outputs/estimates/YYYY-MM-DD_{description}_estimate.md`

Example: `2024-12-14_workstation-gpu-upgrade_estimate.md`

---

## After Generating Estimate

Offer to:
- Email the estimate (if Resend MCP available)
- Export to different format
- Update with revised components
- Generate comparison estimates for alternatives
