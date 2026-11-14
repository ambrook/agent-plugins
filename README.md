# Ambrook agent plugins

Plugins that connect AI assistants to the read-only [Ambrook MCP endpoint](https://api.ambrook.com/mcp).

> [!IMPORTANT]
> This repository is generated. Its source is `mcp/agent-plugins/` in the Ambrook monorepo (`ambrook/ambrook.com`), and the `Sync agent-plugins` workflow there overwrites this repository on every change to `main`. Make changes in the monorepo; edits made here are lost on the next sync.

## Claude

The repository root is a Claude Code marketplace. In Claude Code:

```
/plugin marketplace add ambrook/agent-plugins
/plugin install ambrook@ambrook
```

See [claude-plugin/README.md](claude-plugin/README.md) for what the plugin contains and how to sign in.

## License

The plugin files in this repository are licensed under the [Apache License 2.0](LICENSE). The license does not cover the Ambrook service, which is governed by the [Ambrook Terms of Service](https://ambrook.com/terms), and does not grant permission to use Ambrook's name or logos.
