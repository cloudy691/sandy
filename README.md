# My Claude Plugins Marketplace

A curated marketplace for Claude Code plugins — custom skills, agents, hooks, and MCP servers that extend Claude Code's capabilities.

## Quick Start

### 1. Add the Marketplace

```
/plugin marketplace add <owner>/<repo>
```

Or with full URL:

```
/plugin marketplace add https://github.com/<owner>/<repo>
```

### 2. Install Plugins

After adding the marketplace, install plugins:

```
/plugin install <plugin-name>@my-claude-plugins
```

Or browse all available plugins interactively:

```
/plugin install
```

### 3. Manage Plugins

```
/plugin list                          # List installed plugins
/plugin enable <plugin>@<marketplace> # Enable a disabled plugin
/plugin disable <plugin>@<marketplace># Disable a plugin
/plugin uninstall <plugin>@<marketplace> # Remove a plugin
/plugin update <plugin>@<marketplace>    # Update a plugin
/plugin marketplace list                # List available marketplaces
```

### 4. Reload

After making changes to plugin configuration:

```
/reload-plugins
```

## Current Plugins

_This marketplace is empty by default — plugins are welcomed via PR._

See [CONTRIBUTING.md](./CONTRIBUTING.md) for details on how to submit a new plugin.

## Plugin Structure

Each plugin in this marketplace follows the official Claude Code plugin format:

- **Skills** — Custom domain-specific capabilities (e.g., `skills/<name>/SKILL.md`)
- **Agents** — Specialized sub-agents (e.g., `agents/<name>/AGENT.md`)
- **Commands** — Slash commands (e.g., `commands/<name>.md`)
- **Hooks** — Automated behaviors triggered by events (e.g., `hooks/hooks.json`)
- **MCP Servers** — External tool integrations (e.g., `.mcp.json`)
- **LSP Servers** — Language server protocol integrations (e.g., `.lsp.json`)
- **Themes** — Visual customization (e.g., `themes/<name>.json`)
- **Monitors** — Experimental health-check monitors (e.g., `monitors/monitors.json`)

## Validation

Before submitting a plugin, validate the entire marketplace:

```bash
claude plugin validate .
```

To validate strict mode (warnings as errors):

```bash
claude plugin validate . --strict
```

## License

This marketplace and its submitted plugins are released under the [MIT License](./LICENSE).

## References

- Official docs: https://code.claude.com/docs/en/plugins
- Official marketplace: https://claude.com/plugins
- Community plugins: https://github.com/anthropics/claude-plugins-community
