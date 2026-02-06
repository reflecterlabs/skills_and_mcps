# Cairo Coder MCP

Command-based MCP for Cairo code generation and assistance.

## Configuration

Requires API key for Kasar Labs' Cairo Coder service.

## Setup

1. Get your API key from Kasar Labs
2. Update the `CAIRO_CODER_API_KEY` in `mcp.json`
3. Add to your MCP configuration

## Usage

```json
{
  "mcpServers": {
    "cairo-coder": {
      "command": "npx",
      "args": ["-y", "@kasarlabs/cairo-coder-mcp"],
      "env": {
        "CAIRO_CODER_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## What it provides

AI-powered Cairo code generation, completion, and assistance for Starknet development.
