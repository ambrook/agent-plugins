# Ambrook for ChatGPT

Ask ChatGPT about your [Ambrook](https://ambrook.com) books. This package defines the Ambrook app for ChatGPT: its listing details, the connection to the read-only Ambrook MCP server, and the `use-ambrook` skill for month-end briefings, unpaid invoices, bills due, and bookkeeping cleanup.

> [!NOTE]
> The Ambrook MCP server is in beta. [Request access](https://ambrook.com/pilot) to turn it on for your account.

## Connect

Requires a paid ChatGPT plan (Plus, Pro, Business, Enterprise, or Edu) on chatgpt.com in a browser.

1. Open **Settings → Apps**.
2. Choose **Advanced** and turn on **Developer mode**.
3. Back on **Apps**, choose **Create**.
4. Enter the name `Ambrook`, the URL `https://api.ambrook.com/mcp`, and choose **OAuth** for authentication.
5. Choose **Create**, then sign in to Ambrook and approve access.

Start a new chat to use Ambrook.

## What's included

| File                          | What it does                                                   |
| ----------------------------- | -------------------------------------------------------------- |
| `plugin.json`                 | App listing: name, descriptions, example prompts, and links    |
| `mcp.json`                    | Connection to `https://api.ambrook.com/mcp` with OAuth sign-in |
| `skills/use-ambrook/SKILL.md` | Guidance for common bookkeeping reviews                        |

## Try asking

- "Compare my cash-basis profit and loss for the last two complete months."
- "Show my unpaid invoices and the total customers owe me."
- "Show my unpaid bills due in the next 30 days, including overdue bills."

## Security and privacy

The connection is read-only: ChatGPT can read your books but can't create or change records, send invoices, pay bills, or move money. You sign in with your own Ambrook account and approve access, and ChatGPT sees only the businesses your account can access.

See the [full setup and troubleshooting guide](https://github.com/ambrook/ambrook-plugin), the [Privacy Policy](https://ambrook.com/privacy), and the [Terms of Service](https://ambrook.com/terms).

## License

[Apache License 2.0](https://github.com/ambrook/ambrook-plugin/blob/main/LICENSE). The license covers the plugin files, not the Ambrook service, and does not grant permission to use Ambrook's name or logos.
