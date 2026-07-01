---
name: "buyer-qa"
description: "Reconcile marketplace buyer questions to local auction items and draft approval-gated replies for Ricardo, email, and other marketplace channels."
---

# Buyer Q&A

Use when a requesting user asks to handle buyer questions, marketplace messages, Ricardo notifications, pickup/shipping follow-up, bid-cancellation replies, or daily Q&A queues.

Buyer communication is approval-gated. Draft exact replies; do not send or post them until the requesting user approves the exact text and channel.

## Paths

- Auction root: `~/auctioneer/auctions`
- Active listings: `~/auctioneer/auctions/Active_Listings`
- Daily Q&A: `~/auctioneer/auctions/Daily_QA`
- Email inbox: `~/auctioneer/auctions/Email_Inbox`

## Workflow

1. Read the normalized message or notification from `Email_Inbox/Processed`, `Daily_QA`, or the item folder.
2. Reconcile the message to an item using listing URL, marketplace item ID, title, buyer name, and local status. Use `references/reconciliation.md` when needed.
3. Classify intent using `references/intent-rules.md`.
4. Read the relevant item files: `item.md`, `listing.md` or `ricardo-posting.md`, `status.txt`, and `qa.md` when present.
5. Draft a concise reply using `references/reply-templates.md`.
6. Apply `references/approval-rules.md`.
7. Write or update the relevant `qa.md` or dated `Daily_QA/YYYY-MM-DD.md` entry with source, buyer, listing, status, proposed reply, and approval note.
8. Present the exact draft to the requesting user for approval.
9. After approval, use the approved channel only.

## Ricardo Browser Rule

- Pre-sale Ricardo buyer questions should be answered on Ricardo, not by email, unless the requesting user explicitly says otherwise.
- Browser automation may help navigate to the Ricardo message thread only after the requesting user approves the exact reply.
- Use the normal verified Ricardo browser context/profile; do not use fresh/headless public `agent-browser` if Ricardo presents Cloudflare or human verification.
- If human verification, captcha, login, or an ambiguous thread appears, stop and report the blocker instead of clicking through.

## Safety

- Never send or post an unapproved reply.
- Never reduce approval friction: approval covers exact text, channel, and send/post action.
- Never reveal the full pickup address before confirmed sale/buyer commitment and requesting user approval.
- Negotiations, pickup times, shipping exceptions, cancellations, and bid removals require requesting user approval.
