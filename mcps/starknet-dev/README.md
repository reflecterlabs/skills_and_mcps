# Starknet Development MCPs

This directory contains Model Context Protocols for Starknet blockchain development.

## Available MCPs

- **openzeppelin-cairo/** - HTTP MCP for OpenZeppelin Cairo contracts
- **cairo-coder/** - Command MCP for AI-powered Cairo coding (requires API key)
- **sensei/** - Command MCP for Dojo Engine game development

## How to Use

Each MCP folder contains:
- `mcp.json` - The configuration file
- `README.md` - Documentation and setup instructions

## Configuration Types

### HTTP-based (OpenZeppelin)
Direct connection to hosted service, no local installation needed.

### Command-based (Cairo Coder, Sensei)
Runs as local process via npx. May require:
- API keys
- Environment variables
- Local dependencies

## Quick Setup

1. Copy the `mcp.json` content from the MCP you want to use
2. Paste into your `.vscode/mcp.json` or Claude Code MCP config
3. Update any required API keys or environment variables
4. Enable the MCP in your IDE
