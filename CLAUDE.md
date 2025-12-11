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

## Samples by Difficulty Level

### Beginner - Getting Started

**Python Agents:**
- `helloworld` - Minimal agent returning simple messages (LangGraph)
- `number_guessing_game` - Three-agent game without LLM (pure A2A SDK)
- `dice_agent_rest` / `dice_agent_grpc` - Simple dice rolling (ADK, different transports)
- `a2a-mcp-without-framework` - Raw A2A SDK usage without frameworks
- `adk_facts` - Simple fact generation (ADK intro)
- `travel_planner_agent` - Basic LLM integration (LangChain)

**Python Hosts:**
- `cli` - Command-line client with streaming support
- `beeai-chat` - Simple console chat using BeeAI Framework
- `multiagent` - Minimal ADK-based foundation

**.NET:**
- `BasicA2ADemo` - Echo and calculator agents demonstrating core A2A patterns

### Intermediate - Feature-Rich Single Agents

**Python Agents:**
- `langgraph` - Currency exchange with streaming, multi-turn, webhooks (LangGraph)
- `crewai` - Text-to-image generation with caching (CrewAI)
- `llama_index_file_chat` - File upload, parsing, QA with citations (LlamaIndex)
- `adk_expense_reimbursement` - Form handling and validation (ADK)
- `semantickernel` - Plugin architecture with streaming (Semantic Kernel)
- `marvin` - Structured data extraction with persistence (Marvin)
- `analytics` - Chart generation from natural language (CrewAI + Matplotlib)
- `veo_video_gen` - Video generation with GCS storage (ADK + VEO)
- `github-agent` - GitHub API integration with function calling

**Java Agents:**
- `content_writer` - LLM-powered content generation (Quarkus + LangChain4j)
- `content_editor` - Content polishing and refinement
- `weather_mcp` - External API integration via MCP
- `dice_agent_multi_transport` - Multi-transport support (gRPC + JSON-RPC)

**JavaScript Agents:**
- `movie-agent` - TMDB API integration (Genkit)
- `coder` - Code file generation as artifacts
- `content-editor` - Content editing in TypeScript

**Go:**
- `server` / `client` - JSON-RPC 2.0 protocol implementation with SSE
- `models` - Type-safe data structures

**.NET:**
- `A2ACliDemo` - Secure CLI command execution with whitelisting
- `A2ASemanticKernelDemo` - AI-powered text processing (summarization, sentiment, translation)

**Python Hosts:**
- `a2a_gui` - Web-based GUI with FastAPI and Google Cloud auth

### Advanced - Multi-Agent & Enterprise

**Python Agents:**
- `ag2` - Code review with MCP tool integration (AG2 framework)
- `any_agent_adversarial_multiagent` - Adversarial agent simulation
- `a2a_telemetry` - OpenTelemetry + Jaeger distributed tracing
- `a2a_mcp` - Complete travel system with dynamic agent discovery via MCP registry
- `airbnb_planner_multiagent` - Multi-agent coordination with Gradio UI
- `azureaifoundry_sdk` - Azure AI Foundry integration (3 examples including multi-agent with Semantic Kernel)
- `mindsdb` - Enterprise federated data queries with natural language SQL
- `headless_agent_auth` - Auth0 CIBA authentication flow

**Java Agents:**
- `magic_8_ball_security` - OAuth2 Keycloak authentication + multi-transport

**Python Hosts:**
- `a2a_multiagent_host` - Advanced orchestration with traceability extension
- `content_creation` - Cross-language pipeline (Python + Java + TypeScript)
- `weather_and_airbnb_planner` - Multi-agent with MCP + LangGraph

## Samples by Feature

### Streaming & Real-time
- `langgraph`, `llama_index_file_chat`, `semantickernel`, `analytics` (Python)
- Go `server`/`client` (SSE support)

### Multi-turn Conversations
- `langgraph`, `llama_index_file_chat`, `semantickernel`, `marvin`, `ag2`, `travel_planner_agent` (Python)

### File Handling
- `llama_index_file_chat` (upload & parsing)
- `veo_video_gen` (GCS storage)
- `cli` (file attachments)

