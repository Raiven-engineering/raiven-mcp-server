# Raiven for Cursor

Cursor plugin that connects agents to [Raiven](https://www.raiven.com) through Raiven's hosted MCP server at `https://mcp.raiven.com/mcp`.

Read your Raiven requests, quotes, suppliers, quote comparisons, purchase orders, catalog and inbox, and create and edit RFQs, as your signed-in Raiven user, inside your organization and active branch.

## Install

Open **Customize** in Cursor, search for **Raiven** and select **Install**. For team marketplaces and local installs, see the [repository README](https://github.com/Raiven-engineering/raiven-mcp-server#install-in-cursor).

## Sign in

When Cursor first connects, it opens Raiven's sign-in page. Enter your Raiven email address and the code Raiven emails you, then approve the consent screen. There is nothing to configure.

## Permissions

| Permission | What it allows |
| --- | --- |
| `raiven:read` | View requests, quotes, suppliers, comparisons, purchase orders and the catalog. |
| `raiven:write` | Create and edit RFQs, branch suppliers and supplier contacts, and prepare RFQ emails. |
| `raiven:send` | Send prepared RFQ emails to suppliers. |
| `raiven:mail` | Read your Raiven inbox. |
| `offline_access` | Stay signed in between sessions. |

Sending RFQ emails to suppliers needs the `raiven:send` permission; without it, the send tool returns an `insufficient_scope` error. The plugin can't place orders.

## MCP

```json
{
  "mcpServers": {
    "raiven": {
      "type": "http",
      "url": "https://mcp.raiven.com/mcp",
      "auth": {
        "CLIENT_ID": "LpgtjtldPlxkEe1aHASDxWTZZ2Wv5XhU",
        "scopes": ["raiven:read", "raiven:write", "raiven:send", "raiven:mail", "offline_access"]
      }
    }
  }
}
```

The client ID identifies Raiven's sign-in client for Cursor. It is public, and there is no client secret.

## More

See the [repository README](https://github.com/Raiven-engineering/raiven-mcp-server#readme) for the tool list, data handling and support.

## License

MIT
