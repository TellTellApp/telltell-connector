# TellTell connector

Manage your TellTell Admin account's People directory, teams, overlapping email
groups, custom fields and tags, ordinary settings, and roster imports from
Cursor or Grok Bot. Tags are custom-field options and assignments.

![TellTell](assets/telltell-logomark.webp)

## What's included

- One skill, `manage-telltell`, for account selection, safe updates, roster
  previews, and job results.
- One MCP server, `telltell`, using Streamable HTTP at
  `https://mcp.telltell.co/mcp`.
- Agent Plugins 1.0.0 metadata and TellTell logomarks in
  `assets/telltell-logomark.webp` and `assets/telltell-logomark.svg`.

The package contains no credentials or account records. Cursor, Grok Bot, and
the separate ChatGPT connector use the same TellTell MCP service; each client
needs its own connection and permissions.

## Install

When TellTell is available in your client's marketplace:

**Cursor**

1. Open **Customize** and browse or search the plugin marketplace for
   **TellTell**.
2. Select **Install** and choose your project or user scope.
3. Open the TellTell MCP server's **Connect** or authentication control and
   complete TellTell's OAuth sign-in in your browser.

**Grok Bot**

1. Open the plugin picker (**Plugins**), search for **TellTell**, and add it.
2. Select **Connect**, **Authorize**, or **Authenticate**, as shown by your
   client.
3. Complete TellTell's OAuth sign-in in your browser.

Official guides: [Cursor plugins](https://cursor.com/docs/plugins) and
[Grok Bot plugins](https://cursor.com/help/grok-bot/connect-plugins).

### Connect directly

In Cursor, add this server to your existing MCP configuration, preserving other
entries, then enable it and authenticate:

```json
{
  "mcpServers": {
    "telltell": {
      "url": "https://mcp.telltell.co/mcp"
    }
  }
}
```

See [Cursor MCP setup](https://cursor.com/docs/mcp).

In Grok Bot, ask:

> Add this MCP server: https://mcp.telltell.co/mcp . Name it TellTell and use
> OAuth discovery and automatic client registration. Present the sign-in link
> for me to complete. After I authorize, inspect the tool schemas and call
> `telltell_context_get` to check my account and permissions. Do not create
> records, run jobs, or send email to check connectivity.

A direct MCP connection provides the tools. The packaged `manage-telltell` skill
is supplied by plugin installation. A local Cursor installation does not
configure Grok Bot's cloud connection.

## Sign-in and access

Sign in as a TellTell Admin, confirm the intended account, and choose the
permissions to grant. The server uses OAuth with dynamic client registration,
PKCE, and renewable access through `offline_access`. Use your client's OAuth
flow; leave manual client ID and secret overrides empty and never put a static
bearer token in `mcp.json`.

Available data scopes are `people:read` / `people:write`, `groups:read` /
`groups:write`, `fields:read` / `fields:write`, `settings:read` /
`settings:write`, and `jobs:read` / `jobs:write`. Teams and memberships use
group scopes; group permission and notice changes also require `settings:write`.
Grant only what you need. Start with read permissions, then ask: “Check which
TellTell account and permissions are connected.”

Bulk edits start disabled. An Admin can enable **Allow bulk edits** for the
connection in TellTell **Settings → Connections** after reviewing the email
effects. Roster imports, bulk changes to people's field values, and bulk group
assignments require a stored preview and your confirmation before applying.
Destructive changes and changes affecting email delivery also require a preview
and confirmation. Adding group members or new email addresses can send
configured welcome messages.

Revoke access in TellTell **Settings → Connections → Revoke connection**.
Revocation stops future access; completed changes and queued email remain. The
connector does not provide standalone email sending, billing management,
account-user administration, or account deletion.

## Privacy, terms, and support

[Privacy](https://telltell.co/privacy) · [Terms](https://telltell.co/terms) ·
[Support](https://telltell.co/contact)

## Package synchronization

Source updates are mirrored automatically from TellTell's application repository
with a generated SHA-256 `package-integrity.json`.

## License

Connector code, configuration, and instructions use the [MIT license](LICENSE).
TellTell branding is reserved; see [the branding notice](NOTICE.md).
