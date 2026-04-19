# Generate Upgrade Recommendations

You are generating specific component recommendations based on the user's hardware analysis, preferences, and budget.

## Prerequisites

Check that these exist:
- Hardware profile in `/context/machines/`
- User context in `/context/user-context.md`
- Budget in `/context/budget.md`
- Analysis in `/outputs/analysis/` (run `/analyze` if missing)

## Process

### 1. Review Context

Load and consider:
- User's use case and priorities
- Budget constraints (total and per-component)
- Preferred vendors
- Brand preferences/dislikes
- Idiosyncratic preferences (noise, aesthetics, etc.)
- Currency preference

### 2. Research Current Market

For each recommended component:
- Check current pricing from preferred vendors
- Verify availability
- Note any ongoing sales or promotions
- Consider price-to-performance ratio

Use web search/fetch if available, otherwise note that prices should be verified.

### 3. Generate Recommendations

For each upgrade category, provide:

**Primary Recommendation**
- Specific product (brand, model, specifications)
- Current price (in user's preferred currency)
- Why this fits the user's needs
- Compatibility confirmation

**Alternative Option**
- Budget alternative (if applicable)
- Premium alternative (if within budget ceiling)
- Why user might prefer this instead

**What to Avoid**
- Products that don't fit the use case
- Known problematic models
- Bad price-to-performance options

### 4. Prioritize Recommendations

Rank upgrades by:
1. Impact on user's primary use case
2. Cost-effectiveness
3. Ease of implementation
4. Compatibility risk

---

## Output Format

Save to `/outputs/recommendations/YYYY-MM-DD_{machine-name}_recommendations.md`:

```markdown
# Upgrade Recommendations: {Machine Name}

**Generated:** YYYY-MM-DD
**Budget:** {amount in user's currency}
**Use Case:** {primary use case}

## Priority 1: {Component Type}

### Recommended: {Product Name}
- **Price:** {currency} {amount}
- **Vendor:** {preferred vendor}
- **Why:** {rationale}

### Alternative: {Product Name}
- **Price:** {currency} {amount}
- **Why consider:** {rationale}

---

## Priority 2: {Component Type}
[Continue pattern]

---

## Summary

| Priority | Component | Recommended | Price |
|----------|-----------|-------------|-------|
| 1 | GPU | Product X | $XXX |
| 2 | RAM | Product Y | $XXX |

**Total Estimated Cost:** {currency} {amount}
**Budget Remaining:** {currency} {amount}

## Compatibility Notes
[Any important compatibility considerations]

## Next Steps
1. [Suggested order of upgrades]
2. [Any preparation needed]
```

---

## Important Notes

- **Always use user's preferred currency**
- **Stay within budget** - flag if impossible to meet needs within budget
- **Check vendor availability** in user's region
- **Consider the full cost** (don't forget thermal paste, cables, etc.)
- **Note warranty implications** of upgrades

## After Recommendations

Offer to:
- Run `/estimate` to create a formal quote
- Run `/compare` to deep-dive on specific components
- Update recommendations if user provides feedback
