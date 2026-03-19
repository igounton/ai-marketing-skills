---
name: brand-positioning-audit
version: "3.1.0"
updated: 2026-03-19
changelog: "v3.1 — Vibe Skill Creator rebuild: expert voice, real examples, anti-patterns, flattened structure"
price: "$9"
author: "@BrianRWagner"
platform: claude-code
slug: "brw-brand-positioning-audit"
description: "Use when: user wants to diagnose why their brand messaging isn't working, score their positioning, understand their root failure, or get rewrite-level copy fixes. Triggers: 'audit my brand positioning', 'why isn't my messaging working', 'score my homepage', 'brand positioning diagnosis'. NOT for: writing copy from scratch (use copywriting), auditing content strategy, or voice/tone issues (use brand-voice-extractor)."
---

> **Works with Claude Code, Cursor, GitHub Copilot, and any AI that accepts markdown instructions.**

**Pre-flight script:** `node scripts/audit-prep.mjs <brand_url> [competitor_url]` — fetches and structures page copy before scoring.
**References:** `references/examples.md` — complete audit example, before/after for each root failure type.

---

# Brand Positioning Audit

Most brands don't have a messaging problem. They have a positioning problem — and bad messaging is the symptom.

"We help teams work better together" is not a positioning. Neither is "The leading platform for [category]." These sound like something, but they say nothing. They don't tell your ICP why you're the obvious choice. They don't separate you from the 47 competitors saying the same thing.

This audit finds the root failure in 6 dimensions, then gives you actual copy you can use — not "consider refining your messaging."

---

## Why Positioning Audits Usually Fail

**They score everything equally.** A brand with perfect ICP clarity but zero differentiation gets a 7/10 average score and leaves thinking "not bad!" Meanwhile, their positioning is functionally identical to every competitor.

**They give direction, not copy.** "Strengthen your value proposition" is not advice. "Replace 'We help businesses grow' with 'Double your demo pipeline in 90 days without adding headcount'" is advice.

**They miss the root cause.** Brands have one root failure that causes all the symptoms. Fix the root and everything improves. Fix the symptoms and nothing improves.

---

## ⚠️ Gotchas

**URL-only input might fetch a test variant.** If they're A/B testing, show the hero headline verbatim and ask: "Is this your current hero copy?"

**Self-generated rewrites converge.** When you write Options A/B/C, they tend to collapse into variations of the same angle. Fix: Decide the three frames BEFORE generating — Benefit-forward, ICP-specific, Differentiation-led — then generate each independently.

**Wrong ICP means wrong audit.** If they say "we sell to SMBs" but actually close mid-market, every score is miscalibrated. Ask: "Tell me about a customer who churned in 90 days. Who were they?" ICP clarity comes from failure cases, not ideal ones.

---

## How to Run the Audit

**Get these inputs in one message (no back-and-forth):**

```
1. Brand URL (homepage + about page if possible)
2. Who you sell to — be specific ("B2B founders doing $1-10M" not "businesses")
3. Top 2-3 competitors (optional but improves the audit significantly)
4. What frustrates you about current positioning? (optional — helps focus)
```

If no URL: ask them to paste homepage copy and about page copy directly. Don't audit descriptions — audit actual messaging.

---

## The 6 Dimensions

Score each 1-10. Quote exact copy as evidence for every score.

### 1. ICP Clarity
Can someone read this and immediately know if they're the target customer?

**10:** "For solo consultant-founders doing their own marketing" — specific enough to name 5 real people who fit.
**5:** "For marketers" — which marketers? Doing what? At what stage?
**1:** "For teams everywhere" — meaningless.

### 2. Value Clarity
Is the primary value stated in concrete, outcome terms?

**10:** "Cut your response time in half by routing support tickets automatically" — specific outcome + mechanism.
**5:** "Streamline your workflow" — category, not value.
**1:** "The better way to work" — empty.

### 3. Differentiation (Weight 1.5×)
Could a competitor say this exact thing? If yes, it's not differentiation.

This is the most important dimension and the most commonly failed. Weight it 1.5× in the overall score.

**10:** Position is so specific a competitor would need to change their business to claim it.
**5:** Differentiation angle exists but any competitor could claim it with a messaging tweak.
**1:** Interchangeable with every competitor.

### 4. Proof Credibility
Are claims earned or asserted?

**10:** "Helped 4,200 DTC brands average 23% higher ROAS" — specific, verifiable.
**5:** "Thousands of happy customers" — vague.
**1:** Pure assertion with nothing to back it up.

### 5. Message-Market Fit
Does the language match how the ICP talks about the problem — or how the company talks about itself?

**10:** Uses the ICP's exact words, pain points, and framing.
**5:** Close, but noticeable inside-out language (features, capabilities, platform).
**1:** Entirely internal jargon. Sounds like how founders describe the product, not how customers describe the problem.

### 6. Competitive Separation
Is there a clear reason to choose this over alternatives?

**10:** Creates a comparison frame where competitors' approaches look wrong for the right buyer.
**5:** "Better/faster/cheaper" without explaining why.
**1:** No competitive framing at all.

---

## Root Failure Types

After scoring all 6, identify THE root failure — one thing that's causing the others:

