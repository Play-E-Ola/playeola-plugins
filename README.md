# Playeola Plugin Marketplace

Official Claude Code plugin marketplace for Playeola's iGaming development stack. This marketplace provides specialized agents, workflow automation commands, and intelligent hooks to accelerate TypeScript/Node.js development across all Playeola products.

## Overview

Playeola Plugin Marketplace is designed to work seamlessly across your entire product suite:
- **RGS** (Remote Game Server) - Game runtime & slot engine microservices
- **Game Engine** - Phaser-based slot games
- **Math Simulator** - RTP calculations and game math validation
- **Backoffice** - Administration platform with analytics
- **Website** - Public-facing platform

## Installation

### Step 1: Add Marketplace

From any Claude Code session in your project:

```bash
/plugin marketplace add Play-E-Ola/playeola-plugins
```

This connects your Claude Code to the Playeola plugin marketplace.

### Step 2: Browse & Install Plugins

```bash
# Browse available plugins
/plugin

# Or install directly by name
/plugin install playeola-foundation@playeola-marketplace
```

### Step 3: Verify Installation

```bash
/plugin list
```

You should see the installed plugins listed.

---

## Recommended Setup

### ChunkHound MCP (Highly Recommended)

All Playeola plugins are designed to use ChunkHound MCP for semantic code search. ChunkHound should be installed **in each Playeola project** where you use these plugins (RGS, Game Engine, Backoffice, etc.).

