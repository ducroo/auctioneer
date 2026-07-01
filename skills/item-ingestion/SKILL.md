---
name: "item-ingestion"
description: "Ingest auction items, extract facts, obtain strategy approval, and draft searchable Swiss-German listings."
---

# Item Ingestion

Use when a requesting user or item source sends item photos, a short item blurb, a box/lot description, a Telegram/OpenClaw chatbot upload, or asks to create a draft auction listing.

This skill extracts and organizes item facts. `sales-strategy` decides the proposed platform, packaging, delivery, and pricing, which the requesting user must approve before the final listing is drafted.

## Telegram/OpenClaw Inbound Mode

When item material arrives through Telegram to OpenClaw, treat the chatbot message plus uploaded media as the intake packet. Preserve the source wording, copy available media into `photos/`, and separate facts into: visible from photos, provided by the requesting user, item source, or chat, estimates, and unknowns.

Do not ask the requesting user to reformat the intake if the packet already contains enough to proceed. Ask only for missing details that materially affect buyer confidence, price, shipping, or safe posting.

## Paths

- Auction root: `~/auctioneer/auctions`
- Workspace symlink: `~/.openclaw/workspace-auctioneer/auctions`
- Draft items: `~/auctioneer/auctions/Drafts`
- Ingestion learning log: `~/auctioneer/auctions/ingestion-learning-log.md`

## Workflow

1. Create a unique item ID and draft folder.
   - Use `A0001`, `A0002`, etc. unless the requesting user provides an ID.
   - Folder format: `A0001_short_slug`.
   - Never overwrite an existing folder.
2. Save or copy original photos into `photos/` when file paths or attachments are available.
3. Extract visible facts into `item.md`.
   - Separate observed facts, facts provided by the requesting user or item source, estimates, and unknowns.
   - Estimate dimensions or weight only when visually plausible and label them as estimates.
4. Run the missing-information check using `references/category-required-fields.md`.
   - Prioritize the main recurring categories: dinnerware, pictures/art, carpets/rugs, furniture/closets, and clothes.
   - Mark each needed field as `known`, `visible_estimate`, `missing_needs_requester`, or `not_applicable`.
5. Write `questions.md`.
   - Ask only questions that materially affect buyer confidence, pricing, shipping, or posting.
   - Prefer three to five questions maximum.
   - For Telegram/OpenClaw packets, proceed with clearly labeled estimates instead of asking for measurements unless exact dimensions are buyer-critical, especially for carpets, pictures, closets, and furniture.
6. Call `sales-strategy` with the extracted facts and missing-info summary.
7. Present the strategy to the requesting user and wait for explicit approval.
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
   - Keep unresolved form values explicit with `[BITTE ... EINGEBEN]` placeholders or `needs requesting user input` notes.
10. Write `status.txt`.
   - Initial status: `draft_needs_strategy`.
   - After strategy approval and listing/posting-packet creation: `draft_needs_posting_review`.
   - Publication approval remains separate and defaults to `not_approved`.
11. If ingestion was slowed by missing facts, unclear photos, category uncertainty, strategy uncertainty, or repeated requesting user clarification, append a short entry to `ingestion-learning-log.md`.
   - Do not log every routine item.
   - Capture the friction, recovery, and whether a checklist/playbook should change.

## Output Files

- `photos/`
- `item.md`
- `listing.md` after strategy approval
- `ricardo-posting.md` when Ricardo is the approved platform or the requesting user asks for Ricardo posting
- `questions.md`
- `status.txt`
- `ingestion-learning-log.md` entry when the intake produced a reusable lesson

Use the templates in `assets/` when creating these files. For Ricardo packets, use `assets/ricardo-posting-template.md` as the starting shape.

## Safety

- Do not publish listings.
- Do not message buyers.
- Do not include the full pickup address in listings.
- Do not include a phone number or personal email in public listing text.
- Do not create a final listing before the sales strategy is approved.
