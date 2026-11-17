# Ambrook for Cursor

Ask Cursor about your [Ambrook](https://ambrook.com) books. This plugin connects Cursor to the read-only Ambrook MCP server and adds the `use-ambrook` skill, which guides the agent through month-end briefings, unpaid invoices, bills due, and bookkeeping cleanup.

> [!NOTE]
> The Ambrook MCP server is in beta. [Request access](https://ambrook.com/pilot) to turn it on for your account.

## Install

1. In Cursor, open **Customize** in the sidebar, or browse the [Cursor Marketplace](https://cursor.com/marketplace).
2. Search for **Ambrook** and choose **Install**.
3. Under **MCP servers**, find `ambrook`, choose **Connect**, then sign in to Ambrook and approve access.

On a team plan, an admin can add this repository as a team marketplace instead: open **Dashboard → Plugins & MCPs**, choose **Add Marketplace → Import from Repo**, and enter `https://github.com/ambrook/ambrook-plugin`.

## What's included

| Component                    | What it does                                                                         |
| ---------------------------- | ------------------------------------------------------------------------------------ |
| MCP server (`mcp.json`)      | Connects to `https://api.ambrook.com/mcp` over Streamable HTTP                       |
| Skill (`use-ambrook`)        | Picks the right business and dates, reports full totals, and keeps answers read-only |
| Manifest (`.cursor-plugin/`) | Plugin name, version, keywords, and logo                                             |

The plugin has no rules, hooks, commands, agents, or local scripts.

## Try asking

- "Compare my profit and loss for the last two months and explain the three biggest changes."
- "How much do customers owe me, and which unpaid invoices are due soonest?"
- "Which bills are due in the next 30 days, including anything overdue?"
- "Which recent transactions still need a category, and what does Ambrook suggest?"

## Security and privacy

The connection is read-only: Cursor can read your books but can't create or change records, send invoices, pay bills, or move money. You sign in with your own Ambrook account through OAuth and approve the read-only `external_mcp:read` scope, and Cursor sees only the businesses your account can access. The plugin connects only to `https://api.ambrook.com/mcp` and stores no credentials.

## Troubleshooting

- **The connection fails or says "not found":** your account may not have the AI connection turned on yet. [Request access](https://ambrook.com/pilot) or contact [Ambrook support](https://support.ambrook.com/en/).
- **Sign-in gets stuck:** make sure your browser is signed in to the right Ambrook account, then turn the `ambrook` MCP server off and on in **Customize** and connect again.

See the [full troubleshooting guide](https://github.com/ambrook/ambrook-plugin#troubleshooting).

## Support

- [Documentation](https://ambrook.com/mcp-server)
- [Help center](https://support.ambrook.com/en/) · [support@ambrook.com](mailto:support@ambrook.com)
- [Privacy Policy](https://ambrook.com/privacy) · [Terms of Service](https://ambrook.com/terms)

## License

[Apache License 2.0](https://github.com/ambrook/ambrook-plugin/blob/main/LICENSE). The license covers the plugin files, not the Ambrook service, and does not grant permission to use Ambrook's name or logos.
