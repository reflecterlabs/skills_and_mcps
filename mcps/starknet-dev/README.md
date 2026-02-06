# Starknet Development MCPs

This directory contains Model Context Protocols for Starknet blockchain development.

## Available MCPs

- **openzeppelin-cairo/** - HTTP MCP for OpenZeppelin Cairo contracts
- **cairo-coder/** - Command MCP for AI-powered Cairo coding (requires API key)
- **dojo-sensei/** - Command MCP for Dojo Engine game development

## Project Implementation Patterns

Based on real project usage, MCPs are implemented in two ways:

### Pattern A: Cairo Coder + OpenZeppelin (Complex Setup)
**Used in**: `fairlaunch` and similar Cairo contract projects

**Location in project**:
```
project/
├── .vscode/
│   └── mcp.json              # Both MCPs configured together
└── .github/
    └── copilot-instructions.md   # Detailed usage instructions
```

**Characteristics**:
- Multiple MCPs in single `mcp.json` (servers block)
- Cairo Coder requires API key in environment variables
- Has detailed `.github/copilot-instructions.md` with:
  - When to use the MCP
  - Coding standards and rules
  - Project structure guidelines
  - How to query the MCP effectively

**Example mcp.json**:
```json
{
  "servers": {
    "cairo coder": {
      "command": "npx",
      "args": ["-y", "@kasarlabs/cairo-coder-mcp"],
      "env": {
        "CAIRO_CODER_API_KEY": "your-key-here"
      }
    },
    "OpenZeppelinCairoContracts": {
      "type": "http",
      "url": "https://mcp.openzeppelin.com/contracts/cairo/mcp"
    }
  }
}
```

### Pattern B: Dojo Sensei (Simple Setup)
**Used in**: `dojo-game` and similar Dojo Engine projects

**Location in project**:
```
project/
└── .vscode/
    └── mcp.json              # Just the MCP config
```

**Characteristics**:
- Single MCP per project (usually)
- No API key required
- Uses `stdio` transport type
- No additional instruction files needed
- Simpler configuration

**Example mcp.json**:
```json
{
  "servers": {
    "dojo-sensei": {
      "type": "stdio",
      "command": "npx",
      "args": ["--yes", "github:dojoengine/sensei-mcp"]
    }
  }
}
```

## Configuration Types

### HTTP-based (OpenZeppelin)
- Direct connection to hosted service
- No local installation needed
- No API key required

### Command-based with API Key (Cairo Coder)
- Runs as local process via npx
- Requires `CAIRO_CODER_API_KEY` environment variable
- Has detailed usage instructions in `.github/copilot-instructions.md`

### Command-based Simple (Dojo Sensei)
- Runs as local process via npx
- Uses `stdio` transport
- No API key or additional setup needed

## Quick Setup

### For Cairo Contract Development (Pattern A):
1. Copy `mcp.json` to `.vscode/mcp.json`
2. Copy/adapt `.github/copilot-instructions.md`
3. Update `CAIRO_CODER_API_KEY` with your actual key
4. Both MCPs available together

### For Dojo Game Development (Pattern B):
1. Copy `mcp.json` to `.vscode/mcp.json`
2. Done! No additional setup needed

## Where to Find MCPs in This Repo

Each MCP folder contains:
- `mcp.json` - The configuration file
- `README.md` - MCP-specific documentation
