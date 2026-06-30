---
name: "sales-strategy"
description: "Separate Ricardo and eBay browser research rules."
---

# Proposed Update: Browser Research Rules

Update the existing `sales-strategy` skill with explicit browser/research boundaries.

## Change to `SKILL.md`

In the research workflow, add:

```markdown
- Ricardo research: do not use fresh/headless `agent-browser` against public Ricardo pages for price research. If Ricardo context is needed, use known item URLs, our own listings, normal browser profile checks, or the official API once available. Do not bulk-browse Ricardo search results.
- eBay research: use eBay browser/API research as an optional signal for specialist, rare, lightweight, collectible, model-specific, or internationally traded items, especially when Swiss comps are weak.
- Treat eBay prices as a signal, not a direct Swiss listing price; adjust for marketplace, shipping burden, fees, dispute risk, and local pickup friction.
```

In output, add when browser/eBay research was used:

```markdown
- research sources used: Ricardo normal-profile/API/known listing only, eBay research/browser signal, or none
- eBay research signal: relevant categories/keywords/comps, confidence, and Swiss-market adjustment
```

## Change to `references/platform-rules.md`

Under `## Ricardo`, add:

```markdown
Research boundary:

- Do not run fresh/headless public `agent-browser` sessions against Ricardo search for price research.
- Use Ricardo mainly through official API when available, normal verified browser context for our own account/listings, or known public listing checks that do not trigger bulk access.
```

Under `## eBay`, add:

```markdown
Research use:

- eBay browser/API research is allowed for specialist price/category/keyword discovery.
- Prefer sold/completed signals when available; active asking prices are weaker evidence.
- Use eBay keywords/categories to improve Ricardo titles when the item remains Swiss-market-first.
```

## Operating Rule

Use browser research asymmetrically: be conservative with Ricardo because of Cloudflare/platform sensitivity; use eBay research more freely for public market signals, still without credentialed seller actions unless separately approved.
