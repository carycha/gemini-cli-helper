# Implementation Plan - Autonomous Agent Core

## Phase 1: Environment & Core Scaffolding
- [ ] Task: Initialize project structure (package.json, tsconfig.json, .gitignore)
- [ ] Task: Set up testing framework (Vitest) and linting (ESLint)
- [ ] Task: Write tests for Agent State definition
- [ ] Task: Implement Agent State interface and initial class
- [ ] Task: Write tests for basic Agent Loop skeleton
- [ ] Task: Implement basic Agent Loop (start, stop, step methods)
- [ ] Task: Conductor - User Manual Verification 'Environment & Core Scaffolding' (Protocol in workflow.md)

## Phase 2: Memory System (Local DB)
- [ ] Task: Install `better-sqlite3` and set up DB connection wrapper
- [ ] Task: Write tests for Memory Schema (migrations/init)
- [ ] Task: Implement Memory Schema initialization
- [ ] Task: Write tests for Memory CRUD operations (Episodic/Semantic logs)
- [ ] Task: Implement Memory CRUD operations
- [ ] Task: Conductor - User Manual Verification 'Memory System (Local DB)' (Protocol in workflow.md)

## Phase 3: Tool Registry & Basic Tools
- [ ] Task: Write tests for Tool Registry (registration, retrieval)
- [ ] Task: Implement Tool Registry and Base Tool class
- [ ] Task: Write tests for File System Tool (read/write/list)
- [ ] Task: Implement File System Tool
- [ ] Task: Write tests for Shell Command Tool (execute)
- [ ] Task: Implement Shell Command Tool
- [ ] Task: Conductor - User Manual Verification 'Tool Registry & Basic Tools' (Protocol in workflow.md)

## Phase 4: ReAct Logic & LLM Integration
- [ ] Task: Implement Gemini API Client wrapper (with mock for testing)
- [ ] Task: Design and Implement ReAct System Prompt templates
- [ ] Task: Write tests for ReAct Loop logic (parsing LLM response -> Action)
- [ ] Task: Implement ReAct Loop logic (Observe -> Reason -> Act -> Reflect)
- [ ] Task: Connect Agent Loop to Real LLM and Tools
- [ ] Task: Conductor - User Manual Verification 'ReAct Logic & LLM Integration' (Protocol in workflow.md)

## Phase 5: Self-Expansion & Advanced Capabilities
- [ ] Task: Write tests for Package Manager Tool (install/check)
- [ ] Task: Implement Package Manager Tool
- [ ] Task: Implement Error Correction logic (catch tool errors, feed back to LLM)
- [ ] Task: Implement "Post-Task Reflection" to save lessons to DB
- [ ] Task: Create End-to-End integration test for a complex scenario (e.g., "create a file and read it")
- [ ] Task: Conductor - User Manual Verification 'Self-Expansion & Advanced Capabilities' (Protocol in workflow.md)
