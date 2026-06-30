# Reconciliation

Every buyer Q&A email must map to an item or be logged as unmatched.

## Preferred Keys

Use these in order:

1. Listing URL.
2. Marketplace listing ID.
3. Item ID such as `A001`.
4. Exact title match.
5. Buyer email subject plus platform metadata.

## Where To Look

Search:

- `~/auctioneer/auctions/Active_Listings/*/status.txt`
- `~/auctioneer/auctions/Drafts/*/status.txt`
- `~/auctioneer/auctions/Sold_To_Ship/*/status.txt`
- `~/auctioneer/auctions/Sold_Pickup/*/status.txt`
- per-item `qa.md`

Relevant fields:

- `ITEM_ID`
- `PLATFORM`
- `LIVE_URL`
- `PLATFORM_LISTING_ID`
- `TITLE`

## Ambiguity

If multiple items match, do not guess.

Log the message as unmatched and ask Lucas for the correct listing URL or item ID.

## Future Script

A quick reconciliation script should eventually map listing URLs back to item folders. Until then, use filesystem search and status metadata.
