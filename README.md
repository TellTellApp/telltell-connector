# TellTell for Grok Bot

Manage your People directory, teams, groups, fields, tags, and ordinary account
settings through your TellTell Admin account.

![TellTell](assets/telltell-logomark.webp)

This package targets Agent Plugins 1.0.0 and TellTell’s remote MCP service. Grok
Bot is the first launch target. It contains no API keys or account records.

## Install and connect

After marketplace publication, open Grok Bot’s plugin picker, select TellTell,
and follow **Connect**. Sign in to TellTell, check the account, and select the
permissions you want to grant. Installation follows the official
[Grok Bot plugin guide](https://cursor.com/help/grok-bot/connect-plugins).

For a manual installation or private compatibility test, load this directory in
a client supporting [Agent Plugins](https://agent-plugins.org/specification).
For personal Cursor development, copy the package to
`~/.cursor/plugins/local/telltell`, reload Cursor, and open **Customize** to
connect. See
[Cursor local plugin testing](https://cursor.com/docs/plugins#test-plugins-locally).
This installs in Cursor; Grok Bot installation must be verified separately.

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

## Release status

This connector is being prepared for launch. Marketplace publication and the
actual Grok Bot installation test remain release gates. The local SDK/OAuth test
harness does not establish marketplace approval. The
[standalone repository](https://github.com/TellTellApp/telltell-connector)
contains only the connector package. Production endpoint activation and verified
provider protocol/callback details will be recorded here before launch.

## License

Connector code, configuration, and instructions use the [MIT license](LICENSE).
TellTell branding is reserved; see [the branding notice](NOTICE.md).
