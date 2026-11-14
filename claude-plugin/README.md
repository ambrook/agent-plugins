# Ambrook for Claude

A Claude plugin that connects to the read-only [Ambrook MCP endpoint](https://api.ambrook.com/mcp) and adds the `use-ambrook` skill for month-end briefings, unpaid invoices, bills due, and bookkeeping cleanup.

It is ported from the ChatGPT plugin in the Ambrook monolith (`mcp/chatgpt-plugin`). Keep the skill in step with that package and with server changes that affect the workflows it describes.

## Contents

| Path                           | Purpose                                                      |
| ------------------------------ | ------------------------------------------------------------ |
| `.claude-plugin/plugin.json`   | Plugin manifest                                              |
| `.mcp.json`                    | Remote HTTP MCP server at `https://api.ambrook.com/mcp`      |
| `skills/use-ambrook/SKILL.md`  | How to pick the business and dates, pull reports, and stay read-only |

## Authentication

The server uses OAuth with dynamic client registration and the `external_mcp:read` scope. Claude starts the sign-in flow the first time a tool is used; in Claude Code, run `/mcp` and choose `ambrook` to authenticate. An Ambrook account with MCP access is required.

## Install

The repository root is a Claude Code marketplace (`.claude-plugin/marketplace.json`). In Claude Code:

```
/plugin marketplace add ambrook/agent-plugins
/plugin install ambrook@ambrook
```

When you release a change, bump `version` in both `.claude-plugin/plugin.json` and the marketplace entry.

## Try locally

```bash
claude --plugin-dir ./claude-plugin
```

Example prompts:

- Which Ambrook businesses can I access, and which one is my default?
- Compare my cash-basis profit and loss for the last two complete months.
- Show my unpaid invoices and the total customers owe me.
- Show my unpaid bills due in the next 30 days, including overdue bills.
- Show my 10 most recent transactions missing a category and any suggested categories.

Requests to change data (pay a bill, recategorize transactions, delete invoices) should be declined without calling tools; the connection is read-only.
