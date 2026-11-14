# Ambrook for Grok

Ask Grok about your [Ambrook](https://ambrook.com) books. This Grok Build plugin connects to the hosted, read-only Ambrook MCP server and adds the `use-ambrook` skill, which guides Grok through month-end briefings, unpaid invoices, bills due, and bookkeeping cleanup.

> [!NOTE]
> The Ambrook MCP server is in beta. [Request access](https://ambrook.com/pilot) to turn it on for your account.

Using Grok Bot instead? Add Ambrook from a chat; see the [Grok Bot setup steps](https://github.com/ambrook/agent-plugins#grok).

## What's included

| Component                  | What it does                                                                         |
| -------------------------- | ------------------------------------------------------------------------------------ |
| MCP server (`.mcp.json`)   | Connects to `https://api.ambrook.com/mcp` over Streamable HTTP                       |
| Skill (`use-ambrook`)      | Picks the right business and dates, reports full totals, and keeps answers read-only |
| Manifest (`.grok-plugin/`) | Plugin name, version, keywords, and logo                                             |

The plugin has no hooks, commands, agents, or local scripts.

## Network endpoints and credentials

- **Endpoint:** `https://api.ambrook.com/mcp`, the hosted Ambrook MCP server. The plugin calls no other endpoint.
- **Credentials:** none stored in the plugin. On first connect, you sign in with your Ambrook account through OAuth and approve the read-only `external_mcp:read` scope.
- **Access:** read-only, and limited to the businesses your Ambrook account can access. Grok can't create or change records, send invoices, pay bills, or move money.

## Try asking

- "Compare my profit and loss for the last two months and explain the three biggest changes."
- "How much do customers owe me, and which unpaid invoices are due soonest?"
- "Which bills are due in the next 30 days, including anything overdue?"
- "Which recent transactions still need a category, and what does Ambrook suggest?"

## Troubleshooting

- **The connection fails or says "not found":** your account may not have the AI connection turned on yet. [Request access](https://ambrook.com/pilot) or contact [Ambrook support](https://support.ambrook.com/en/).
- **Sign-in gets stuck:** make sure your browser is signed in to the right Ambrook account, then try connecting again.

See the [full troubleshooting guide](https://github.com/ambrook/agent-plugins#troubleshooting).

## Support

- [Documentation](https://ambrook.com/mcp-server)
- [Help center](https://support.ambrook.com/en/) · [support@ambrook.com](mailto:support@ambrook.com)
- [Privacy Policy](https://ambrook.com/privacy) · [Terms of Service](https://ambrook.com/terms)

## License

[Apache License 2.0](https://github.com/ambrook/agent-plugins/blob/main/LICENSE). The license covers the plugin files, not the Ambrook service, and does not grant permission to use Ambrook's name or logos.
