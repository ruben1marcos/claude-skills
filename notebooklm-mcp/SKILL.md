---
name: notebooklm-mcp
description: Instala y usa el MCP de NotebookLM / Gemini Notebook (paquete notebooklm-mcp-cli) para listar, consultar y gestionar cuadernos y fuentes desde Claude Code o Claude Desktop. Usar cuando el usuario mencione NotebookLM, Gemini Notebook, sus cuadernos o fuentes, o pida instalar/configurar esta integracion.
---
# NotebookLM MCP

Repositorio: https://github.com/jacob-bd/gemini-notebook-mcp-cli (paquete `notebooklm-mcp-cli`, MIT).
Usa APIs internas no documentadas de Google: puede romperse sin aviso y puede no cumplir sus terminos de servicio. Avisalo al usuario antes de instalar.

## Instalacion (Windows)
1. Instalar uv (instalador oficial de Astral):
   `powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"`
2. Instalar el paquete: `uv tool install notebooklm-mcp-cli` (crea `nlm` y `notebooklm-mcp` en `~/.local/bin`).
3. Registrar en Claude Code: `claude mcp add --scope user gemini-notebook-mcp "$HOME\.local\bin\notebooklm-mcp.exe"`
4. Registrar en Claude Desktop: agregar `"mcpServers": {"gemini-notebook-mcp": {"command": "<ruta>\notebooklm-mcp.exe"}}` en `%APPDATA%\Claude\claude_desktop_config.json` conservando el resto del archivo.
5. Reiniciar Claude Code / Desktop.

Script automatico equivalente: `scripts/instalar-notebooklm-mcp.ps1` del repo Claude_configuracion.

## Autenticacion (siempre la hace el usuario)
- Pedir al usuario que ejecute `nlm login` en una PowerShell NORMAL de su usuario (no administrador: el perfil se guarda en el home del usuario que ejecuta el comando) y elija la opcion 1 (protegido).
- Nunca pedir ni escribir credenciales de Google; nunca copiar cookies entre usuarios de Windows.

## Uso
- Listar cuadernos: `nlm notebook list`
- Con el MCP cargado, preferir sus herramientas sobre el CLI.
- Pedir confirmacion antes de borrar cuadernos o fuentes.
