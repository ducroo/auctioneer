# Handoff To Buyer Q&A

After normalization, hand matched emails to `buyer-qa`.

Required handoff fields:

- source: gmail
- Gmail message ID
- Gmail thread ID
- platform
- listing URL
- item ID
- matched item folder
- buyer name/handle
- buyer message
- date

`buyer-qa` then:

- classifies intent
- drafts the reply
- logs it in `Daily_QA`
- appends item `qa.md`

Do not send the reply.