- **Clarity failure** — Can't tell what this is or who it's for. Everything else is downstream.
- **Audience failure** — ICP is too broad. All messaging is aimed at no one in particular.
- **Differentiation failure** — Position is real but not owned. Competitors say the same thing.
- **Proof failure** — Claims aren't earned. Positioning requires proof that doesn't exist yet.
- **Language failure** — Positioning insight is right but expressed in inside-out language. Rewrites will fix it.

State it clearly: "The root failure is [type] — [one sentence on why]."

---

## Anti-Patterns (What Fails Every Time)

❌ **The Aspirational Position.** "We're the Stripe of [category]." You're not. Positioning by analogy to a $100B company sets expectations you can't meet and says nothing about what you actually do.

❌ **The Feature Parade.** Listing every feature on the homepage instead of stating one clear outcome. If the first screen has 8 bullet points, you don't have positioning — you have a spec sheet.

❌ **The Category Creator Trap.** Inventing a new category ("we're an AI-powered revenue enablement platform") when you haven't earned category creation. If nobody Googles your category, it doesn't exist yet.

❌ **The Everyone Welcome Mat.** "For teams of all sizes, across all industries." This isn't inclusive — it's indecisive. Great positioning alienates people who aren't the right fit. That's a feature, not a bug.

❌ **The Vague Differentiator.** "We're different because we focus on simplicity." So does every competitor. Real differentiation is specific enough that a competitor would have to change their product to claim it.

❌ **The Proof Dodge.** "Trusted by leading companies" with no logos, no names, no numbers. If you can't name them, the proof isn't proof.

---

## Before/After: Real Positioning Rewrites

### Example: Vague SaaS Homepage

**Before:**
> **Hero:** "The smarter way to manage your business"
> **Sub:** "Our comprehensive platform helps teams work more efficiently with AI-powered insights."

**Root failure:** Clarity — can't tell what this is, who it's for, or what it does.

**After (Option A — Benefit-forward):**
> **Hero:** "Get 4 hours back every week"
> **Sub:** "Automate the admin work that's eating your day — invoicing, scheduling, follow-ups. Built for solo consultants."

**After (Option B — ICP-specific):**
> **Hero:** "Built for solo consultants who hate admin"
> **Sub:** "One place for invoicing, scheduling, and client follow-ups. Stop toggling between 6 tabs."

**After (Option C — Differentiation-led):**
> **Hero:** "Your clients think you have an assistant. You don't."
> **Sub:** "Automatic invoicing, smart scheduling, and follow-up sequences that run while you do the real work."

**Why these are different:** A leads with outcome, B leads with who it's for, C leads with the owned position. Each is a genuinely different strategy, not a word swap.

---

## Output Format

```markdown
# Brand Positioning Audit — [Brand Name]
*Audited: [Date]*

## Scorecard

| Dimension | Score | Evidence |
|-----------|-------|----------|
| ICP Clarity | [X] | [quote from site + one-line assessment] |
| Value Clarity | [X] | [quote + assessment] |
| Differentiation (1.5×) | [X] | [quote + assessment] |
| Proof Credibility | [X] | [quote + assessment] |
| Message-Market Fit | [X] | [quote + assessment] |
| Competitive Separation | [X] | [quote + assessment] |
| **Overall (weighted)** | **[X]** | |

## Root Diagnosis

**Root failure: [type]**

[2-3 sentences: what's broken, why fixing other dimensions won't matter until this is resolved]

## Current Messaging (verbatim)

Hero: "[exact headline]"
Sub: "[exact subheadline]"
CTA: "[exact CTA text]"

## Priority Fixes

**Fix 1 (root failure):** [Specific action with reasoning]
**Fix 2:** [Specific action]
**Fix 3:** [Specific action]

## Rewrite Pack (ready to use)

**Option A — Benefit-forward:**
Hero: [rewrite] | Sub: [rewrite] | CTA: [rewrite]

**Option B — ICP-specific:**
Hero: [rewrite] | Sub: [rewrite] | CTA: [rewrite]

**Option C — Differentiation-led:**
Hero: [rewrite] | Sub: [rewrite] | CTA: [rewrite]
```

---

## After the Audit

End with:

```
Your positioning audit for [Brand]. Overall: [X]/10 | Root failure: [type]

What's next?
A) More headline options — 5 variations on the strongest positioning angle
B) Competitor benchmark — same scorecard on a competitor, side-by-side comparison
C) Decision mode — evaluating two positioning directions against the scorecard
D) Done — take the rewrites and implement
```

---

## Quality Checklist

- [ ] Every score backed by verbatim copy from the site (not gut feel)
- [ ] Root failure is ONE thing, not a list
- [ ] Rewrite options are genuinely different strategies (not word swaps)
- [ ] Rewrites use specific, concrete language (no "streamline" or "optimize")
- [ ] Differentiation weighted 1.5× in overall score

---

*Brand Positioning Audit v3.1.0 — Part of the AI Marketing Skills library by Brian Wagner (@BrianRWagner)*
*Works with: Claude Code, Cursor, GitHub Copilot, VS Code Copilot, ChatGPT, Claude.ai*
