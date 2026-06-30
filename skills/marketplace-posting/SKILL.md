---
name: "marketplace-posting"
description: "Prepare and post marketplace listings from local auction item folders, with Ricardo optimized through posting packets, staged photos, and reusable form maps."
---

# Marketplace Posting

Use when Lucas asks to post, prepare posting, review posting readiness, or update a marketplace listing from an item folder.

This skill turns the already-prepared local auction files into a marketplace form entry. For Ricardo, browser time should be the final mechanical step only: the item facts, text, pricing, shipping, photos, and approval state must be ready before opening the site.

## Paths

- Auction root: `~/auctioneer/auctions`
- Workspace symlink: `~/.openclaw/workspace-auctioneer/auctions`
- Draft items: `~/auctioneer/auctions/Drafts`
- Active listings: `~/auctioneer/auctions/Active_Listings`
- Posting learning log: `~/auctioneer/auctions/posting-learning-log.md`

## Required Local Inputs

Before browser work, inspect the item folder for:

- `item.md`
- `listing.md` or `ricardo-posting.md`
- `strategy.md` when present
- `questions.md`
- `status.txt`
- `photos/`

For Ricardo, prefer `ricardo-posting.md` when present. It is the human-readable posting packet and should already contain the key form values.

## Workflow

1. Run `references/preflight.md`.
2. Normalize the posting packet using `references/posting-packet.md`.
   - If `ricardo-posting.md` exists, reconcile it against `listing.md`, `strategy.md`, and `status.txt`.
   - If only `listing.md` exists, derive the posting packet from the approved strategy and listing.
   - Do not open Ricardo while required packet fields are still unknown unless Lucas explicitly accepts the missing field.
3. Stage upload photos using `references/photo-staging.md`.
   - Keep originals in `photos/` unchanged.
   - Create deterministic upload copies in the item folder, for example `photos_upload/01_main.jpg`.
   - Use direct-child image paths for browser upload when possible, because Ricardo previously rejected nested/non-inbound paths.
4. For Ricardo, delegate browser profile and Cloudflare rules to `ricardo-browser-assist`.
5. Use `references/ricardo-field-map.md` before opening the form.
   - Pick the closest known category/form map.
   - Pre-decide field values and likely dynamic attributes.
   - Mark unknown or guessed fields for Lucas in the final approval summary.
6. Open the marketplace form in the persistent, already verified browser context.
   - For Ricardo, Lucas currently uses persistent Brave; treat that as the default trusted context.
   - Do not use fresh/headless public Ricardo sessions.
7. Fill the form mechanically from the posting packet.
   - Refresh the page snapshot after category changes, dynamic attribute changes, photo upload, validation messages, and navigation.
   - Do not research, rewrite, or decide strategy inside the browser form.
8. Stop before final publish and apply `references/approval-gate.md`.
9. After publication, record the live URL, marketplace item ID when visible, result, duration, errors, and reusable lessons in `posting-learning-log.md`.
10. Update item status according to `references/posting-status.md`.

## Ricardo Efficiency Rules

- The optimized unit is one item, not a batch. Items may arrive one by one.
- The browser session should start only after the posting packet and staged photos are ready.
- The final Ricardo pass should be: open create-listing control, choose category, fill known fields, upload staged photos, resolve validation, pause for approval, publish after approval.
- Capture every recurring category/field decision in `references/ricardo-field-map.md` or the learning log so the next similar item needs fewer exploratory clicks.
- Treat `agent-browser` as optional. It can accelerate deterministic filling only when attached to a verified/logged-in context; the persistent Brave profile remains the default when login continuity or Cloudflare state matters.
- Keep the final publish/edit approval gate unchanged regardless of browser tool.

## Operating Rule

Marketplace automation reduces mechanical browser work, not approval friction. Publishing, editing live listings, and buyer replies still require explicit Lucas approval.
