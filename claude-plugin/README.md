# Ambrook for Claude

A Claude plugin that connects to the read-only [Ambrook MCP endpoint](https://api.ambrook.com/mcp) and adds the `use-ambrook` skill for month-end briefings, unpaid invoices, bills due, and bookkeeping cleanup.

## Contents

| Path                          | Purpose                                                              |
| ----------------------------- | -------------------------------------------------------------------- |
| `.claude-plugin/plugin.json`  | Plugin manifest                                                      |
| `.claude-plugin/icon.png`     | Listing icon (512 × 512 PNG)                                         |
| `.mcp.json`                   | Remote HTTP MCP server at `https://api.ambrook.com/mcp`              |
| `skills/use-ambrook/SKILL.md` | How to pick the business and dates, pull reports, and stay read-only |

## Authentication

The server uses OAuth with dynamic client registration and the `external_mcp:read` scope. Claude starts the sign-in flow the first time a tool is used; in Claude Code, run `/mcp` and choose `ambrook` to authenticate. An Ambrook account with MCP access is required.

## Install

```
/plugin marketplace add ambrook/agent-plugins
/plugin install ambrook@ambrook
```

## Example prompts

- Which Ambrook businesses can I access, and which one is my default?
- Compare my cash-basis profit and loss for the last two complete months.
- Show my unpaid invoices and the total customers owe me.
- Show my unpaid bills due in the next 30 days, including overdue bills.
- Show my 10 most recent transactions missing a category and any suggested categories.

Requests to change data (pay a bill, recategorize transactions, delete invoices) should be declined without calling tools; the connection is read-only.

## Developing (Ambrook monorepo)

The source lives in `mcp/agent-plugins/` in `ambrook/ambrook.com`, and the `Sync agent-plugins` workflow publishes it to [`ambrook/agent-plugins`](https://github.com/ambrook/agent-plugins) on every change to `main`.

- `skills` is a symlink to `../chatgpt-plugin/skills`, so the Claude and ChatGPT plugins ship the same skill. The sync copies the files, not the link.
- Bump `version` in `.claude-plugin/plugin.json` when you change the plugin, so installed copies pick up the update.
- From the monorepo root, validate with `claude plugin validate mcp/agent-plugins` and try it with `claude --plugin-dir mcp/agent-plugins/claude-plugin`.
