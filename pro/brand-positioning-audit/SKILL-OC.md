---
name: brand-positioning-audit
version: "3.1.0"
updated: 2026-03-19
platform: openclaw
description: "Diagnose why brand messaging isn't working. Scores 6 dimensions, finds root failure, delivers rewrite-level copy fixes. NOT for: writing copy from scratch or voice/tone issues."
---

# Brand Positioning Audit — OpenClaw

Most brands have a positioning problem, not a messaging problem. This audit finds the root cause across 6 dimensions and gives you actual copy — not direction.

## Inputs (one message)
1. Brand URL (homepage + about page)
2. Who you sell to (specific ICP)
3. Top 2-3 competitors (optional)
4. What frustrates you about current positioning? (optional)

No URL? Paste homepage copy + about page copy directly.

## 6 Dimensions (score 1-10, quote evidence)

| Dimension | What to Score | Weight |
|-----------|--------------|--------|
| ICP Clarity | Can someone tell if they're the target? | 1× |
| Value Clarity | Concrete outcome stated? | 1× |
| Differentiation | Could a competitor say this? | **1.5×** |
| Proof Credibility | Claims earned or asserted? | 1× |
| Message-Market Fit | ICP's words or company's words? | 1× |
| Competitive Separation | Clear reason to choose this? | 1× |

## Root Failure Types
- **Clarity** — Can't tell what this is or who it's for
- **Audience** — ICP too broad, messaging aimed at no one
- **Differentiation** — Position real but not owned, competitors say the same thing
- **Proof** — Claims not earned, positioning needs proof that doesn't exist
- **Language** — Insight is right but expressed in inside-out language

## Anti-Patterns
❌ Aspirational Position — "We're the Stripe of X" sets unmet expectations
❌ Feature Parade — 8 bullet points on homepage = no positioning
❌ Category Creator Trap — inventing categories nobody searches for
❌ Everyone Welcome Mat — "all sizes, all industries" = indecisive
❌ Vague Differentiator — "we focus on simplicity" (so does everyone)
❌ Proof Dodge — "trusted by leading companies" with no names

## Output Format
```
# Brand Positioning Audit — [Brand]

## Scorecard
| Dimension | Score | Evidence |
|-----------|-------|----------|
[6 rows with verbatim quotes]

## Root Diagnosis: [type] — [why]

## Priority Fixes (3, root failure first)

## Rewrite Pack
Option A (Benefit-forward): Hero | Sub | CTA
Option B (ICP-specific): Hero | Sub | CTA
Option C (Differentiation-led): Hero | Sub | CTA
```

Generate three GENUINELY different strategies (not word swaps). Decide frames before generating.

## Gotchas
- A/B test pages → confirm hero copy is canonical before scoring
- Wrong ICP → ask about churned customers, not ideal ones
- Self-generated rewrites converge → pick 3 frames independently before writing

## After Audit: Offer A) more headline options B) competitor benchmark C) decision mode D) done
