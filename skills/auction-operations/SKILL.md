---
name: "auction-operations"
description: "Coordinate local auction item lifecycle, specialist skills, marketplace posting, buyer communication, and reports."
---

# Auction Operations

Use when a requesting user asks for overall auction work, item status, posting coordination, buyer-message handling, sales follow-up, or operational decisions across the local auction workspace.

Delegate specialist work to `item-ingestion`, `sales-strategy`, `marketplace-posting`, `ricardo-browser-assist`, `gmail-mailbox`, `buyer-qa`, and `daily-report`.

## Paths

- Auction root: `~/auctioneer/auctions`
- Workspace symlink: `~/.openclaw/workspace-auctioneer/auctions`
- Posting learning log: `~/auctioneer/auctions/posting-learning-log.md`
- Ingestion learning log: `~/auctioneer/auctions/ingestion-learning-log.md`

## Lifecycle

1. Ingest item facts and photos with `item-ingestion`. Treat Telegram/OpenClaw chatbot uploads as the normal inbound path when present.
2. Decide marketplace, pricing, packaging, and delivery with `sales-strategy`.
3. For price/category research, follow `sales-strategy` browser rules: avoid fresh/headless public Ricardo browsing; eBay research/browser use is allowed as a market signal when relevant.
4. Draft local listing files and resolve only material missing facts. Do not stall on nice-to-have details.
5. Obtain requesting user approval for strategy/listing where required.
6. Prepare posting with `marketplace-posting`, including category playbook selection and upload photo staging.
7. For Ricardo, use `ricardo-browser-assist` and the persistent verified Brave profile by default.
8. Stop before publish and require the item-specific approval gate.
9. After publication, update status and record live URL/lessons.
10. Reconcile incoming email with `gmail-mailbox`.
11. For buyer questions, use `buyer-qa`; browser automation may open the relevant Ricardo thread only after the requesting user approves the exact reply.
12. Generate daily summaries with `daily-report` when requested.

## Browser Tool Routing

Marketplace browser automation is routed by risk:

- strategy research: `sales-strategy`
- Ricardo posting/form work: `ricardo-browser-assist` plus `marketplace-posting`
- Ricardo buyer replies: `buyer-qa` after exact reply approval
- eBay public research: `sales-strategy`; seller writes require separate approval/tooling

For Ricardo, browser automation is allowed only as a form accelerator after the browser context is verified/logged in. Do not use automation for strategy, price research, exploratory public browsing, login recovery, Cloudflare, captcha, or human-verification checks. If verification appears, stop and report the blocker.

## Priority Category Playbooks

Build and reuse field maps first for the categories expected most often:

- dinnerware / porcelain services
- pictures / art / framed decor
- carpets / rugs
- furniture, especially closets and storage furniture
- clothes and wearable bundles

When a requested item falls in one of these categories, prefer the existing playbook and update it after posting rather than rediscovering the Ricardo form from scratch.

## Operating Rules

- Keep item decisions in local files before opening marketplace forms.
- Treat `ricardo-posting.md` as the current human-readable posting packet when present.
- Items may arrive one by one; do not require batches.
- Never publish, edit live listings, close listings, lower prices, or message buyers without explicit requesting user approval for that action.
- Do not include full pickup address, phone number, or personal email in public listing text.
- Record reusable ingestion lessons in `ingestion-learning-log.md` when intake, missing facts, photos, category choice, or strategy work creates friction.
- Record reusable marketplace/browser lessons in `posting-learning-log.md` so later one-by-one postings become faster.
