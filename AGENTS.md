# Instructions

This is a GitHub template repository for evaluating and recording how LLMs utilize the **MLIT Data Platform MCP Server**. Users create a new repository from this template and run research tasks against the MCP server.

## Project Structure & Architecture

- **Purpose**: Evaluate how LLMs use MCP server tools — which tools they select, in what order, and how effective each search strategy is.
- **Template Repository**: This repository is a template. Each evaluation creates a new repo from this template.
- **Core Configuration**: `.vscode/mcp.json` defines the MCP server connection for VS Code.
- **External Dependency**: The MCP server source code (`mlit-dpf-mcp`) resides in a separate local repository. The paths in `.vscode/mcp.json` must be updated to match the user's local environment.

## Key Files

| File | Purpose |
| ------ | --------- |
| `EXAMPLE-PROMPTS.md` | Prompt template for LLM-driven research tasks. Edit the "調査内容" section to define a research topic. |
| `.vscode/mcp.json` | VS Code MCP server configuration. Update `command` and `args` paths before use. |
| `.github/skills/mlit-dpf-mcp-server-research/SKILL.md` | Research skill definition with tool usage guides for complex data discovery. |

## Tech Stack

- **Configuration**: JSONC (JSON with comments)
- **Runtime**: Python (via external venv)
- **Protocol**: Model Context Protocol (MCP)
- **LLM Integration**: Compatible with any LLM supporting MCP (e.g., GPT-4, Claude, Llama 3)
