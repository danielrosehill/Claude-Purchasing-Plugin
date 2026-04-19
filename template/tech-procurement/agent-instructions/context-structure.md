# Context Structure

This document defines the contextual information to gather from the user and store in `/context/` to enable effective hardware recommendations.

---

# User Context

Store in: `/context/user-context.md`

## Location

- **Primary location:** Country/region where user lives
- **Secondary locations:** Other countries/regions where user might purchase hardware (business travel, vacations)
- **Shipping considerations:** Any restrictions on delivery addresses

This affects vendor availability, shipping costs, and import duties.

## Preferred Currency

**Critical:** All quotes, estimates, and price comparisons must use the user's preferred currency.

- **Currency code:** (e.g., USD, EUR, GBP, ILS, CAD, AUD)
- **Number format preference:** (e.g., 1,234.56 vs 1.234,56)

Ask this during initial setup and apply consistently throughout all outputs.

## Preferred Vendors

- **Preferred websites:** (e.g., Amazon, Newegg, local retailers)
- **Preferred local shops:** (physical stores the user likes)
- **Vendors to avoid:** (bad experiences, regional unavailability)
- **Account advantages:** (Prime membership, loyalty programs, business accounts)

Prioritize these vendors when sourcing recommendations.

## Purpose & Use Case

Why is the user upgrading? This shapes all recommendations.

- **Primary use:** Gaming, AI/ML, content creation, development, server, etc.
- **Professional vs. recreational:** Affects urgency, tax deductibility
- **Specific workloads:** Particular software, games, or tasks
- **Timeline:** Urgent need vs. can wait for sales

## Brand Preferences

- **Preferred brands:** (positive past experiences)
- **Brands to avoid:** (negative experiences, philosophical objections)
- **Neutral stance:** (no preference for certain categories)

## Idiosyncratic Preferences

Personal preferences that affect recommendations:

- **Noise sensitivity:** Preference for quiet components
- **Aesthetics:** RGB, color schemes, windowed cases
- **Size constraints:** SFF builds, rack mount requirements
- **Power efficiency:** Electricity cost concerns, heat concerns
- **Specific requirements:** Particular ports, features, certifications

---

# Budget Context

Store in: `/context/budget.md`

## Total Budget

- **Amount:** (in user's preferred currency)
- **Type:** Hard limit vs. preferred range
- **Flexibility:** How much overage is acceptable if justified

## Per-Component Limits

Optional limits for specific components:
- GPU budget:
- CPU budget:
- RAM budget:
- Storage budget:
- Other:

## Payment Preferences

- **Single purchase:** Buy everything at once
- **Phased approach:** Spread purchases over time
- **Sale waiting:** Willing to wait for deals

## Value Priorities

What matters more to the user:
- Raw performance vs. price-to-performance
- New vs. previous generation (at discount)
- Premium brands vs. value options

---

# Business Context

Store in: `/context/business.md` (if applicable)

## Business Information

- **Business name:** For formal estimates and quotes
- **Business address:** If needed for formal documents
- **Contact information:** For estimates

## VAT/Tax Requirements

- **VAT registration:** Is the business VAT registered?
- **VAT rate:** Applicable rate for calculations
- **Tax deduction needs:** Are purchases tax-deductible?

## Document Formatting

- **Estimate format:** Standard vs. VAT-compliant
- **Approval workflow:** Internal approval, accountant review, etc.
- **Required fields:** Purchase order numbers, cost centers, etc.

---

# Hardware Context

Store in: `/context/machines/{machine-name}/`

## Documentation per Machine

For each computer being upgraded:

### Required Files

1. **`{machine-name}_spec.json`** - Complete machine-readable specification
2. **`{machine-name}_summary.md`** - Human-readable summary with analysis

### Optional Component Files

Detailed information for specific components:
- `cpu.md`
- `gpu.md`
- `memory.md`
- `storage.md`
- `motherboard.md`
- `psu.md`
- `case.md`
- `cooling.md`

## Gathering Hardware Data

Methods for collecting specifications:
- **Direct access:** Run commands on local machine
- **SSH access:** Connect to network machines
- **User input:** Manual specification entry
- **File import:** Process exports from `/inputs/`

## Required Information

For each component, capture:
- Model/part number
- Specifications
- Current condition
- Age/purchase date (if known)
- Warranty status (if known)

## Expansion Capacity

Critical for upgrade planning:
- **RAM:** Slots used / total slots, max supported
- **Storage:** SATA ports used / total, M.2 slots used / total
- **PCIe:** Slots available, lane allocation
- **Power:** PSU wattage, available connectors

## Date Stamping

**Always record the profile date.** Hardware data becomes stale.

- Verify current date using TIME MCP or user confirmation
- Never assume training data dates are accurate
- Note "Profile Date: YYYY-MM-DD" on all output files

---

# Privacy Considerations

## Potentially Sensitive Data

Before sharing publicly, consider redacting:
- Serial numbers
- MAC addresses
- License keys visible in screenshots
- Account usernames
- Exact addresses
- Private pricing from quotes

## Redaction Options

Offer users:
1. Full redaction (remove entirely)
2. Partial redaction (show only last 4 characters)
3. Placeholder replacement (e.g., "[REDACTED]")

## Shareable Export

If user wants to share workspace publicly:
- Create a sanitized copy
- Review all files for sensitive data
- Exclude `/inputs/` directory (may contain personal screenshots)
- Exclude `/context/business.md` (business details)
