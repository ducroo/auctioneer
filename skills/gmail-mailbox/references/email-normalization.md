# Email Normalization

Create one Markdown file per relevant email.

Filename format:

```text
YYYY-MM-DD_HHMM_<gmail-message-id>.md
```

Use `assets/parsed-email-template.md`.

## Body Extraction

Keep:

- buyer message
- listing URL
- offer amount
- pickup/shipping question
- marketplace metadata

Remove or compress:

- repeated boilerplate
- unsubscribe blocks
- tracking links unrelated to listing
- long quoted history unless needed

## Status Values

- `new`
- `parsed`
- `handed_to_buyer_qa`
- `unmatched`
- `ignored`

## Matching

If listing URL maps to an item folder, include:

- `Item ID`
- `Matched item folder`

If not:

- move to `Unmatched/`
- set `Status: unmatched`
- include reason