### Tool/Function Calling
- `langgraph`, `ag2`, `semantickernel`, `github-agent`, `beeai-chat` (Python)

### MCP (Model Context Protocol) Integration
- `ag2` (mypy tools), `a2a_mcp` (agent registry), `airbnb_planner_multiagent`, `weather_mcp` (Java), `azureaifoundry_sdk` (Python)

### Multi-Agent Orchestration
- `a2a_mcp`, `airbnb_planner_multiagent`, `content_creation`, `weather_and_airbnb_planner`, `a2a_multiagent_host` (Python)
- `azureaifoundry_sdk/multi_agent` (Python)

### Authentication & Security
- `magic_8_ball_security` (OAuth2 Keycloak) (Java)
- `headless_agent_auth` (Auth0 CIBA) (Python)
- `A2ACliDemo` (command whitelisting) (.NET)

### Observability & Tracing
- `a2a_telemetry` (Jaeger + OpenTelemetry) (Python)
- `a2a_multiagent_host` (traceability extension) (Python)

### Cross-Language Systems
- `content_creation` (Python + Java + TypeScript orchestration)
- `weather_and_airbnb_planner` (Python + Java)

### Different Transport Protocols
- `dice_agent_grpc` vs `dice_agent_rest` (gRPC vs REST)
- `dice_agent_multi_transport` (unified gRPC + JSON-RPC)
- `magic_8_ball_security` (JSON-RPC + REST + gRPC)

### Web UI
- `adk_expense_reimbursement` (forms), `airbnb_planner_multiagent` (Gradio), `content_creation` (Gradio), `weather_and_airbnb_planner` (Gradio), `a2a_gui` (FastAPI), `demo/ui` (Mesop)

### Cloud Deployment
- `adk_cloud_run` (Google Cloud Run with AlloyDB)
- `veo_video_gen` (Vertex AI + GCS)
- `azureaifoundry_sdk` (Azure AI Foundry)

## Recommended Learning Path

1. **Start Here (Beginner):**
   - Python: `helloworld` or `number_guessing_game` → `cli` host
   - .NET: `BasicA2ADemo`
   - Goal: Understand basic A2A message flow

2. **Learn Frameworks (Intermediate):**
   - Python: Try `langgraph` (streaming, multi-turn) or `crewai` (image generation)
   - Explore different frameworks: `semantickernel`, `ag2`
   - Goal: See how different frameworks integrate with A2A

3. **Add Advanced Features (Intermediate):**
   - File handling: `llama_index_file_chat`
   - Forms: `adk_expense_reimbursement`
   - External APIs: `github-agent`, `weather_mcp` (Java)
   - Goal: Build feature-rich single agents

4. **Multi-Agent Systems (Advanced):**
   - Start: `a2a_multiagent_host` (basic orchestration)
   - MCP integration: `a2a_mcp` (agent registry)
   - Cross-language: `content_creation` (Python + Java + TypeScript)
   - Goal: Build coordinated multi-agent systems

5. **Production Patterns (Advanced):**
   - Security: `magic_8_ball_security`, `headless_agent_auth`
   - Observability: `a2a_telemetry` (Jaeger tracing)
   - Cloud deployment: `adk_cloud_run`, `azureaifoundry_sdk`
   - Goal: Production-ready agent systems

## Python Development

**Prerequisites:**
- Python 3.12 or higher (check `.python-version` in `samples/python/`)
- [UV](https://docs.astral.sh/uv/) for dependency management

**Workspace structure:**
- Root `pyproject.toml` defines a UV workspace with members organized by difficulty level
- Python samples are in `samples/python/agents/{beginner,intermediate,advanced}/` and `samples/python/hosts/{beginner,intermediate,advanced}/`
- Each agent/host is a separate UV package with its own `pyproject.toml`

**Running agents and hosts:**
```bash
# Run an agent (starts A2A server)
cd samples/python/agents/<difficulty>/<agent-name>
uv run .

# Run a host (starts A2A client)
cd samples/python/hosts/<difficulty>/<host-name>
uv run .
```

**Example workflow:**
```bash
# Terminal 1: Start an agent
cd samples/python/agents/intermediate/langgraph
uv run .

# Terminal 2: Start the CLI host
cd samples/python/hosts/beginner/cli
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
