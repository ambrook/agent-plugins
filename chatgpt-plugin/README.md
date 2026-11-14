# Ambrook for ChatGPT

This directory is the source for the Ambrook plugin submitted to OpenAI. It connects to the read-only [Ambrook MCP endpoint](https://api.ambrook.com/mcp). The server implementation lives in [the main app](../../../src/backend/mcp/external/); this package contains the listing and review metadata, connection settings, icon, and `use-ambrook` skill. Update the skill and review cases alongside server changes that affect the workflows they describe. The Claude plugin in [`../claude-plugin`](../claude-plugin/) ships the same skill through a symlink, so a skill change reaches both.

## Build the submission ZIP

For a release, build from a clean checkout of the commit you're submitting. From the monorepo root:

```sh
(
  cd mcp/agent-plugins/chatgpt-plugin || exit 1
  ambrook_plugin_output=$(mktemp -d) || exit 1
  ambrook_plugin_zip="$ambrook_plugin_output/ambrook.zip"
  zip -X "$ambrook_plugin_zip" \
    plugin.json mcp.json assets/ambrook-icon.png skills/use-ambrook/SKILL.md &&
    unzip -t "$ambrook_plugin_zip" &&
    unzip -Z -1 "$ambrook_plugin_zip" &&
    printf 'Submission ZIP: %s\n' "$ambrook_plugin_zip"
)
```

The ZIP contains only the four listed files at its root. Keep generated ZIPs out of Git. When adding a package file, add it to the command above.

## Verify before submitting

- Test the packaged skill in ChatGPT with the Ambrook demo account. Run the cases in `plugin.json` and confirm that unsupported requests, such as paying a bill, don't trigger an attempted payment or a browser fallback.
- Check that the demo link plays for reviewers. Enter reviewer sign-in details only in OpenAI's secure **Review details** fields. Keep credentials and tokens out of Git and the ZIP.
- Upload the ZIP in OpenAI Platform and verify the imported listing, skill, connection, demo link, and review cases. See [OpenAI's submission guide](https://developers.openai.com/plugins/deploy/submission) for the portal steps.
