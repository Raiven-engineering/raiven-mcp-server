# Raiven MCP

Raiven MCP lets AI apps work with your [Raiven](https://www.raiven.com) account. An AI app connected to Raiven MCP can read your requests, quotes, suppliers, quote comparisons, purchase orders, catalog and Raiven inbox, and can create and edit RFQs. It acts as you, inside your organization and your active branch, with the same permissions you have in the Raiven portal.

This repository holds the Cursor plugin and its listing files. The Raiven MCP server is hosted by Raiven at `https://mcp.raiven.com/mcp`; its source code isn't public.

## Who can use it

Anyone with a Raiven account. There is no separate sign-up: you sign in with your usual Raiven login.

## Install in Cursor

Pick one:

- **Cursor Marketplace.** Once Raiven is listed, open **Customize** in Cursor, search for **Raiven** and select **Install**.
- **Team marketplace.** A Cursor team admin (Teams or Enterprise plan) can import this repository: **Dashboard → Plugins & MCPs → Team Marketplaces → Add Marketplace → Import from Repo**, then paste `https://github.com/Raiven-engineering/raiven-mcp-server`. Teammates then install Raiven from **Customize**.
- **Local plugin.** Copy the [`plugins/cursor`](plugins/cursor) folder to `~/.cursor/plugins/local/raiven`, then restart Cursor or run **Developer: Reload Window**. On Enterprise plans this needs local plugin imports to be allowed by an admin.

Cursor shows the server as `plugin-raiven-raiven` when it asks you to approve a tool call.

## Signing in

The first time Cursor connects, it opens Raiven's sign-in page in your browser:

1. Enter your Raiven email address and the code Raiven emails you.
2. Review the consent screen, which lists what Cursor is asking to do, and approve it.

Cursor then stays signed in and renews access on its own. Cursor never sees your Raiven portal session; it gets a token that only works with Raiven MCP.

Cursor asks for these permissions:

| Permission | What it allows |
| --- | --- |
| `raiven:read` | View your requests, quotes, quote suppliers and contacts, quote comparisons, purchase orders, catalogs and branch suppliers. |
| `raiven:write` | Create and edit RFQs, choose an RFQ's suppliers, add branch suppliers, add, edit and remove supplier contacts, and prepare RFQ emails. |
| `raiven:mail` | Read the email threads, messages and attachments in your Raiven inbox. |
| `offline_access` | Stay signed in, so you don't have to sign in again every time access expires. |

## What it can't do

- It can't place orders or send purchase orders.
- It can't email suppliers. It can prepare RFQ emails, but not send them.
- It can't send, reply to or change email in your Raiven inbox.
- It can't do anything you can't do in the Raiven portal, and it works only inside your organization and active branch.

## Tools

| Permission | Tools |
| --- | --- |
| `raiven:read` | `raiven_get_current_user`, `raiven_list_requests`, `raiven_get_request`, `raiven_list_quotes`, `raiven_get_quote`, `raiven_get_quote_suppliers`, `raiven_get_quote_supplier_contacts`, `raiven_get_quote_comparison`, `raiven_get_quote_purchase_orders`, `raiven_list_catalogs`, `raiven_search_catalog_parts`, `raiven_list_branch_suppliers` |
| `raiven:write` | `raiven_create_rfq`, `raiven_update_rfq`, `raiven_set_rfq_suppliers`, `raiven_prepare_rfq_emails`, `raiven_create_branch_supplier`, `raiven_create_supplier_contact`, `raiven_update_supplier_contact`, `raiven_delete_supplier_contact` |
| `raiven:mail` | `raiven_list_email_threads`, `raiven_get_email_thread`, `raiven_get_email_message`, `raiven_get_email_attachment` |

Email content is written by other people, such as suppliers. Raiven MCP marks it as untrusted, telling the AI app to treat it as information, never as instructions.

## Your data

- Tool results go to the AI app you connected, and are handled under that app's terms.
- Raiven keeps logs of tool calls for **[PLACEHOLDER: log retention period]**.
- To disconnect Cursor, open **Customize** in Cursor, find the Raiven server and log out. Cloud Agents keep a separate sign-in: log out on the server's Cloud row too.
- To revoke all AI-app access to your Raiven account: **[PLACEHOLDER: how users revoke all AI-app access]**.

See Raiven's [privacy policy](https://www.raiven.com/privacy-policy) and [terms of use](https://www.raiven.com/terms-of-use).

## Support

Email [support@raiven.com](mailto:support@raiven.com) for account, sign-in or data problems. Never include access tokens in an email or an issue.

## License

The files in this repository are licensed under the [MIT License](LICENSE).
