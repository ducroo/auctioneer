---
name: "gmail-mailbox"
description: "Monitor auction Gmail, route pre-sale Ricardo alerts to platform replies, and handle post-sale email drafts with approval."
---

# Gmail Mailbox

Use for reading and normalizing messages from `auctioneer600@gmail.com`, routing pre-sale Ricardo notifications, and creating approved post-sale email drafts.

## Schedule

Recommended monitoring cadence:

- every three hours between 08:00 and 20:00 Europe/Zurich
- one additional check as part of the morning daily report
- no routine overnight checks

The schedule should be implemented separately with cron after Lucas approves the exact times.

## Scope

- fetch and search marketplace emails
- preserve raw source and normalize useful fields locally
- extract listing URL, marketplace, buyer message, and sale state
- reconcile messages to item folders
- before sale: hand the buyer question to `buyer-qa` for a Ricardo-platform response
- after sale: hand pickup or shipping coordination to `buyer-qa` for an email response
- create or update a Gmail draft only after Lucas approves the exact draft
- send only after a separate explicit approval

Do not mark read, archive, label, move, trash, or delete messages unless Lucas explicitly requests that exact action.

## Paths

- Email inbox root: `~/auctioneer/auctions/Email_Inbox`
- New: `~/auctioneer/auctions/Email_Inbox/New`
- Raw: `~/auctioneer/auctions/Email_Inbox/Raw`
- Parsed: `~/auctioneer/auctions/Email_Inbox/Parsed`
- Processed: `~/auctioneer/auctions/Email_Inbox/Processed`
- Unmatched: `~/auctioneer/auctions/Email_Inbox/Unmatched`

## Auth

Use Gmail API OAuth with:

- `https://www.googleapis.com/auth/gmail.readonly`
- `https://www.googleapis.com/auth/gmail.compose`

Keep OAuth files under `~/.openclaw/secrets/` with mode `600`. Never expose or commit them.

## Workflow

1. Authenticate to Gmail.
2. Search recent marketplace emails using `references/search-rules.md`.
3. Save raw source in `Raw/` and normalize it using `references/email-normalization.md`.
4. Reconcile the message to a listing and item folder.
5. Determine whether the item is pre-sale or sold.
6. Route communication by stage.
   - Pre-sale Ricardo question: prepare a response for Ricardo's messaging interface; do not email the buyer.
   - Post-sale pickup/shipping coordination: prepare an email response.
   - Ambiguous sale state or item match: move to `Unmatched/` and ask Lucas.
7. Log the normalized message status.
8. For an approved post-sale email, create a Gmail draft and report the recipient and draft ID.
9. Require a new explicit approval before sending.

## Safety

- Ricardo notification emails are not authorization to answer by email before sale.
- Never send merely because draft creation was approved.
- Never infer a recipient or item when reconciliation is ambiguous.
- Never reveal the full pickup address before confirmed sale/buyer commitment and Lucas's approval.
- Do not expose credentials, tokens, or private buyer data in logs.
