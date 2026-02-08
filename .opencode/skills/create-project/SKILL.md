---
name: create-project
description: |
  Orchestrates the creation of new projects at ~/Desktop/ with proper configuration.
  Use this skill when the user wants to create a new project of any type.
  
  Supports project types:
  - cairo: Starknet smart contracts using Scarb/Starknet Foundry
  - solidity: EVM smart contracts using Foundry
  - noir: ZK circuits using Nargo
  - agents: AI agents using Daydreams, ElizaOS, or Starknet-Agentic
  - integration: Full-stack dApp with Vite frontend, contracts, proving, and agents
  
  This meta-skill sets up the universal project structure, configures MCPs,
  references relevant skills, and runs the appropriate init command.
  
  Requirements: OpenCode v1.1.2+ or Claude Code
---

# Create Project

This meta-skill creates new projects with proper configuration for the Reflecter Labs workflow.

## When to Use

Use this skill when the user wants to create a new project. The skill will:
1. Ask for project name and type
2. Create the project at ~/Desktop/{project-name}/
3. Set up universal configuration folders (.github, .opencode, .claude, .vscode)
4. Configure relevant skills and MCPs
5. Run the appropriate init command
6. Set up type-specific folder structure

## Project Types

### 1. Cairo (Smart Contracts)
- **Framework**: Starknet Foundry
- **Init Command**: `scarb init`
- **MCPs**: Cairo Coder + OpenZeppelin Cairo Contracts
- **Copilot Instructions**: Yes (for Cairo Coder MCP)

### 2. Solidity (Smart Contracts)
- **Framework**: Foundry
- **Init Command**: `forge init`
- **MCPs**: None (no MCPs configured for Solidity)
- **Copilot Instructions**: No

### 3. Noir (ZK Circuits)
- **Framework**: Nargo
- **Init Command**: `nargo init`
- **MCPs**: None (to be added when available)
- **Copilot Instructions**: No

### 4. Agents (AI Agents)
- **Framework**: User chooses
  1. **Daydreams**: `bunx @lucid-agents/cli my-agent`
  2. **ElizaOS**: `elizaos create`
  3. **Starknet-Agentic**: `npx create-starknet-agent@latest`
- **MCPs**: Depends on framework
- **Copilot Instructions**: No

### 5. Integration (Full-Stack dApp)
- **Frontend**: Vite
- **Init Command**: `npm create vite@latest app/`
- **Structure**:
  - `contracts/`: Cairo or Solidity (user chooses)
  - `proving/`: Client-side proving (empty, for future)
  - `app/`: Vite frontend
  - `agents/`: Agent code
- **MCPs**: All relevant to chosen tech stack
- **Copilot Instructions**: Yes if using Cairo

## Workflow

### Step 1: Gather Information

Ask the user:
1. **Project name**: What should we call this project?
2. **Project type**: Which type?
   - cairo
   - solidity
   - noir
   - agents
   - integration

3. **If agents type**: Which framework?
   1. Daydreams
   2. ElizaOS
   3. Starknet-Agentic

4. **If integration type**: 
   - Which language for contracts folder? (cairo/solidity)
   - Which agent framework? (Daydreams/ElizaOS/Starknet-Agentic)

### Step 2: Create Project Directory

Create: `~/Desktop/{project-name}/`

### Step 3: Create Universal Structure

Create these folders in the project:
```
project/
├── .github/
├── .opencode/
├── .claude/
└── .vscode/
```

### Step 4: Configure Skills

Create `.opencode/skills.json` and `.claude/skills.json`:

```json
{
  "skills": {
    "skill-creator": "../skills_and_mcps/skills/anthropic/skill-creator"
  }
}
```

Note: Use forward slashes in paths even on Windows.

### Step 5: Configure MCPs

Create `.vscode/mcp.json` with relevant MCPs:

