# Posting Packet

The posting packet is the single source of truth for form entry. For Ricardo, `ricardo-posting.md` is the preferred human-readable packet. A separate JSON file is optional later, but not required for the current workflow.

## Required Ricardo Fields

A complete Ricardo packet should answer:

- platform: Ricardo
- item ID and folder
- title
- description
- category path or closest category candidate
- condition
- sale format: auction, minimum-bid auction, or fixed price
- start price or fixed price in CHF
- buy-now price, or `none`
- quantity
- shipping mode: pickup only, shipping only, or pickup plus shipping
- pickup region only, never full public address
- payment mode or default Ricardo setting
- ordered photo paths
- remaining placeholders or guessed fields

## Packet Quality Rules

- Prefer concrete form values over prose such as "closest available category" when the value is already known from previous postings.
- Keep uncertainty explicit with `guessed`, `needs requesting user input`, or `accepted missing` notes.
- Keep the description German-only unless the requesting user explicitly asks otherwise.
- Do not include phone number, personal email, or full pickup address.
- Put pickup/shipping terms and private-sale disclaimer in the listing text.
- If the item needs measurements, brand/model, material, compatibility, size, or condition details for buyer confidence, resolve them before browser posting when feasible.

## Optional Machine-Readable Companion

When useful, create `posting-packet.json` next to `ricardo-posting.md` with the same data. Use this only as an accelerator for tooling; the markdown packet remains acceptable.

Recommended top-level keys:

```json
{
  "platform": "Ricardo",
  "item_id": "A0000",
  "title": "",
  "description": "",
  "category_path": "",
  "condition": "used",
  "sale_format": "auction",
  "start_price_chf": 0,
  "buy_now_price_chf": null,
  "quantity": 1,
  "shipping_mode": "pickup_only",
  "pickup_region": "Region Guemligen",
  "photo_paths_ordered": [],
  "guessed_fields": [],
  "remaining_risks": []
}
```
