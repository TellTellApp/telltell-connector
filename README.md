# TellTell for Grok Bot

Manage your People directory, teams, groups, fields, tags, and ordinary account
settings through your TellTell Admin account.

![TellTell](assets/telltell-logomark.webp)

This package targets Agent Plugins 1.0.0 and TellTell’s remote MCP service. Grok
Bot is the first launch target. It contains no API keys or account records.

## Review status — September 18, 2026

This is a pre-release submission, not an installable production release yet. The
production URL in `mcp.json` currently returns HTTP 404 because production
activation remains pending. Installing this package unchanged will not connect.
The staging service responds with an OAuth challenge, and its discovery and
OpenAPI endpoints are reachable. Successful sign-in and basic reads have been
verified in Cursor desktop; native Grok Bot verification remains pending.

The publisher application was submitted on September 11. Marketplace approval
and receipt confirmation remain pending. Cursor support directed application
follow-up to **marketplace-publishing@cursor.com**. We will replace this status
with verified production and installation evidence before requesting launch.

## Install and connect after release

After marketplace publication, open Grok Bot’s plugin picker, select TellTell,
and follow **Connect**. Sign in to TellTell, check the account, and select the
permissions you want to grant. Installation follows the official
[Grok Bot plugin guide](https://cursor.com/help/grok-bot/connect-plugins).

The remote MCP address is
`https://telltell-web-789927640952.us-east1.run.app/mcp`. Use the client’s OAuth
connection flow; never add a static bearer token to `mcp.json`.

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

Complete authorization with the designated staging account, then send a new
message asking to list TellTell tools and read groups. The complete native Grok
Bot OAuth/tool flow is still being verified; this documented setup route is not
a claim of marketplace approval. A private skill supplies workflow instructions
and does not replace the authenticated connector.

A local Cursor installation does not carry over into Grok Bot. Grok Bot's cloud
computer must be able to reach the MCP server over public HTTPS; `localhost` on
your own laptop is not that computer.

No static tokens, application source, or customer records belong in this
package. HTTP reachability and local SDK tests do not establish Grok Bot
certification.

## License

Connector code, configuration, and instructions use the [MIT license](LICENSE).
TellTell branding is reserved; see [the branding notice](NOTICE.md).
