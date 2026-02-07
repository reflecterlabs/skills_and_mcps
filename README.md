# ✨ Skills & MCP

**The Skills Center of Reflecter Labs**

Where AI capabilities come to life.

---

## 🚀 Quick Start for Developers

### 1. Setup inicial (una vez)
```bash
cd ~/Desktop
git clone https://github.com/reflecterlabs/skills_and_mcps.git
cd skills_and_mcps
```

### 2. Usar el meta-skill
```bash
# En la carpeta skills_and_mcps
claude  # o opencode
```

Luego escribe: **"Create new project"**

El meta-skill `create-project` se detecta automáticamente desde `.claude/skills.json`.

### 3. Tipos de proyectos soportados

| Tipo | Comando init | MCPs incluidos |
|------|-------------|----------------|
| `cairo` | `scarb init` | Cairo Coder + OpenZeppelin |
| `solidity` | `forge init` | Ninguno |
| `noir` | `nargo init` | Ninguno |
| `agents` | Framework específico | Depende del framework |
| `integration` | `npm create vite@latest app/` | Todos los relevantes |

**Frameworks agents**: Daydreams, ElizaOS, Starknet-Agentic

### 4. Estructura creada
```
~/Desktop/{project-name}/
├── .github/           # copilot-instructions.md (solo Cairo)
├── .opencode/
│   └── skills.json    # Referencias a skills_and_mcps
├── .claude/
│   └── skills.json    # Referencias a skills_and_mcps
└── .vscode/
    └── mcp.json       # Configuración de MCPs
```

### 5. Notas importantes
- Siempre se crea en `~/Desktop/`
- Usa `/` en paths (incluso en Windows)
- Para Cairo: agrega tu API key de Cairo Coder en `.vscode/mcp.json`
- Los skills se referencian, no se copian

### 6. Workflow típico
```bash
cd ~/Desktop/skills_and_mcps
claude
> "Create new project"
# Seguir prompts: nombre, tipo, framework si aplica
cd ~/Desktop/mi-nuevo-proyecto
# Empezar a codear
```

---

## 🎯 What Lives Here

A curated collection of **Skills** (what we can do) and **MCPs** (how we connect) that power our meta-skills and workflows.

```
skills/
├── 🌙 daydreams/            # Lucid ecosystem skills
└── 🧠 anthropic/            # Anthropic skill-creator

mcps/
├── ⛓️  starknet-dev/        # Cairo, Dojo, OpenZeppelin
├── 🗄️  data-backend/       # Supabase & databases
└── 📋 project-management/   # Jira & tracking

meta-skills/                # The conductors 🎼
└── create-project/         # Project creation meta-skill
```

## 🎨 Contributing

Add your skill to the right home. Keep it documented. Make it shine.

---

*Built with love by Reflecter Labs* 💜
