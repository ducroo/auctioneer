# Posting Status

Update `status.txt` after publishing.

Required fields:

```text
STATUS=active_listing
APPROVAL=approved
PLATFORM=
LIVE_URL=
POSTED_AT=
PRICE=
SHIPPING=
ITEM_FOLDER=
```

Append rather than erase useful prior history.

Move the item folder:

```text
~/auctioneer/auctions/Drafts/<item>
```

to:

```text
~/auctioneer/auctions/Active_Listings/<item>
```

If publishing fails after a draft was created on a marketplace, record:

```text
STATUS=posting_interrupted
PLATFORM_DRAFT_URL=
LAST_ERROR=
UPDATED_AT=
```
