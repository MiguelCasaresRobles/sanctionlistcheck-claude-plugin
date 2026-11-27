# SanctionListCheck for Claude

This repository is a Claude Code plugin marketplace. It holds one plugin: `sanctionlistcheck`.
The plugin screens names against 10 official sanctions lists with the remote MCP server `https://sanctionlistcheck.com/mcp`.
Each hit is a possible match for a person to review.

## Install

```
/plugin marketplace add MiguelCasaresRobles/sanctionlistcheck-claude-plugin
/plugin install sanctionlistcheck@sanctionlistcheck
```

The plugin, its skill and its setup: [plugins/sanctionlistcheck/README.md](plugins/sanctionlistcheck/README.md).
Guide: https://sanctionlistcheck.com/mcp
Glama listing: https://glama.ai/mcp/connectors/com.sanctionlistcheck/sanctionlistcheck

## License

The MIT license covers the files in this repository. It does not give any right to use the SanctionListCheck name or logo.
