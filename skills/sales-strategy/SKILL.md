---
name: "sales-strategy"
description: "Choose auction marketplace, research depth, price, packaging, and delivery strategy for local estate-clearance items, with Ricardo/eBay browser boundaries."
---

# Sales Strategy

Use when a requesting user asks for a price, platform choice, sale strategy, research depth, shipping/pickup decision, or approval-ready strategy for an auction item.

This skill turns `item.md`, photos, and missing-information notes into a practical selling recommendation. Prefer speed and clear uncertainty over over-researching ordinary household items.

## Paths

- Auction root: `~/auctioneer/auctions`
- Draft items: `~/auctioneer/auctions/Drafts`
- Strategy template: `assets/strategy-template.md`

## Workflow

1. Read the item folder inputs: `item.md`, photos when needed, `questions.md`, and any price/platform preference from the requesting user or item source.
2. Pick research depth using `references/research-depth.md`.
3. Choose platform using `references/platform-rules.md`.
4. Choose pickup/shipping using `references/shipping-rules.md` and packaging using `references/packaging-rules.md`.
5. Price using `references/pricing-rules.md`.
6. For the expected main categories, keep the recommendation practical and playbook-ready:
   - dinnerware: count, maker/series, chips/cracks, pickup risk drive value.
   - pictures/art: signature/provenance and dimensions drive research depth.
   - carpets/rugs: dimensions, condition, smell/stains, material/origin if known.
   - furniture/closets: dimensions, disassembly, condition, pickup friction.
   - clothes: brand, size, condition, bundle logic, Vinted fit before Ricardo.
7. Write or update `strategy.md` with platform, price, format, shipping, research sources used, assumptions, and approval status.
8. If strategy approval is needed, present the concise recommendation and wait for the requesting user before final listing/posting.

## Browser Research Rules

- Ricardo research: do not use fresh/headless `agent-browser` against public Ricardo pages for price research. If Ricardo context is needed, use known item URLs, our own listings, normal verified browser profile checks, or the official API once available. Do not bulk-browse Ricardo search results.
- eBay research: allowed as an optional signal for specialist, rare, lightweight, collectible, model-specific, or internationally traded items, especially when Swiss comps are weak.
- Treat eBay prices as a signal, not a direct Swiss listing price; adjust for marketplace, shipping burden, fees, dispute risk, and local pickup friction.
- Do not let browser research delay ordinary local pickup items unless likely value or mispricing risk justifies it.

## Output Requirements

Include:

- recommended platform and backup platform
- sale format and starting/fixed price
- pickup/shipping recommendation
- packaging recommendation
- research depth and sources used: Ricardo normal-profile/API/known listing only, eBay signal, other web/source, or none
- confidence level and key assumptions
- material questions that block posting, if any

## Safety

- Never publish, edit, close, relist, or lower prices without requesting user approval.
- Never use Ricardo browser automation to bypass Cloudflare, captcha, login, or human verification.
- Never invent provenance, maker, artist, age, material, or condition to improve price.
