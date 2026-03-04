# Semantic Search Plugin

A hybrid code search plugin that combines claude-context semantic search with Grep.

## Features

- **Semantic Search**: Explore relevant code for conceptual/logical questions using claude-context
- **Precise Tracking**: Exhaustively trace exact identifiers (functions, variables, types) using Grep
- **Hybrid Strategy**: Automatically combines tools based on query type
- **Code Modification Safety Net**: Impact analysis before changes, completeness checks after

## Prerequisites: claude-context MCP Server

This plugin requires [claude-context](https://github.com/zilliztech/claude-context).

### Codebase Indexing

After setting up the MCP server, index the target codebase:

```
mcp__claude-context__index_codebase(path="/absolute/path/to/codebase")
```

## Usage

Automatically triggered when asking questions about the codebase or requesting code modifications.

```
"Where is the booking confirmation logic?"    → Semantic search first
"BookingState.SUCCESS usages"                 → Grep first
"Add a new state to BookingState"             → Hybrid (modification workflow)
```

## Structure

```
sementic-search-plugin/
├── .claude-plugin/
│   └── plugin.json
├── README.md
└── skills/
    └── semantic-search/
        ├── SKILL.md                  # Main skill definition
        └── references/
            └── search-patterns.md    # Search pattern examples
```
