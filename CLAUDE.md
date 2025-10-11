# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is the **Playeola Plugin Marketplace** - a Claude Code plugin marketplace for Playeola's iGaming development stack. It contains 4 plugins that provide specialized agents, workflow commands, and automation hooks for TypeScript/Node.js development.

**Target Projects:**
- RGS (Remote Game Server) - Game runtime & slot engine microservices
- Game Engine - Phaser-based slot games
- Math Simulator - RTP calculations and game math validation
- Backoffice - Administration platform with analytics
- Website - Public-facing platform

## Code Search and Navigation - ChunkHound MCP ⚠️ HIGHEST PRIORITY

**ALWAYS use ChunkHound MCP for code search and navigation**

ChunkHound provides semantic search powered by local Ollama embeddings and must be your first choice for:
- Finding where functions or classes are implemented
- Locating service files, API routes, or components
- Searching for similar code patterns
- Understanding code dependencies and relationships
- Discovering project structure and architecture

**When to use ChunkHound:**
- Before using grep, glob, or manual file searching
- When analyzing codebases or understanding architecture
- When looking for specific implementations
- When exploring unfamiliar code

**Do NOT use grep/glob/find when ChunkHound can answer the question.**

ChunkHound understands semantic meaning, making it superior for code discovery tasks. This is the most important tool usage rule in the Playeola ecosystem.

## Architecture

### Plugin Structure

Each plugin follows a consistent structure:

```
plugin-name/
├── plugin.json              # Plugin manifest (name, version, description)
├── agents/                  # Specialized agent definitions (.md files)
├── commands/                # Workflow command definitions (.md files)
├── hooks/                   # Automation hooks (hooks.json)
└── README.md               # Plugin documentation
```

### Marketplace Manifest

`.claude-plugin/marketplace.json` - Central registry that lists all available plugins with their sources, versions, and descriptions.

### Four-Phase Plugin System

The marketplace is organized into 4 progressive phases, each building on the previous:

**Phase 1: playeola-foundation (v1.0.0)**
- Foundation layer for code quality and documentation
- Agents: `code-review-expert`, `documentation-orchestrator`
- Commands: `/smart-commit`

**Phase 2: playeola-gaming (v1.1.0)**
- Gaming and microservices expertise
- Agents: `slot-game-specialist`, `microservices-orchestrator`
- Commands: `/sync-service-docs`

**Phase 3: playeola-analytics (v1.2.0)**
- Analytics and feature planning capabilities
- Agents: `analytics-champion`, `feature-architect`
- Commands: `/implement-analytics`, `/brainstorm-feature`

**Phase 4: playeola-advanced (v2.0.0)**
- Meta-orchestration and PR automation
- Agents: `agent-coordinator`
- Commands: `/orchestrate`, `/create-pr`

### Agent Coordination Pattern

Phase 4's `agent-coordinator` acts as a meta-orchestrator that can invoke and coordinate ALL agents from Phases 1-3. It:
- Analyzes task complexity and required domains
- Routes tasks to appropriate specialized agents
- Manages sequential and parallel agent execution
- Aggregates results from multiple agents
- Handles cross-phase workflows

## File Type Conventions

### Agent Files (agents/*.md)

Agent definitions use markdown with YAML frontmatter:
```markdown
---
name: agent-name
description: Brief description
auto_invoke: false
---

# Agent Title

[Agent documentation and capabilities]
```

**Key Sections:**
- Core Responsibilities
- Workflow (when invoked)
- Specialized Knowledge Areas
- Integration with Other Agents
- Output Format
- Example Scenarios

### Command Files (commands/*.md)

Command definitions use markdown with YAML frontmatter:
```markdown
---
name: command-name
description: Brief description
---

[Command workflow and usage documentation]
```

**Key Sections:**
- Workflow (phase-by-phase execution)
- Usage Examples
- Integration points
- Best Practices

### Hook Files (hooks/hooks.json)

Hooks define automation triggers:
```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "name": "hook-name",
            "description": "What it does",
            "event": "user-prompt-submit",
            "condition": "regex or logic",
            "action": {
              "type": "suggestion|invoke-agent|warning",
              "message": "Message to user"
            }
          }
        ]
      }
    ]
  }
}
```

