# claude-skills

Copia de respaldo de las skills de Claude Code.

| Carpeta | Origen | Instalar en |
| :--- | :--- | :--- |
| raíz (`*.md`, `gsd-*`, `notebooklm-mcp`, `synced/`) | `~/.claude/skills` (skills globales) | `~/.claude/skills` |
| `project-skills/` | `.claude/skills` de proyecto, instaladas con `npx skills` (ver `project-skills/skills-lock.json`) | `<proyecto>/.claude/skills` |

## Restaurar

```powershell
# Globales
Copy-Item -Recurse -Force .\* "$HOME\.claude\skills" -Exclude project-skills,README.md,.git

# De proyecto (copia directa)
Copy-Item -Recurse -Force .\project-skills\* "<proyecto>\.claude\skills" -Exclude skills-lock.json

# O reinstalar desde las fuentes originales (versiones actuales)
Copy-Item .\project-skills\skills-lock.json "<proyecto>\"
cd "<proyecto>"; npx skills experimental_install
```

`synced/` lo gestiona Claude Desktop (skills de Anthropic sincronizadas); no editar a mano.

Nota de Windows: algunas rutas superan 260 caracteres. Antes de clonar: `git config --global core.longpaths true`.
