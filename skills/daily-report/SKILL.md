---
name: daily-report
description: "Generate a daily auction operations report from local item folders, Q&A queues, email inbox state, sales, pickups, shipping, and stale items."
---

# Daily Report

Use when Lucas asks for a daily overview, morning brief, status report, or operations dashboard.

This skill reads local auction state and writes a dated report. It does not contact buyers, publish listings, lower prices, or move item folders.

## Paths

- Auction root: `~/auctioneer/auctions`
- Output folder: `~/auctioneer/auctions/Daily_Overviews`
- Output file: `YYYY-MM-DD.md`

## Data Sources

Use `references/data-sources.md`.

Read from:

- `Drafts/`
- `Active_Listings/`
- `Sold_To_Ship/`
- `Sold_Pickup/`
- `Daily_QA/`
- `Email_Inbox/`

Per item, inspect available:

- `status.txt`
- `item.md`
- `listing.md`
- `qa.md`
- sales strategy output
- marketplace posting metadata

## Workflow

1. Determine report date in Europe/Zurich.
2. Scan auction folders and collect status.
3. Identify decisions Lucas needs to make.
4. Identify Q&A awaiting approval.
5. Identify packing, shipping, and pickup tasks.
6. Identify stale listings using `references/stale-item-rules.md`.
7. Write the report using `assets/daily-report-template.md`.
8. Save to `Daily_Overviews/YYYY-MM-DD.md`.
9. Optionally summarize the top priorities in chat.

## Rules

- Use factual local state only.
- If marketplace views, bids, or stats are unavailable, write `not checked`.
- Do not infer a sale without explicit local status.
- Do not change prices.
- Do not contact buyers.
- Do not publish listings.
- Do not move folders unless Lucas explicitly asks.
