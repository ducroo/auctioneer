# Gmail API OAuth Setup

Use Gmail API OAuth for `auctioneer600@gmail.com`.

## Google Cloud Setup

1. Open Google Cloud Console.
2. Create or select a project, for example `Auctioneer`.
3. Enable the Gmail API.
4. Configure the OAuth consent screen / Google Auth platform.
   - Audience can be external for a normal Gmail account.
   - Add `auctioneer600@gmail.com` as a test user if the app is in testing mode.
5. Create an OAuth client.
   - Application type: Desktop app.
   - Name: `Auctioneer local Gmail client`.
6. Download the OAuth client JSON.
7. Save it locally as:

```text
~/.openclaw/secrets/gmail-auctioneer-credentials.json
```

File permissions should be private:

```bash
chmod 600 ~/.openclaw/secrets/gmail-auctioneer-credentials.json
```

## Scopes

V1 read-only scope:

```text
https://www.googleapis.com/auth/gmail.readonly
```

Future draft/send scopes, only when needed:

```text
https://www.googleapis.com/auth/gmail.compose
https://www.googleapis.com/auth/gmail.send
```

If scopes change, delete the local token and re-run OAuth:

```text
~/.openclaw/secrets/gmail-auctioneer-token.json
```

## Local Token

The first OAuth run opens a browser consent flow and creates:

```text
~/.openclaw/secrets/gmail-auctioneer-token.json
```

Do not commit this file.
