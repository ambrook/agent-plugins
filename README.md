# Ambrook agent plugins

Plugins that connect AI assistants to the read-only [Ambrook MCP endpoint](https://api.ambrook.com/mcp).

> [!NOTE]
> Ambrook publishes this repository automatically, and changes made here directly are overwritten. To report a problem or request a change, contact [Ambrook support](https://support.ambrook.com/en/).

## Claude

The repository root is a Claude Code marketplace. In Claude Code:

```
/plugin marketplace add ambrook/agent-plugins
/plugin install ambrook@ambrook
```

See [claude-plugin/README.md](claude-plugin/README.md) for what the plugin contains and how to sign in.

## ChatGPT

[chatgpt-plugin](chatgpt-plugin/) contains the Ambrook plugin package for ChatGPT.

## License

The plugin files in this repository are licensed under the [Apache License 2.0](LICENSE). The license does not cover the Ambrook service, which is governed by the [Ambrook Terms of Service](https://ambrook.com/terms), and does not grant permission to use Ambrook's name or logos.
