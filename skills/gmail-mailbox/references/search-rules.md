# Search Rules

Search marketplace-origin emails from `auctioneer600@gmail.com`.

## Default Query

Start narrow:

```text
newer_than:14d (ricardo OR tutti OR anibis OR vinted OR facebook OR autoscout OR ronorp OR ebay)
```

For routine processing:

```text
is:unread newer_than:7d
```

Do not mark messages read unless the requesting user asks.

## Relevant Sources

Likely marketplace sources:

- Ricardo
- tutti
- Anibis
- Vinted
- Facebook Marketplace
- Ron Orp
- AutoScout24
- eBay special cases

## Must Extract

- Gmail message ID
- Gmail thread ID
- date
- from
- subject
- marketplace
- listing URL
- listing ID if visible
- buyer name/handle if visible
- buyer message
