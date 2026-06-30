# Posting Preflight

Before opening a marketplace, verify:

- Item folder exists.
- `photos/` contains usable images.
- `listing.md` exists.
- Disclaimer appears at the top of `listing.md`.
- Public listing text contains no full pickup address.
- Public listing text contains no phone number or personal email.
- Platform is selected by `sales-strategy` or Lucas.
- Price / start price is selected.
- Shipping mode is selected.
- Missing placeholders such as `[BITTE ... EINGEBEN]` are resolved or explicitly accepted by Lucas.
- Approval is present for this item.

Stop and ask Lucas if any of these fail.

## Approval State

Proceed only if either:

- `status.txt` has `APPROVAL=approved` and `STATUS=approved_for_posting`
- Lucas explicitly approves posting this item in the current conversation

Do not infer approval from prior general permission.

## Ricardo Browser Readiness

Before opening Ricardo, also verify:

- `ricardo-posting.md` exists or the Ricardo packet can be derived completely from approved local files.
- Ordered upload photos are staged or the original `photos/` paths are simple enough to upload reliably.
- Category and required attributes have been checked against `references/ricardo-field-map.md`.
- Browser context is the persistent verified auction profile, currently Lucas's Brave setup, or another manually verified context.
- No public/headless Ricardo research is needed for the posting decision.

If Cloudflare/human verification appears, stop automation and request normal browser/manual verification. Do not attempt to solve or bypass it.
