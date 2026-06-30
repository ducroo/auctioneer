---
name: "buyer-qa"
description: "Add browser caution for Ricardo buyer replies."
---

# Proposed Update: Browser Caution for Ricardo Replies

Update the existing `buyer-qa` skill with a browser automation note.

## Change to `SKILL.md`

In Workflow step 10, under pre-sale posting, add:

```markdown
- Browser automation may help navigate to the Ricardo message thread only after Lucas approves the exact reply.
- Use normal verified Ricardo browser context/profile; do not use fresh/headless public `agent-browser` if Ricardo presents Cloudflare/human verification.
- If a human-verification, captcha, login, or ambiguous thread appears, stop and report the blocker instead of clicking through.
```

## Operating Rule

For buyer communication, automation can reduce navigation friction but must never reduce approval friction. The exact message content and send/post action remain approval-gated.
