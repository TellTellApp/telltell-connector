# TellTell for Grok Bot

Manage your People directory, teams, groups, fields, tags, and ordinary account
settings through your TellTell Admin account.

![TellTell](assets/telltell-logomark.webp)

This package targets Agent Plugins 1.0.0 and TellTell’s remote MCP service. Grok
Bot is the first launch target. It contains no API keys or account records.

## Availability and review status

TellTell’s production MCP service is available to Admins across TellTell
accounts. The endpoint in `mcp.json` requires OAuth. On September 18, 2026,
production passed checks for MCP authentication challenges, protected-resource
discovery, OAuth issuer discovery, and its published OpenAPI contract. Settings
→ Connections is available in the production app.

The Cursor Marketplace publisher application was submitted on September 11 and
listing approval remains pending. Marketplace installation is a separate step
from connecting the hosted MCP service directly. Application follow-up goes to
**marketplace-publishing@cursor.com**.

Native Grok Bot completed OAuth, discovered eight read-only tools, and read
connection context and groups in an owner-confirmed synthetic staging account on
September 18. That test granted only `people:read` and `groups:read`, with bulk
edits disabled. It verifies native Grok Bot compatibility for that staging read
flow; it does not claim Marketplace approval or production write testing.

## Connect now

Ask your Grok Bot:

> Add this MCP server: https://telltell-web-789927640952.us-east1.run.app/mcp .
> Name it TellTell and use its OAuth discovery and automatic client
> registration. Present the sign-in link for me to complete. Start with People
> and groups read permissions if scope selection is supported. After I
> authorize, list the tools and check connection permissions; wait before
> reading or changing account data.

Complete the connect card, sign in as a TellTell Admin, confirm the intended
account, and select the permissions you want to grant. Use the client’s OAuth
flow; do not supply a manual client ID, guess a callback address, or put a
static bearer token in `mcp.json`. Start with read permissions and confirm bulk
edits are off before trying account reads.

After Marketplace approval and publication, you can instead open Grok Bot’s
plugin picker, select TellTell, and follow **Connect**. See the official
[Grok Bot plugin guide](https://cursor.com/help/grok-bot/connect-plugins).

Ask “List my TellTell groups” or “Update Alex’s name to Alex Chen.” For a roster
import, review the preview and approve the proposed changes in the conversation.
Bulk edits start disabled. An Admin can enable them for this connection in
TellTell **Settings → Connections**, after reviewing the email and undo warning.

Connections use current account entitlements with no additional connector charge
in v1. Revoke access in **Settings → Connections**. Completed updates and queued
welcome messages remain effective after revocation.

## Staging and local compatibility testing

For designated testers using synthetic TellTell staging accounts, the hosted
staging MCP URL is:

```text
https://telltell-web-342964311037.us-east1.run.app/mcp
```

Use the client's OAuth connection flow with a staging Admin account. Start with
People/groups read permissions and leave bulk edits disabled. First ask it to
list the available TellTell tools and read the synthetic account's groups; do
not enable write access until the connection has been verified.

**Cursor desktop:** a local copy can use the staging URL with both the plugin
and MCP server named `telltell-staging`. Load it from
`~/.cursor/plugins/local/telltell-staging`, reload Cursor, and open
**Customize**. See
[Cursor local testing](https://cursor.com/docs/plugins#test-plugins-locally).
Keep this staging copy separate; do not submit it as the production package.

**Grok Bot:** add the hosted server through a Bot conversation. Cursor staff
[documents this chat-based setup](https://forum.cursor.com/t/grokbot-custom-connectors/169965);
there is no custom-connector settings form. Send:

> Add this MCP server: https://telltell-web-342964311037.us-east1.run.app/mcp .
> Name it telltell-staging and use its OAuth flow. This is a synthetic staging
> test. Present the authorization link for me to complete. Do not change
> records, run jobs, or send email.

Use native OAuth discovery and client-managed dynamic registration; do not
manually inject a client ID or guess callback addresses. Complete authorization
with the designated staging account, then request tool discovery, connection
context, and a bounded groups read. This flow passed staging read-only testing;
write, refresh, revocation, and Marketplace installation checks remain separate.
A private skill supplies workflow instructions and does not replace the
authenticated connector.

A local Cursor installation does not carry over into Grok Bot. Grok Bot's cloud
computer must be able to reach the MCP server over public HTTPS; `localhost` on
your own laptop is not that computer.

No static tokens, application source, or customer records belong in this
package. HTTP reachability and local SDK tests do not establish Grok Bot
certification.

## License

Connector code, configuration, and instructions use the [MIT license](LICENSE).
TellTell branding is reserved; see [the branding notice](NOTICE.md).
