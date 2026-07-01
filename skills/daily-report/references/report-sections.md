# Report Sections

Use these sections in order.

## Today's Priorities

Short checklist of decisions and tasks the requesting user should care about today.

Include:

- draft approvals
- posting approvals
- Q&A approvals
- pickup/shipping actions
- stale listings needing decisions

## Listings

Subsections:

- Drafts awaiting requesting user.
- Approved, not posted.
- Active listings.

For active listings, include:

- item ID
- platform
- title
- URL
- price
- listing age if known
- stats if locally available, otherwise `not checked`

## Buyer Q&A Awaiting Approval

Summarize entries from `Daily_QA/` and per-item `qa.md` with status `awaiting_approval`.

Include:

- item ID
- platform
- buyer
- question summary
- proposed reply summary
- action: Approve / Edit / Discard

## Sales And Fulfillment

Subsections:

- Sold, needs shipping.
- Sold, pickup.

Include buyer/payment/address status only if locally stored.

## Stale / Needs Action

Use `stale-item-rules.md`.

## Notes

Short factual notes, gaps, and warnings.


## Ingestion Process Lessons

Include only recent or high-impact ingestion lessons from `ingestion-learning-log.md` when they affect current workflow, missing-information patterns, or category checklist updates. Keep this brief; daily reports should surface operational changes, not duplicate the full log.
