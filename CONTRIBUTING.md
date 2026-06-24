# Contributing to My Claude Plugins Marketplace

Thank you for contributing! This guide walks you through submitting a new plugin.

## Prerequisites

- Claude Code installed
- Basic understanding of Claude Code plugin system
- Read [official docs](https://code.claude.com/docs/en/plugins)

## How to Submit a Plugin

### Step 1: Create Your Plugin Directory

```bash
mkdir plugins/<your-plugin-name>
```

### Step 2: Add Plugin Manifest

Create `plugins/<your-plugin-name>/.claude-plugin/plugin.json`:

```json
{
  "name": "<kebab-case-plugin-name>",
  "displayName": "<Human Readable Name>",
  "description": "<One-line description of what this plugin does>",
  "version": "1.0.0",
  "author": "<Your Name>",
  "license": "MIT",
  "source": {
    "relativePath": "./plugins/<your-plugin-name>"
  }
}
```

### Step 3: Add Components

Place plugin components directly in the plugin root:

```
plugins/<your-plugin-name>/
├── .claude-plugin/
│   └── plugin.json          ← REQUIRED
├── SKILL.md                 ← Skills (optional)
├── AGENT.md                 ← Agents (optional)
├── commands/
│   └── <command-name>.md    ← Commands (optional)
├── hooks/
│   └── hooks.json           ← Hooks (optional)
├── .mcp.json                ← MCP Server config (optional)
└── .lsp.json                ← LSP Server config (optional)
```

**Important rules:**

- Only `.claude-plugin/plugin.json` lives inside `.claude-plugin/`
- All other files (`SKILL.md`, `commands/`, `.mcp.json`, etc.) are at the plugin root
- Skills use `SKILL.md` with YAML frontmatter
- Commands use flat `.md` files in `commands/`
- Hooks use `hooks.json` at plugin root or in `hooks/hooks.json`

### Step 4: Register in Marketplace

Add your plugin to `.claude-plugin/marketplace.json`:

```json
{
  "name": "your-plugin-name",
  "displayName": "Your Plugin Name",
  "description": "Brief description",
  "version": "1.0.0",
  "author": "Your Name",
  "source": "./plugins/your-plugin-name"
}
```

### Step 5: Validate

```bash
claude plugin validate .
```

This checks your plugin manifest, version, and source paths.

### Step 6: Commit and Push

```bash
git add .
git commit -m "feat: add <plugin-name> plugin"
git push
```

### Step 7: Submit Pull Request

Open a PR with a clear description of:
- What the plugin does
- Which components it includes (skills, commands, agents, hooks, MCP servers)
- Any special permissions or dependencies

## Plugin Naming Guidelines

- Use kebab-case (e.g., `code-reviewer`, `doc-generator`)
- Avoid generic names that could conflict with official/community plugins
- Keep names descriptive but concise

## Plugin Ideas

Feel free to contribute any of these (or propose something new):

- **Code Review** — Automated PR review via Claude
- **Security Audit** — Scans for OWASP top 10 issues
- **Doc Generator** — Auto-generates documentation from code
- **Test Writer** — Generates unit tests for functions
- **Git Helper** — Smart commit messages, rebase assistance
- **Database Migration** — Reviews and validates DB migrations
- **API Tester** — Runs and validates REST/GraphQL APIs

## Questions?

Check the [official docs](https://code.claude.com/docs/en/plugins) or open an issue in this repo.
