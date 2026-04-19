---
description: Quick one-off evaluation of a single product against the current spec
argument-hint: <product URL, model name, or pasted listing>
---

# Evaluate a Single Product

Evaluate the product in `$ARGUMENTS` against the current `spec.md` and the latest recommendation.

This is a **quick inline check**, not a full research cycle. Print the verdict in the response; do NOT write a file unless the user asks.

## Steps

1. **Read the spec first, every time:**
   - `spec.md` — must-haves, hard nos, nice-to-haves, per-purchase overrides, standing preferences snapshot
   - The most recent file in `from-ai/recommendations/` (current top pick, for comparison) if one exists

   Never skip this. A spec change since the last recommendation can invalidate otherwise-fine products.

2. **Resolve the product.** `$ARGUMENTS` may be:
   - A URL → fetch with WebFetch and extract model, price, key specs, seller
   - A model name only → look up specs from the manufacturer site (prefer brand's own site over retailers)
   - A pasted listing → parse directly

   If a critical spec is missing, fetch it. Do not guess specs.

3. **Score against each criterion** — mark **PASS / FAIL / PARTIAL** with a one-line reason:
   - Each must-have from `spec.md`
   - Each hard no (per-purchase AND standing avoided brands)
   - Markup vs the effective threshold (per-purchase override > standing default)

4. **Compare against the current top pick** from the latest recommendations file. Is this better, worse, or sideways? Be specific about *why*.

5. **Verdict** — end with one of:
   - ✅ **Buy** — clearly better than current top pick for the spec
   - 🟡 **Consider** — viable alternative, trade-offs worth thinking about
   - ⚪ **Sideways** — equivalent to current pick, no reason to switch
   - ❌ **Skip** — fails the spec or strictly worse

6. **Honesty rules:**
   - If the spec rules it out, say so plainly.
   - If you can't verify a key spec, say "unverified" rather than guessing.
   - A technically-compliant product that fails the spec's context or priorities is still a Skip.

## Output

Print inline. Only write a file if the user explicitly asks.
