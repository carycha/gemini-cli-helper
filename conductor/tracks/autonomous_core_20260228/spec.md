# Specification: Autonomous Agent Core (OpenClaw-like)

## Overview
Implement a comprehensive, autonomous agent extension for the Gemini CLI that mimics the capabilities of OpenClaw. This agent will feature a continuous ReAct loop, a local database for long-term memory, and the ability to self-expand by installing new tools and packages. It aims to achieve autonomous learning, error correction, and system optimization.

## Core Architecture
- **Pattern:** ReAct (Reasoning + Acting) Loop.
- **Cycle:**
  1. **Observe:** Gather context from the environment (shell, files, memory).
  2. **Reason:** Analyze the situation using the Gemini API and current memory.
  3. **Act:** Execute tools (Shell, File I/O, Web Search, Package Install).
  4. **Reflect:** Evaluate the outcome, update memory, and self-correct if necessary.
  5. **Repeat:** Continue until the goal is met or human intervention is requested.

## Functional Requirements
### 1. Autonomous Loop
- Implement a robust `while(true)` loop that maintains context across steps.
- Handle interruptions and resume capability.
- **Error Correction:** Automatically analyze tool output errors and retry with adjusted parameters or strategies.

### 2. Memory System
- **Storage:** Use a local database (SQLite via `better-sqlite3` or similar) to store:
  - **Episodic Memory:** Logs of past actions and outcomes.
  - **Semantic Memory:** Extracted knowledge, code snippets, and patterns.
  - **Procedural Memory:** Stored "skills" or workflows.
- **Retrieval:** Implement a mechanism to query relevant memory before taking action.

### 3. Self-Expansion & Tooling
- **Base Tools:** File System, Shell, Web Search (via API/scraping).
- **Package Management:** Ability to detect missing tools and run `npm install` or other commands to acquire them.
- **Skill Creation:** Ability to write new scripts or tool definitions and register them for future use.

### 4. Continuous Learning
- **Post-Task Analysis:** After completing a task, the agent must generate a summary and store "lessons learned" in the database.
- **Knowledge Graph:** (Optional for v1) Build a graph of relationships between project files and concepts.

## Non-Functional Requirements
- **Performance:** Database queries must be fast (<50ms).
- **Reliability:** The agent must not crash on tool failures; it must catch exceptions and log them.
- **Security:** Prompt for confirmation before executing high-risk commands (e.g., `rm -rf`, installing global packages).

## Technical Stack
- **Language:** TypeScript.
- **Runtime:** Node.js.
- **Database:** `better-sqlite3` or `sqlite`.
- **LLM:** Gemini API.

## Success Criteria
- The agent can take a high-level goal (e.g., "Research and set up a React project") and execute it without further human input.
- The agent successfully installs a missing npm package when it realizes it needs one.
- The agent remembers a preference or fact from a previous session (persisted in DB).