## Development Workflow

### Adding a New Agent

1. Create `plugin-name/agents/agent-name.md`
2. Follow the agent file conventions above
3. Define agent capabilities, workflow, and integration points
4. Update plugin README to document the new agent

### Adding a New Command

1. Create `plugin-name/commands/command-name.md`
2. Follow the command file conventions above
3. Define workflow phases and execution steps
4. Specify which agents the command invokes
5. Update plugin README to document the new command

### Adding a New Plugin

1. Create plugin directory: `plugin-name/`
2. Create `plugin.json` with name, version, description
3. Create subdirectories: `agents/`, `commands/`, `hooks/`
4. Create `README.md` with comprehensive plugin documentation
5. Add plugin entry to `.claude-plugin/marketplace.json`
6. Update main `README.md` to list the new plugin

### Version Numbering

- **Phase 1:** v1.0.0 (Foundation)
- **Phase 2:** v1.1.0 (Gaming & Microservices)
- **Phase 3:** v1.2.0 (Analytics & Planning)
- **Phase 4:** v2.0.0 (Advanced - major version bump)

Increment appropriately based on scope of changes.

## Key Design Principles

### Agent Specialization

Each agent has a focused domain of expertise:
- Avoid overlap between agent capabilities
- Agents should be composable (work well together)
- Agent-coordinator orchestrates cross-domain workflows

### Project Adaptation

All agents must adapt to the target project:
- Read project's `Claude.md` if it exists
- Discover documentation structure (don't assume)
- Match existing commit message style
- Respect project patterns and conventions

### Progressive Enhancement

Plugins build on each other:
- Phase 1 provides foundation (code review, docs)
- Phase 2 adds domain expertise (gaming, services)
- Phase 3 adds planning capabilities (analytics, specs)
- Phase 4 adds orchestration (meta-coordination, PR automation)

Users can install any combination, but Phase 4 requires Phases 1-3 for full functionality.

### Hook Philosophy

Hooks should:
- Suggest, not force
- Trigger at the right moments
- Provide value without being intrusive
- Be disabled by default if experimental

## Testing Plugins

When testing plugin changes:

1. **Local Testing:** Test in a non-critical Playeola project first
2. **Agent Testing:** Manually invoke agents to verify behavior
3. **Command Testing:** Run commands and verify full workflow execution
4. **Hook Testing:** Trigger hook conditions and verify suggestions appear
5. **Integration Testing:** Test agent coordination in Phase 4

## Documentation Standards

### Agent Documentation

Must include:
- Clear capability description
- Workflow breakdown (step-by-step)
- Integration with other agents
- Example scenarios with real use cases
- Output format specification

### Command Documentation

Must include:
- Phase-by-phase workflow
- Which agents are invoked
- Example usage with realistic scenarios
- Error handling and edge cases
- Integration with other commands

### README Files

Plugin READMEs must include:
- What's included (agents, commands, hooks)
- Installation instructions
- Usage examples
- Integration with other phases
- When to use each capability

## Commit Message Style

Follow conventional commits format:
```
<type>: <short summary>

<detailed description>

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

**Types:** feat, fix, docs, refactor, test, chore

## Repository Management

- **Marketplace:** GitHub repository at `Play-E-Ola/playeola-plugins`
- **Installation:** Users add with `/plugin marketplace add Play-E-Ola/playeola-plugins`
- **Internal Tool:** For Playeola team use
- **Version Control:** All changes must be committed and documented

## Claude Code Integration

This repository IS a Claude Code plugin marketplace. When working here:
- Changes affect how Claude Code operates in Playeola projects
- Agent definitions are consumed by Claude Code's plugin system
- Commands become slash commands in Claude Code
- Hooks automate suggestions in Claude Code sessions

## Important Notes

- **Agent Autonomy:** Agents should be autonomous - they receive a task and complete it without back-and-forth
- **Context Passing:** When agent-coordinator invokes agents, pass relevant context and previous results
- **Error Handling:** All workflows should handle errors gracefully and provide recovery options
- **User Control:** Users should be able to approve plans before execution (especially in `/orchestrate`)
- **Documentation Sync:** Whenever agents or commands change, update all relevant README files
