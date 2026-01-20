# Project Context

## Purpose
The **LLM Skills** project is a collection of specialized instructions ("skills") and resources designed to extend the capabilities of AI coding assistants like Claude, Gemini, and Qwen. It serves as a library of best practices, workflows, and automated scripts that enable compatible agents to perform complex, domain-specific tasks reliably.

## Tech Stack
- **Markdown**: Primary language for defining skills, instructions, and documentation (`.md`).
- **Python**: Used for automation scripts and tooling within skill directories (`.py`).
- **OpenSpec**: The standard for managing specifications, change proposals, and project lifecycle.

## Project Conventions

### Code Style
- **Markdown**: Follow standard GitHub Flavored Markdown (GFM). Use headers for structure and clear, concise language for instructions.
- **Python**: Adhere to PEP 8 guidelines. Scripts should be self-contained within their skill or the global `scripts` directory.

### Architecture Patterns
- **Skills Structure**: Each skill resides in its own directory under `skills/` and MUST contain a `SKILL.md` file as the entry point.
- **Resources**: Scripts and static assets for a skill should be placed in `scripts/` and `resources/` subdirectories within the skill folder.
- **Directives**: Use clear logical directives (e.g., "Always open...", "Use...") to guide agent behavior.

### Testing Strategy
- **Validation**: Use `openspec validate` to ensure changes conform to project standards.
- **Script Testing**: Python scripts should include basic assertions or be verified manually via the `run_command` tool during development.

### Git Workflow
- **OpenSpec Protocol**: All significant changes (new skills, updates) must follow the OpenSpec workflow:
    1.  Create a proposal in `changes/<change-id>`.
    2.  Implement and validate using `openspec`.
    3.  Archive upon completion.

## Domain Context
- **Agentic Workflows**: Understanding how AI agents interpret instructions is key. Instructions should be unambiguous and context-aware.
- **Spec-Driven Development**: The project strictly adheres to "OpenSpec" for managing its own evolution.

## Important Constraints
- **Self-Contained**: Skills should minimize external dependencies to ensure portability across different agent environments.
- **Readability**: Documentation is consumed by both humans and LLMs; prioritize clarity and structure.

## External Dependencies
- **OpenSpec CLI**: Required for managing the project lifecycle (`openspec`).
- **fd / ripgrep**: Recommended for efficient file navigation and searching within the workspace.
