# forge2-qualifier-parth
nmg forge2 qualifier round 
# Dual-Agent Workspace Orchestrator (Hermes + OpenClaw)

An autonomous, multi-agent engineering workspace driven entirely by natural language via Slack. This system features a dual-agent architecture where an orchestrator agent delegates tasks to a specialized execution agent to plan, scaffold, and build full-stack applications.

---

## 🏗️ Architecture & Agent Stack

This workspace leverages a specialized multi-agent framework designed to separate high-level orchestration from local tool execution:

*   **Orchestrator Agent (Hermes):** Powered by native `gemini-2.5-flash` routed through a custom OpenAI-compatible proxy path to seamlessly manage secure authorization tokens. Hermes intercepts Slack commands, handles architectural planning, and structures task delegations.
*   **Execution Agent (OpenClaw):** Powered by Groq (`llama-3.3-70b-versatile`). OpenClaw acts as the local system runner—executing file modifications, terminal operations, and tracking file states via a centralized workspace state map.

### Data Model Framework
The workspace is initialized around the core system pillars:
*   `AGENTS.md` - Lifecycle configurations and operational rules for the dual loops.
*   `IDENTITY.md` - Persona constraints and tool-access boundaries for the runtime brains.
*   `SOUL.md` - Deep core memory and task persistence rules.
*   `USER.md` - Contextual preferences and global user constraints.
*   `openclaw-workspace-state.json` - Real-time state map utilized by the agents to track execution progress.

---

## 🚀 Getting Started & Configuration

### Prerequisites
* Mac with `hermes` and `openclaw` CLI layers installed.
* Slack Workspace with a custom app using Socket Mode and incoming webhooks enabled.

### 1. Agent Model Routing
To reproduce the authenticated workspace state, the orchestrator must pass validation via a custom endpoint to accommodate secure Google AI Studio tokens:

```bash
hermes model
# Select: Custom endpoint (enter URL manually)
# Base URL: [https://generativelanguage.googleapis.com/v1beta/openai](https://generativelanguage.googleapis.com/v1beta/openai)
# Model Name: gemini-2.5-flash
