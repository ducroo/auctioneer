---
name: "ricardo-browser-assist"
description: "Operate Ricardo safely and efficiently through a persistent verified browser profile, posting packets, staged photos, and reusable form maps."
---

# Ricardo Browser Assist

Use for Ricardo-specific browser work: posting listings, editing listings, verifying live listing state, and opening buyer-message threads after approval.

Ricardo browser work is intentionally narrow. Strategy, text, pricing, shipping, and photo decisions should happen in local auction files before the browser opens.

## Boundaries

- Use Lucas's persistent Brave auction profile as the default Ricardo browser context.
- Do not use fresh/headless `agent-browser` for public Ricardo browsing; the 2026-06-16 public smoke test reached Cloudflare human verification.
- Do not interact with or attempt to bypass Cloudflare, captcha, or human-verification challenges.
- `agent-browser` may be used for Ricardo only when attached to an already verified, normal auction browser context/profile, or when a dedicated auction profile has been manually verified first.
- Prefer the existing OpenClaw/user browser profile whenever visual verification, login continuity, or Cloudflare state matters.
- Do not bulk-browse Ricardo search results for research.
- Do not publish, edit live listings, or send buyer replies without explicit Lucas approval for the exact action.

## Efficient Posting Pattern

1. Confirm `marketplace-posting` preflight is complete.
2. Confirm a Ricardo posting packet exists, usually `ricardo-posting.md`.
3. Confirm upload images are staged in final order.
4. Check `marketplace-posting/references/ricardo-field-map.md` for the closest known category.
5. Open Ricardo from the persistent Brave context using the normal create-listing path.
6. Fill only from the packet and field map.
7. After each dynamic step, refresh the view/snapshot and continue.
8. Stop at final publish and show the approval summary.
9. Publish only after Lucas writes `Approve publish` for that item.
10. Log the result and any new category/form lessons.

## What A Field Map Means

A field map is a small record of what Ricardo's form asked for in a category: category path, dynamic attributes, values that worked, odd controls, upload quirks, and validation fixes. It is meant to reduce repeated discovery for similar items arriving one by one.

It does not replace judgment. If a field map no longer matches Ricardo's current form, use the current verified browser view and update the learning log afterward.

## Agent Browser Pattern for Verified Sessions

Use `agent-browser` only for deterministic form interaction after the browser context is already trusted/verified.

Core loop:

```bash
agent-browser --session ricardo-posting snapshot -i -c -d 5 --json
agent-browser --session ricardo-posting fill @REF "text from posting packet"
agent-browser --session ricardo-posting upload @REF /path/to/photos_upload/01_main.jpg /path/to/photos_upload/02_detail.jpg
agent-browser --session ricardo-posting wait --load networkidle
agent-browser --session ricardo-posting snapshot -i -c -d 5 --json
```

Use a fresh snapshot before every click/fill/upload step and again after every dynamic form change. Treat `@REF` values as short-lived; refresh after navigation, category changes, uploads, validation errors, and modal dialogs.

## Required Logging

Log important Ricardo browser events in `~/auctioneer/auctions/posting-learning-log.md`:

- item ID
- marketplace action
- duration when known
- result and live URL when published
- failed URL guesses or navigation dead ends
- upload problems and recovery
- dynamic form quirks
- useful category/attribute decisions for the field map
- `blocked_cloudflare_verification` if Ricardo shows human verification

## References

- Public-interface test: `~/auctioneer/auctions/_docs/ricardo-agent-browser-public-test.md`
- API assessment: `~/auctioneer/auctions/_docs/ricardo-api-assessment.md`
