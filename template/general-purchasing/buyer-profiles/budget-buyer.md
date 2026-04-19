# Budget Buyer

*Best value for money inside a tight budget. Accepts trade-offs on prestige, polish, and feature depth in exchange for the lowest cost that still meets the must-haves.*

## Core stance

- **Price-per-capability is the metric.** Not the cheapest product — the cheapest product that clears the must-haves.
- **Brand prestige is not worth paying for.** Same OEM, unbadged, at 40% off = the right answer.
- **"Good enough" is the goal.** Over-spec is waste.
- **Refurb, open-box, last-gen, and off-brand are all fair game** if the reviews support them.

## Priorities (ordered)

1. Meeting all must-haves at minimum spend
2. Value vs RRP — including last-gen and refurb channels
3. Reliability *sufficient for the expected usage window* (not lifetime — just until next upgrade cycle)
4. Warranty — as a hedge, not as a feature
5. Manufacturer reputation — only as a tie-breaker between equally-priced options
6. Aesthetics / prestige — ignored

## Preferred signals

- Last-generation models at clearance pricing (still supported, just superseded)
- Manufacturer-refurbished with warranty
- OEM-made products sold under multiple brand names (identify the cheapest badge)
- Honest "no-frills" brand positioning — Xiaomi sub-brands, house brands from serious retailers
- High review-count with stable 4.0+ rating (mass-market validation)
- Open-box / returned stock from reputable sellers
- Products one tier below the category leader with 90% of the capability for 50% of the price

## Red flags

- Sub-€10 / sub-$10 "bargain" products in categories where floor pricing signals counterfeit or safety issues (electrical goods, PPE, batteries, chargers)
- No-brand products with no review history, regardless of price
- Grey-market imports with no regional warranty (saves 20%, costs 100% on failure)
- Subscription-locked features that push true cost above the mid-range alternative
- Shipping / VAT / customs that erase the headline discount (import realism — let `price-comparison` sub-agent check)
- "Cheap now, expensive later" — e.g. printer with cheap body + extortionate ink

## Weight adjustments (evaluation axes)

| Axis | Multiplier |
|------|-----------|
| Value vs RRP | ×2.5 |
| Price-per-must-have | ×2.0 |
| Total cost incl. consumables | ×1.5 |
| Warranty | ×1.2 |
| Reliability (short/medium-term) | ×1.0 |
| Manufacturer reputation | ×0.7 |
| Feature depth | ×0.6 |
| Build quality | ×0.6 |
| Aesthetics | ×0.3 |
| Prestige | ×0.0 |

## Typical-archetype brands

- Tech: Xiaomi, Redmi, Anker (budget line), TCL, Hisense
- Tools: Ryobi, Parkside (Lidl), AmazonBasics for non-critical
- Kitchen: Ikea kitchenware, supermarket house brands
- Furniture: Ikea, flat-pack generics

## Typical anti-archetypes

- Luxury / lifestyle brands (anything marketed on heritage or logo)
- "Prosumer" products where the spec bump doesn't match the price bump
- First-party ecosystem accessories where a third-party equivalent exists

## Combines well with

- **`reliability-buyer`** — "cheap, boring, works". Excellent default for most utilitarian purchases.
- **`minimalist`** — fewer features = lower price by construction.
- **`bifl-buyer`** — tension, but see "Conflicts with". A "cheapest BIFL-grade option" pick is legitimate and often very strong.

## Conflicts with

- **`premium-aesthete`** — direct contradiction.
- **`feature-maximiser`** — pulls in opposite directions; the combination forces explicit prioritisation.
- **`early-adopter`** — new releases carry the new-release premium.

## When NOT to apply this profile

- Safety-critical goods (child seats, helmets, climbing gear, electrical work). Budget pressure on safety items is false economy.
- Products used daily for work where downtime has real cost.
- Gifts and anything where perceived value matters (this is the Aesthete's domain).
