# OpenZeppelin Cairo Contracts MCP

HTTP-based MCP for accessing OpenZeppelin's Cairo smart contract library.

## Configuration

This MCP uses HTTP connection to OpenZeppelin's hosted service.

## Usage

Add to your `.vscode/mcp.json` or Claude Code configuration:

```json
{
  "servers": {
    "OpenZeppelinCairoContracts": {
      "type": "http",
      "url": "https://mcp.openzeppelin.com/contracts/cairo/mcp"
    }
  }
}
```

## What it provides

Access to OpenZeppelin's Cairo contract standards and implementations for Starknet development.
