# Dojo Sensei MCP

Command-based MCP for Dojo Engine's Sensei - AI assistance for Cairo game development.

## Configuration

Installs directly from GitHub using npx with stdio transport.

## Usage

```json
{
  "servers": {
    "dojo-sensei": {
      "type": "stdio",
      "command": "npx",
      "args": [
        "--yes",
        "github:dojoengine/sensei-mcp"
      ]
    }
  }
}
```

## What it provides

AI-powered assistance for Dojo Engine game development on Starknet, including entity systems, world management, and Cairo gaming patterns.

## Project Location

In projects: `.vscode/mcp.json`

This MCP is simpler than Cairo Coder and doesn't require API keys or additional instructions.
