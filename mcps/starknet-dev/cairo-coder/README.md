# Cairo Coder MCP

Command-based MCP for Cairo code generation and assistance.

## Configuration

Requires API key for Kasar Labs' Cairo Coder service.

## Project Location

```
project/
├── .vscode/
│   └── mcp.json              # MCP configuration
└── .github/
    └── copilot-instructions.md   # Usage instructions (IMPORTANT!)
```

## Setup

1. Get your API key from Kasar Labs
2. Copy `mcp.json` to `.vscode/mcp.json`
3. Update `CAIRO_CODER_API_KEY` with your actual key
4. Create `.github/copilot-instructions.md` with usage guidelines (see example in fairlaunch project)

## Usage

### mcp.json
```json
{
  "servers": {
    "cairo coder": {
      "command": "npx",
      "args": ["-y", "@kasarlabs/cairo-coder-mcp"],
      "env": {
        "CAIRO_CODER_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

### copilot-instructions.md
This file should include:
- When to use Cairo Coder MCP
- Coding standards and conventions
- Project structure guidelines
- How to query the MCP effectively (keep queries atomic!)
- Build/test commands to run after code changes

See: `C:\Users\henry\Desktop\fairlaunch\.github\copilot-instructions.md`

## What it provides

AI-powered Cairo code generation, completion, and assistance for Starknet development.

## Important Notes

- **ALWAYS** use the Cairo Coder MCP for Cairo questions
- Keep MCP queries atomic (one concept at a time)
- Run `scarb build` after writing Cairo code
- Combine with OpenZeppelin Cairo Contracts MCP for best results
