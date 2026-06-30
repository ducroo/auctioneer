---
name: "item-ingestion"
description: "Ingest auction items, extract facts, obtain strategy approval, and draft searchable Swiss-German listings."
---

# Item Ingestion

Use when Lucas sends item photos, a short item blurb, a box/lot description, or asks to create a draft auction listing.

This skill extracts and organizes item facts. `sales-strategy` decides the proposed platform, packaging, delivery, and pricing, which Lucas must approve before the final listing is drafted.

## Paths

- Auction root: `~/auctioneer/auctions`
- Workspace symlink: `~/.openclaw/workspace-auctioneer/auctions`
- Draft items: `~/auctioneer/auctions/Drafts`

## Workflow

1. Create a unique item ID and draft folder.
   - Use `A0001`, `A0002`, etc. unless Lucas provides an ID.
   - Folder format: `A0001_short_slug`.
   - Never overwrite an existing folder.
2. Save or copy original photos into `photos/` when file paths or attachments are available.
3. Extract visible facts into `item.md`.
   - Separate observed facts, Lucas-provided facts, estimates, and unknowns.
   - Estimate dimensions or weight only when visually plausible and label them as estimates.
4. Run the missing-information check using `references/category-required-fields.md`.
   - Mark each needed field as `known`, `visible_estimate`, `missing_needs_lucas`, or `not_applicable`.
5. Write `questions.md`.
   - Ask only questions that materially affect buyer confidence, pricing, shipping, or posting.
   - Prefer three to five questions maximum.
6. Call `sales-strategy` with the extracted facts and missing-info summary.
7. Present the strategy to Lucas and wait for explicit approval.
   - Do not draft the final marketplace listing while strategy approval is pending.
8. After strategy approval, draft `listing.md` in Swiss-style German using `references/listing-style.md`.
   - Use the approved packaging, marketplace, delivery, and pricing decisions.
   - Include verified search keywords naturally in both the title and description.
   - Title order: brand or maker, item type, important count or size, color or material, and relevant style or era.
   - Use synonyms in the description only where accurate and helpful.
   - Never invent or imply a series, decor, model, maker, age, material, or condition.
   - Avoid keyword stuffing.
   - Put the disclaimer and delivery conditions first.
   - Insert `[BITTE ... EINGEBEN]` placeholders where mandatory facts remain missing.
9. When Ricardo is the approved platform, create `ricardo-posting.md` as the human-readable posting packet.
   - Include title, description, category candidate, sale format, price, shipping/pickup mode, ordered photo paths, and notes for form attributes.
   - Keep unresolved form values explicit with `[BITTE ... EINGEBEN]` placeholders or `needs Lucas` notes.
10. Write `status.txt`.
   - Initial status: `draft_needs_strategy`.
   - After strategy approval and listing/posting-packet creation: `draft_needs_posting_review`.
   - Publication approval remains separate and defaults to `not_approved`.

## Output Files

- `photos/`
- `item.md`
- `listing.md` after strategy approval
- `ricardo-posting.md` when Ricardo is the approved platform or Lucas asks for Ricardo posting
- `questions.md`
- `status.txt`

Use the templates in `assets/` when creating these files. For Ricardo packets, use `assets/ricardo-posting-template.md` as the starting shape.

## Safety

- Do not publish listings.
- Do not message buyers.
- Do not include the full pickup address in listings.
- Do not include a phone number or personal email in public listing text.
- Do not create a final listing before the sales strategy is approved.
