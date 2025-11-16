# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository contains multi-language samples demonstrating the Agent2Agent (A2A) Protocol. A2A enables agents to communicate and collaborate across different frameworks and languages.

**Related repositories:**
- [A2A Specification](https://github.com/a2aproject/A2A) - Protocol specification
- [a2a-python](https://github.com/a2aproject/a2a-python) - Python SDK
- [a2a-inspector](https://github.com/a2aproject/a2a-inspector) - UI inspection tool

## Repository Structure

```
a2a-samples/
├── samples/          # Language-specific samples
│   ├── python/      # Python agents and hosts
│   ├── java/        # Java agents (Quarkus + LangChain4j)
│   ├── go/          # Go implementation
│   ├── dotnet/      # .NET demos
│   └── js/          # JavaScript agents (Genkit)
├── extensions/      # A2A protocol extensions (timestamp, traceability, etc.)
├── demo/ui/         # Mesop web application demo
└── notebooks/       # Jupyter notebooks for quickstart/evaluation
```

### Key Concepts

- **Agents**: A2A servers that perform tasks using various frameworks (LangGraph, CrewAI, ADK, Semantic Kernel, etc.)
- **Hosts**: A2A clients that connect to and orchestrate one or more agents
- **Extensions**: Protocol extensions that augment base A2A types (e.g., timestamps, traceability)

## Python Development

**Prerequisites:**
- Python 3.12 or higher (check `.python-version` in `samples/python/`)
- [UV](https://docs.astral.sh/uv/) for dependency management

**Workspace structure:**
- Root `pyproject.toml` defines a UV workspace with members in `samples/python/agents/`, `samples/python/hosts/`, and `demo/ui`
- Each agent/host is a separate UV package with its own `pyproject.toml`

**Running agents and hosts:**
```bash
# Run an agent (starts A2A server)
cd samples/python/agents/<agent-name>
uv run .

# Run a host (starts A2A client)
cd samples/python/hosts/<host-name>
uv run .
```

**Example workflow:**
```bash
# Terminal 1: Start an agent
cd samples/python/agents/langgraph
uv run .

# Terminal 2: Start the CLI host
cd samples/python/hosts/cli
uv run .
```

**Formatting:**
- Use `./format.sh` from the repository root to format Python and Jupyter notebook files
- Supports `--all` flag to format all tracked files
- Supports `--unsafe-fixes` flag for Ruff unsafe fixes
- Tools used: autoflake, ruff (check + format), tensorflow_docs nbfmt (for notebooks)

**Testing:**
- Framework: pytest
- Run tests: `pytest` (in relevant directories)
- Test files typically named `test_*.py` or `*_test.py`

**Linting:**
- Configuration: `.ruff.toml` in repository root
- Run manually: `ruff check` and `ruff format`

## Java Development

**Prerequisites:**
- Maven for build management
- Java SDK (version varies by sample)

**Framework:**
- Quarkus with LangChain4j for most agent samples

**Build and run:**
```bash
cd samples/java/agents/<agent-name>
mvn clean install
mvn quarkus:dev
```

## Go Development

**Prerequisites:**
- Go 1.21 or later

**Project structure:**
```
samples/go/
├── server/    # Server implementation
├── client/    # Client implementation
└── models/    # Shared data structures
```

**Testing:**
```bash
cd samples/go
go test ./...
```

## .NET Development

**Prerequisites:**
- .NET 9.0 SDK

**Demos:**
- BasicA2ADemo - Core A2A concepts
- A2ACliDemo - CLI command execution agents
- A2ASemanticKernelDemo - AI-powered agents with Semantic Kernel

**Run:**
```bash
cd samples/dotnet/<demo-name>/<project-name>
dotnet run
```

## JavaScript Development

**Prerequisites:**
- Node.js and npm
- [Genkit](https://genkit.dev/) framework

**Setup and run:**
```bash
cd samples/js
npm install

# Set API key
export GEMINI_API_KEY=<your_api_key>

# Run agent
npm run agents:<agent-name>

# Run CLI client (in separate terminal)
npm run a2a:cli
```

## Demo Web Application

Location: `demo/ui/`

The demo is a [mesop](https://github.com/mesop-dev/mesop) web application that:
- Provides a chat interface to a Host Agent (Google ADK)
- Host Agent orchestrates requests to Remote Agents via A2A
- Dynamically add agents by entering their AgentCard address
- Renders complex content (images, forms, thought bubbles)

**Running:**
```bash
cd demo/ui

# Create .env file with credentials (GOOGLE_API_KEY or Vertex AI config)
uv run main.py  # Runs on port 12000
```

## Extensions

Extensions augment the base A2A protocol. Examples:
- **timestamp**: Adds timestamps to messages and artifacts
- **traceability**: Tracks message lineage
- **agp**: Agent Governance Protocol
- **secure-passport**: Security enhancement

Extension specifications are in `extensions/<name>/v*/`, with sample implementations in `extensions/<name>/samples/`.

## Security Considerations

**CRITICAL**: All sample code treats external agents as potentially untrusted entities. When building on these samples:

- **Validate and sanitize** all input from external agents (AgentCard, messages, artifacts, task statuses)
- **Prevent prompt injection** by sanitizing data before using it in LLM prompts
- **Handle credentials securely**
- Do not use sample code in production without proper security hardening

## CI/CD

**Linting:**
- GitHub Actions workflow: `.github/workflows/linter.yaml`
- Uses super-linter with specific validators disabled for Python (relies on format.sh instead)

**Code formatting enforcement:**
- PRs should run `./format.sh` to ensure consistent formatting
- Format script is git-aware and only formats changed files by default
