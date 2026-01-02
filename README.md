# yaml-lsp

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Plugin](https://img.shields.io/badge/claude-plugin-orange.svg)](https://docs.anthropic.com/en/docs/claude-code/plugins)
[![Marketplace](https://img.shields.io/badge/marketplace-zircote--lsp-purple.svg)](https://github.com/zircote/lsp-marketplace)
[![YAML](https://img.shields.io/badge/YAML-CB171E?logo=yaml&logoColor=white)](https://yaml.org/)

A Claude Code plugin providing comprehensive YAML development support through:

- **yaml-language-server** integration for IDE-like features
- **Automated hooks** for validation and formatting
- **YAML ecosystem** integration (yamllint, prettier)

## Quick Setup

```bash
# Run the setup command (after installing the plugin)
/setup
```

Or manually:

```bash
# Install yaml-language-server
npm install -g yaml-language-server

# Install development tools
pip install yamllint
npm install -g prettier
```

## Features

### LSP Integration

The plugin configures yaml-language-server for Claude Code via `.lsp.json`:

```json
{
    "yaml": {
        "command": "yaml-language-server",
        "args": ["--stdio"],
        "extensionToLanguage": {
            ".yaml": "yaml",
            ".yml": "yaml"
        },
        "transport": "stdio"
    }
}
```

**Capabilities:**
- Schema validation
- Hover documentation
- Code completion
- Document outline
- Real-time diagnostics

### Automated Hooks

| Hook | Trigger | Description |
|------|---------|-------------|
| `yamllint` | `**/*.yaml` | YAML validation |
| `prettier` | `**/*.yaml` | Formatting |
| `yq-validate` | `**/*.yaml` | Syntax validation |
| `yaml-todo-fixme` | `**/*.yaml` | Surface TODO/FIXME comments |

## Required Tools

| Tool | Installation | Purpose |
|------|--------------|---------|
| `yaml-language-server` | `npm i -g yaml-language-server` | LSP server |
| `yamllint` | `pip install yamllint` | Validation |
| `prettier` | `npm i -g prettier` | Formatting |
| `yq` | `brew install yq` | YAML processing |

## Project Structure

```
yaml-lsp/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── .lsp.json                  # yaml-language-server configuration
├── commands/
│   └── setup.md              # /setup command
├── hooks/
│   └── scripts/
│       └── yaml-hooks.sh
├── tests/
│   └── sample.yaml           # Test file
├── CLAUDE.md                  # Project instructions
└── README.md                  # This file
```

## License

MIT
