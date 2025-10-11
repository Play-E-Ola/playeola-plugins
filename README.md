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

## Available Plugins

### Phase 1: Core Foundation ✅ (Available Now)

**Plugin:** `playeola-foundation`

**What's Included:**
- `code-review-expert` agent - Comprehensive code review, enforces Claude.md rules
- `documentation-orchestrator` agent - Keeps docs in sync with code
- `/smart-commit` command - Code review → fix → update docs → commit
- Smart hooks - Auto-suggestions, safety checks

**Installation:**
```bash
/plugin install playeola-foundation@playeola-marketplace
```

**Use Cases:**
- Automated code quality checks before committing
- Documentation always stays current
- Enforces project-specific rules from Claude.md
- Prevents committing secrets or sensitive data

[View Plugin Details](./playeola-foundation/README.md)

---

### Phase 2: Gaming & Microservices 🚧 (Coming Soon)

**Plugin:** `playeola-gaming` (In Development)

**What Will Be Included:**
- `slot-game-specialist` agent - Slot mechanics, Phaser, game math
- `microservices-orchestrator` agent - Service communication, API validation
- `/sync-service-docs` command - Cross-service documentation sync

**Target Release:** Week 2

---

### Phase 3: Analytics & Planning 🚧 (Coming Soon)

**Plugin:** `playeola-analytics` (In Development)

**What Will Be Included:**
- `analytics-champion` agent - Dashboard design, data validation
- `feature-architect` agent - Brainstorming, specs, planning
- `/implement-analytics` command - Scaffold dashboards/reports
- `/brainstorm-feature` command - Ideation to implementation

**Target Release:** Week 2-3

---

### Phase 4: Advanced Orchestration 🚧 (Planned)

**Plugin:** `playeola-advanced` (Planned)

**What Will Be Included:**
- `agent-coordinator` agent - Meta-orchestration
- `/create-pr` command - CTO-friendly PR generation
- `/orchestrate` command - Handle any complexity

**Target Release:** Week 3

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
│   ├── .claude-plugin/
│   │   └── plugin.json
│   ├── agents/
│   │   ├── code-review-expert.md
│   │   └── documentation-orchestrator.md
│   ├── commands/
│   │   └── smart-commit.md
│   ├── hooks/
│   │   └── hooks.json
│   └── README.md
├── playeola-gaming/                 (Phase 2 - coming soon)
├── playeola-analytics/              (Phase 3 - coming soon)
└── README.md                        (this file)
```

---

## Plugin Features by Phase

| Feature | Phase 1 | Phase 2 | Phase 3 | Phase 4 |
|---------|---------|---------|---------|---------|
| Code Review | ✅ | ✅ | ✅ | ✅ |
| Documentation Sync | ✅ | ✅ | ✅ | ✅ |
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

### v1.0.0 (Current)
- **playeola-foundation** plugin released
  - `code-review-expert` agent
  - `documentation-orchestrator` agent
  - `/smart-commit` command
  - Basic automation hooks

### Coming in v1.1.0 (Phase 2)
- **playeola-gaming** plugin
  - Gaming specialists
  - Microservices orchestration
  - Service documentation sync

### Coming in v1.2.0 (Phase 3)
- **playeola-analytics** plugin
  - Analytics workflows
  - Feature planning system
  - Brainstorming tools

### Coming in v2.0.0 (Phase 4)
- **playeola-advanced** plugin
  - Advanced orchestration
  - PR automation
  - Full ecosystem integration

---

## License

Internal use for Playeola projects.

---

**Built with ❤️ by Playeola for production-ready iGaming development**
