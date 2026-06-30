---
name: "auction-operations"
description: "Coordinate local auction item lifecycle, specialist skills, marketplace posting, buyer communication, and reports."
---

# Auction Operations

Use when Lucas asks for overall auction work, item status, posting coordination, buyer-message handling, sales follow-up, or operational decisions across the local auction workspace.

Delegate specialist work to `item-ingestion`, `sales-strategy`, `marketplace-posting`, `ricardo-browser-assist`, `gmail-mailbox`, `buyer-qa`, and `daily-report`.

## Paths

- Auction root: `~/auctioneer/auctions`
- Workspace symlink: `~/.openclaw/workspace-auctioneer/auctions`
- Posting learning log: `~/auctioneer/auctions/posting-learning-log.md`

## Lifecycle

1. Ingest item facts and photos with `item-ingestion`.
2. Decide marketplace, pricing, packaging, and delivery with `sales-strategy`.
3. For price/category research, follow `sales-strategy` browser rules: avoid fresh/headless public Ricardo browsing; eBay research/browser use is allowed as a market signal when relevant.
4. Draft local listing files and resolve material missing facts.
5. Obtain Lucas approval for strategy/listing where required.
6. Prepare posting with `marketplace-posting`.
7. For Ricardo, use `ricardo-browser-assist` and the persistent verified Brave profile by default.
8. Stop before publish and require the item-specific approval gate.
9. After publication, update status and record live URL/lessons.
10. Reconcile incoming email with `gmail-mailbox`.
11. For buyer questions, use `buyer-qa`; browser automation may open the relevant Ricardo thread only after Lucas approves the exact reply.
12. Generate daily summaries with `daily-report` when requested.

## Browser Tool Routing

Marketplace browser automation is routed by risk:

- strategy research: `sales-strategy`
- Ricardo posting/form work: `ricardo-browser-assist` plus `marketplace-posting`
- Ricardo buyer replies: `buyer-qa` after exact reply approval
- eBay public research: `sales-strategy`; seller writes require separate approval/tooling

For Ricardo, browser automation is allowed as a form accelerator only after the browser context is verified/logged in. Do not use automation to bypass public Ricardo Cloudflare/human checks.

## Operating Rules

- Keep item decisions in local files before opening marketplace forms.
- Treat `ricardo-posting.md` as the current human-readable posting packet when present.
- Items may arrive one by one; do not require batches.
- Never publish, edit live listings, close listings, lower prices, or message buyers without explicit Lucas approval for that action.
- Do not include full pickup address, phone number, or personal email in public listing text.
- Record reusable marketplace lessons so later one-by-one postings become faster.