**Quick Setup:**
1. Install ChunkHound MCP in your project: [ChunkHound Quickstart Guide](https://chunkhound.github.io/quickstart/)
2. The plugins will automatically use ChunkHound for code discovery and navigation
3. Hooks will remind you if you use grep/glob instead of ChunkHound

**Why ChunkHound?**
- Semantic search understands code meaning, not just text matching
- Superior for finding implementations, dependencies, and architectural patterns
- Required for optimal agent performance in code discovery tasks

Note: ChunkHound is installed **per-project**, not in this marketplace repository.

---

## Available Plugins

### Phase 1: Core Foundation ✅ (Available Now)

**Plugin:** `playeola-foundation`

**What's Included:**
- `code-review-expert` agent - Comprehensive code review, enforces Claude.md rules
- `documentation-orchestrator` agent - Keeps docs in sync with code
- `/smart-commit` command - Code review → fix → update docs → commit
- `/optimize-docs` command - Audit all docs → remove obsolete → update → reorganize
- Smart hooks - Auto-suggestions, safety checks

**Installation:**
```bash
/plugin install playeola-foundation@playeola-marketplace
```

**Use Cases:**
- Automated code quality checks before committing
- Documentation always stays current
- Proactive documentation audits and optimization
- Enforces project-specific rules from Claude.md
- Prevents committing secrets or sensitive data

[View Plugin Details](./playeola-foundation/README.md)

---

### Phase 2: Gaming & Microservices ✅ (Available Now)

**Plugin:** `playeola-gaming`

**What's Included:**
- `slot-game-specialist` agent - Slot mechanics, Phaser, game math
- `microservices-orchestrator` agent - Service communication, API validation
- `/sync-service-docs` command - Cross-service documentation sync

**Installation:**
```bash
/plugin install playeola-gaming@playeola-marketplace
```

**Use Cases:**
- Slot game development with RTP validation
- Phaser optimization and performance
- Cross-service API coordination
- Breaking change management
- Service architecture guidance

[View Plugin Details](./playeola-gaming/README.md)

---

### Phase 3: Analytics & Planning ✅ (Available Now)

**Plugin:** `playeola-analytics`

**What's Included:**
- `analytics-champion` agent - Dashboard design, data validation, query optimization
- `feature-architect` agent - Brainstorming, specs, planning, task breakdown
- `/implement-analytics` command - Scaffold dashboards/reports
- `/brainstorm-feature` command - Ideation to implementation

**Installation:**
```bash
/plugin install playeola-analytics@playeola-marketplace
```

**Use Cases:**
- Building analytics dashboards
- Data visualization and reporting
- Feature planning and brainstorming
- Technical specification creation
- Implementation planning with estimates
- Progress tracking (SESSION_STATE.md style)

[View Plugin Details](./playeola-analytics/README.md)

---

### Phase 4: Advanced Orchestration ✅ (Available Now)

**Plugin:** `playeola-advanced`

**What's Included:**
- `agent-coordinator` agent - Meta-orchestration across all phases
- `/orchestrate` command - Ultimate workflow for complex tasks
- `/create-pr` command - Comprehensive PR generation with quality checks

**Installation:**
```bash
/plugin install playeola-advanced@playeola-marketplace
```

**Use Cases:**
- Complex multi-domain feature implementation
- End-to-end workflow coordination
- Intelligent agent selection and routing
- Production-ready pull request creation
- Multi-agent task coordination
- Comprehensive quality validation

[View Plugin Details](./playeola-advanced/README.md)

---

## Quick Start Example

After installing `playeola-foundation`:

```
You: I've updated the games API to add pagination

Claude: [makes changes]

You: /smart-commit

Claude:
### Code Review
✅ Changes look good
🟢 Suggestion: Add pagination examples to API docs

### Documentation
Updated: docs/api/games.md (added pagination documentation)

### Commit
feat: add pagination to games API endpoint

Added page and limit query parameters for paginated results.
Updated API documentation with examples.

🤖 Generated with Claude Code
```

---

## Marketplace Structure

```
playeola-plugins/                    (marketplace root)
├── .claude-plugin/
│   └── marketplace.json             (marketplace manifest)
├── playeola-foundation/             (Phase 1 plugin)
│   ├── plugin.json
│   ├── agents/
│   │   ├── code-review-expert.md
│   │   └── documentation-orchestrator.md
│   ├── commands/
│   │   └── smart-commit.md
│   ├── hooks/
│   │   └── hooks.json
│   └── README.md
├── playeola-gaming/                 (Phase 2 plugin)
│   ├── plugin.json
│   ├── agents/
│   │   ├── slot-game-specialist.md
│   │   └── microservices-orchestrator.md
│   ├── commands/
│   │   └── sync-service-docs.md
│   ├── hooks/
│   │   └── hooks.json
│   └── README.md
├── playeola-analytics/              (Phase 3 - coming soon)
└── README.md                        (this file)
```

---

## Plugin Features by Phase

| Feature | Phase 1 | Phase 2 | Phase 3 | Phase 4 |
|---------|---------|---------|---------|---------|
| Code Review | ✅ | ✅ | ✅ | ✅ |
| Documentation Sync | ✅ | ✅ | ✅ | ✅ |
| Documentation Optimization | ✅ | ✅ | ✅ | ✅ |
| Smart Commit | ✅ | ✅ | ✅ | ✅ |
| Slot Game Expertise | - | ✅ | ✅ | ✅ |
| Microservices Orchestration | - | ✅ | ✅ | ✅ |
| Analytics Workflows | - | - | ✅ | ✅ |
| Feature Planning | - | - | ✅ | ✅ |
| Advanced Orchestration | - | - | - | ✅ |
| PR Automation | - | - | - | ✅ |

---

## Benefits

### For Individual Developers
- Never forget to update documentation
- Catch issues before they reach production
- Consistent, high-quality commits
- Project-specific rule enforcement

### For Teams
- Centralized plugin distribution
- Consistent development practices across projects
- Easy onboarding for new team members
- Version-controlled plugin updates

### For Playeola Projects
- Specialized gaming expertise (slot mechanics, Phaser)
- Microservices integration support
- Analytics dashboard assistance
- Feature planning workflows

---

## Configuration

### Project-Specific Adaptation

All plugins automatically adapt to each project:

**Claude.md Rules:**
- If `Claude.md` exists, plugins enforce those rules
- If not, applies general TypeScript/Node.js best practices

**Documentation Structure:**
- Discovers your project's documentation layout
- Maintains whatever structure you use
- No assumptions about specific files

**Commit Style:**
- Matches existing commit message style in your repo
- Adapts to your team's conventions

### ChunkHound MCP Integration

All plugins are designed to work with ChunkHound MCP for semantic code search:
- **ChunkHound is the preferred tool for all code search operations**
- Agents use ChunkHound for code discovery and navigation before grep/glob
- Provides semantic search powered by local Ollama embeddings
- Hooks remind users when grep/glob is used instead of ChunkHound
- Superior results for code understanding and discovery tasks

---

## Troubleshooting

### Marketplace Not Found
```bash
# Make sure you're using the correct command
/plugin marketplace add Play-E-Ola/playeola-plugins

# Verify the repository is accessible
# Repository: https://github.com/Play-E-Ola/playeola-plugins
```

### Plugin Installation Fails
```bash
# Check available plugins in marketplace
/plugin

# Try installing with full marketplace name
/plugin install playeola-foundation@playeola-marketplace
```

### Hooks Not Triggering
- Some hooks are disabled by default until later phases
- Check plugin's `hooks/hooks.json` for `"enabled": false`
- Enable hooks manually if needed

---

## Support

**Questions or issues?**
- Check Claude Code docs: https://docs.claude.com/claude-code
- Review individual plugin READMEs for detailed behavior
- Test in a non-critical project first

---

## Contributing

This is an internal Playeola tool. Improvements welcome:

1. Test changes in a development project first
2. Update documentation if behavior changes
3. Add hooks for new automation opportunities
4. Submit PRs for review

---

## Version History

### v2.0.0 (Current)
- **playeola-advanced** plugin released 🎉
  - `agent-coordinator` agent - Meta-orchestration across all phases
  - `/orchestrate` command - Ultimate workflow for complex multi-domain tasks
  - `/create-pr` command - Comprehensive PR generation with quality checks
  - Advanced coordination hooks
  - Complete ecosystem integration
- **Playeola Plugin Marketplace now complete with all 4 phases!**

### v1.2.0
- **playeola-analytics** plugin released
  - `analytics-champion` agent - Dashboard design and analytics expertise
  - `feature-architect` agent - Feature planning and specifications
  - `/implement-analytics` command - Analytics implementation workflow
  - `/brainstorm-feature` command - Feature brainstorming and planning
  - Analytics and planning hooks

### v1.1.0
- **playeola-gaming** plugin released
  - `slot-game-specialist` agent
  - `microservices-orchestrator` agent
  - `/sync-service-docs` command
  - Gaming and microservices hooks

### v1.0.0
- **playeola-foundation** plugin released
  - `code-review-expert` agent
  - `documentation-orchestrator` agent
  - `/smart-commit` command
  - Basic automation hooks

---

## License

Internal use for Playeola projects.

---

**Built with ❤️ by Playeola for production-ready iGaming development**