**For Cairo**:
```json
{
  "servers": {
    "cairo coder": {
      "command": "npx",
      "args": ["-y", "@kasarlabs/cairo-coder-mcp"],
      "env": {
        "CAIRO_CODER_API_KEY": "your-api-key-here"
      }
    },
    "OpenZeppelinCairoContracts": {
      "type": "http",
      "url": "https://mcp.openzeppelin.com/contracts/cairo/mcp"
    }
  }
}
```

**For Solidity**: Empty or minimal MCPs
```json
{
  "servers": {}
}
```

**For Noir**: Empty (MCPs to be added later)
```json
{
  "servers": {}
}
```

**For Agents**: Depends on framework (configure as needed)

**For Integration**:
```json
{
  "servers": {
    "cairo coder": {
      "command": "npx",
      "args": ["-y", "@kasarlabs/cairo-coder-mcp"],
      "env": {
        "CAIRO_CODER_API_KEY": "your-api-key-here"
      }
    },
    "OpenZeppelinCairoContracts": {
      "type": "http",
      "url": "https://mcp.openzeppelin.com/contracts/cairo/mcp"
    }
  }
}
```
(Only include Cairo MCPs if contracts are Cairo)

### Step 6: Add Copilot Instructions (If Needed)

For **cairo** and **integration with cairo**, copy:
`./references/copilot-instructions.md`
to:
`~/Desktop/{project-name}/.github/copilot-instructions.md`

### Step 7: Run Init Command

Run the appropriate init command in the project directory:

- **cairo**: `scarb init`
- **solidity**: `forge init`
- **noir**: `nargo init`
- **agents**: Framework-specific command
- **integration**: `npm create vite@latest app/`

### Step 8: Create Integration Folders (If Integration Type)

If integration type, create after Vite init:
```
project/
├── contracts/          # Empty, for Cairo or Solidity
├── proving/            # Empty, for future client-proving
└── agents/             # Empty, for agent code
```

### Step 9: Verify and Report

1. List created structure
2. Report any manual steps needed (e.g., "Add your Cairo Coder API key to .vscode/mcp.json")
3. Suggest next steps

## Important Notes

- **Always use forward slashes** in file paths, even on Windows
- Projects are always created at `~/Desktop/{project-name}/`
- This skill is automatically discovered by OpenCode from `.opencode/skills/create-project/SKILL.md`
- Copilot instructions are only for Cairo Coder MCP guidance
- Each project references the skill-creator skill for future skill development

## Team Setup Convention (CRITICAL)

This skill uses **relative paths** to reference the central `skills_and_mcps` repository. For this to work correctly across all team members' machines, everyone must follow this convention:

### Required Setup

1. **Clone Location (MANDATORY)**
   All team members must clone the repository to:
   ```
   ~/Desktop/skills_and_mcps/
   ```

2. **How to Clone:**
   ```bash
   cd ~/Desktop
   git clone https://github.com/reflecterlabs/skills_and_mcps.git
   ```

3. **Usage:**
   ```bash
   cd ~/Desktop/skills_and_mcps
   opencode  # or claude
   # Then say: "Create new project"
   ```

### Why This Matters

The skill generates projects at `~/Desktop/{project-name}/` with skill references like:
```json
{
  "skills": {
    "skill-creator": "../skills_and_mcps/skills/anthropic/skill-creator"
  }
}
```

This relative path (`../skills_and_mcps/`) works because:
- New projects are at: `~/Desktop/new-project/`
- The skills repo is at: `~/Desktop/skills_and_mcps/`
- From the new project, the skills repo is: `../skills_and_mcps/`

**This approach:**
- ✅ Works regardless of username (alice, bob, charlie)
- ✅ Works on macOS, Linux, and Windows (WSL)
- ✅ Requires no environment variables
- ✅ Requires no setup commands
- ✅ Is completely portable across team members

### Troubleshooting

If skills are not found in new projects:
1. Verify `skills_and_mcps` is at `~/Desktop/skills_and_mcps/`
2. Verify the new project is at `~/Desktop/{project-name}/`
3. Check that both are in the same parent directory (`~/Desktop/`)
