# Intent Rules

Classify the buyer message before drafting.

## Common Intents

- `availability`: asks whether item is still available.
- `measurements`: asks dimensions or sizes.
- `condition`: asks wear, defects, function, completeness.
- `price_offer`: proposes a lower price or asks best price.
- `pickup`: asks location, address, or pickup time.
- `shipping`: asks whether shipping is possible.
- `bundle`: asks about buying multiple items together.
- `reservation`: asks to hold the item.
- `complaint`: problem after sale or dissatisfaction.
- `spam_or_low_quality`: vague or suspicious inquiry.
- `other`: does not fit above.

## Negotiation Handling

- Draft, do not commit.
- If offer is reasonable, propose a requesting user approval decision.
- If offer is low, draft a polite decline or counteroffer with placeholder.
- Never reveal urgency.

## Missing Detail Handling

If the buyer asks for information not available in item files, use the missing-detail template rather than inventing facts.
