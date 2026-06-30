# Data Sources

Scan the auction root:

```text
~/auctioneer/auctions/
```

## Folders

- `Drafts/`: item folders not yet active.
- `Active_Listings/`: posted listings.
- `Sold_To_Ship/`: sold items needing shipping.
- `Sold_Pickup/`: sold items for pickup.
- `Daily_QA/`: buyer replies awaiting approval.
- `Email_Inbox/`: normalized Gmail input state.
- `Daily_Overviews/`: previous reports.

## Per-Item Files

Read when present:

- `status.txt`: operational state, platform, price, URL, shipping.
- `item.md`: item facts and missing information.
- `listing.md`: listing draft/public text.
- `qa.md`: per-item buyer questions and proposed replies.
- strategy files or sales strategy section in `item.md`.

## Missing Files

If a folder is missing expected files, report it as an action item instead of failing.

Examples:

- missing `status.txt`
- missing photos
- listing has placeholders
- active listing lacks `LIVE_URL`
