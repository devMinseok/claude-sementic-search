# Semantic Search Plugin

A hybrid code search plugin that combines claude-context semantic search with Grep.

## Features

- **Semantic Search**: Explore relevant code for conceptual/logical questions using claude-context
- **Precise Tracking**: Exhaustively trace exact identifiers (functions, variables, types) using Grep
- **Hybrid Strategy**: Automatically combines tools based on query type
- **Code Modification Safety Net**: Impact analysis before changes, completeness checks after

## Quick Start

### 1. Install the plugin

```bash
# Add the marketplace
/plugin marketplace add https://github.com/devMinseok/claude-sementic-search

# Install the plugin
/plugin install semantic-search@devminseok-plugins
```

### 2. Set up claude-context MCP server

This plugin requires [claude-context](https://github.com/zilliztech/claude-context). Follow its setup instructions to add it as an MCP server.

### 3. Index your codebase

```
mcp__claude-context__index_codebase(path="/absolute/path/to/codebase")
```

### 4. Start searching

Just ask questions about your codebase — the plugin triggers automatically.

```
"Where is the booking confirmation logic?"    → Semantic search first
"BookingState.SUCCESS usages"                 → Grep first
"Add a new state to BookingState"             → Hybrid (modification workflow)
```

## Structure

```
sementic-search-plugin/
└── skills/
    └── semantic-search/
        ├── SKILL.md                  # Main skill definition
        └── references/
            └── search-patterns.md    # Search pattern examples
```
