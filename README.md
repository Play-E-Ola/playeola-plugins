# Playeola Plugins

Official Claude Code plugin collection for Playeola's iGaming development stack. This plugin ecosystem provides specialized agents, workflow automation commands, and intelligent hooks to accelerate TypeScript/Node.js development across all Playeola products.

## Overview

Playeola Plugins is designed to work seamlessly across your entire product suite:
- **RGS** (Remote Game Server) - Game runtime & slot engine microservices
- **Game Engine** - Phaser-based slot games
- **Math Simulator** - RTP calculations and game math validation
- **Backoffice** - Administration platform with analytics
- **Website** - Public-facing platform

### What's Included

**Phase 1 (Current):**
- 2 Specialized Agents (code review, documentation)
- 1 Workflow Command (/smart-commit)
- Smart Hooks (auto-invocation, suggestions, safety checks)

**Coming Soon:**
- Phase 2: Gaming specialists & microservices orchestration
- Phase 3: Analytics workflows & feature planning
- Phase 4: Advanced orchestration & PR automation

## Installation

### Prerequisites
- Claude Code CLI installed
- Git repository initialized
- Node.js project with TypeScript

### Install Plugin

```bash
# Clone this repository
git clone https://github.com/playeola/playeola-plugins.git

# Install the plugin (from your project directory)
claude plugins install /path/to/playeola-plugins

# Verify installation
claude plugins list
```

### Enable Plugin

```bash
# Enable for current project
claude plugins enable playeola-plugins

# Or enable globally (for all projects)
claude plugins enable playeola-plugins --global
```

## Phase 1: Core Foundation

### Agents

#### `code-review-expert`
Comprehensive code review specialist for TypeScript/Node.js projects.

**Capabilities:**
- Enforces project-specific Claude.md rules
- Validates TypeScript best practices
- Identifies bugs, security issues, and anti-patterns
- Suggests specific fixes with code examples
- Adapts to each project's unique requirements

**Usage:**
```
Please review my code changes using the code-review-expert agent
```

**Auto-invoked:**
- By `/smart-commit` command before committing
- When "follow Claude.md rules" is mentioned
- After significant code edits (via hooks)

---

#### `documentation-orchestrator`
Documentation maintenance expert that keeps docs in sync with code.

**Capabilities:**
- Discovers all documentation in your project
- Updates docs when code changes (API docs, specs, plans)
- Ensures consistency across all documentation files
- Adapts to any documentation structure
- Maintains formatting and style

**Usage:**
```
Please update the documentation to reflect my recent changes
```

**Auto-invoked:**
- By `/smart-commit` command before committing
- After API changes (via hooks)
- When documentation updates are needed

---

### Commands

#### `/smart-commit`
Intelligent commit workflow that ensures quality before committing.

**What it does:**
1. **Code Review** - Runs comprehensive review via `code-review-expert`
2. **Fix Issues** - Implements fixes for critical/important issues
3. **Update Docs** - Syncs documentation via `documentation-orchestrator`
4. **Create Commit** - Generates proper commit message and commits

**Usage:**
```
/smart-commit
```

**Example Output:**
```markdown
### Phase 1: Code Review
✅ No critical issues
🟡 1 important issue fixed (missing error handling)
🟢 2 suggestions noted

### Phase 2: Documentation
Updated: docs/api/games.md, README.md

### Phase 3: Commit
Committed: "fix: add error handling to games API endpoint"

Ready to push!
```

**Benefits:**
- Never forget to update documentation
- Catch issues before they reach production
- Consistent, high-quality commits
- Saves time on repetitive tasks

---

### Hooks

Smart automation that triggers at the right moments.

**Active Hooks:**

1. **Auto Code Review Suggestion**
   - Triggers after significant code edits
   - Suggests running code review or /smart-commit

2. **Smart Commit Reminder**
   - Triggers when you say "done", "finished", or "ready to commit"
   - Reminds you to use /smart-commit

3. **Claude.md Rules Enforcer**
   - Triggers when you mention "follow rules" or "check Claude.md"
   - Auto-invokes code-review-expert

4. **Secret Commit Prevention**
   - Triggers before committing .env, credentials files
   - Warns about potential secret leaks

**Future Hooks (Phase 2-3):**
- Auto-invoke gaming specialists for slot-related work
- Auto-invoke microservices orchestrator for service changes
- Auto-invoke analytics champion for dashboard work
- API documentation sync reminders

---

## Usage Examples

### Example 1: Making Changes & Committing

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
fix: add pagination to games API endpoint

Added page and limit query parameters for paginated results.
Updated API documentation with examples.
```

### Example 2: Following Project Rules

```
You: Make sure this follows our Claude.md rules

Claude: [code-review-expert agent auto-invoked]

I'll review your code against the Claude.md rules...

Found 2 violations:
1. Missing ChunkHound usage for code search (Claude.md requires it)
2. Business logic in API route (should be in service layer)

Should I fix these issues?
```

### Example 3: Documentation Update

```
You: I changed the authentication flow in the backoffice

Claude: [makes changes]

Hook triggered: API changes detected. Consider updating documentation.

You: Yes, update the docs

Claude: [documentation-orchestrator agent invoked]

Updated documentation:
- docs/api/auth.md (new authentication flow)
- README.md (updated setup instructions)
- Claude.md (updated auth patterns section)
```

---

## Project Structure

```
playeola-plugins/
├── .claude-plugin/
│   └── plugin.json           # Plugin manifest
├── agents/
│   ├── code-review-expert.md           # Code review specialist
│   └── documentation-orchestrator.md   # Documentation maintainer
├── commands/
│   └── smart-commit.md       # Smart commit workflow
├── hooks/
│   └── hooks.json           # Automation hooks
└── README.md                # This file
```

---

## Configuration

### Project-Specific Adaptation

This plugin automatically adapts to each project:

**Claude.md Rules:**
- If `Claude.md` exists, `code-review-expert` enforces those rules
- If not, applies general TypeScript/Node.js best practices

**Documentation Structure:**
- Discovers your project's documentation layout
- Maintains whatever structure you use
- No assumptions about specific files

**Commit Style:**
- Matches existing commit message style in your repo
- Adapts to your team's conventions

### Customization

#### Modify Hooks

Edit `hooks/hooks.json` to customize automation:

```json
{
  "name": "your-custom-hook",
  "event": "user-prompt-submit",
  "condition": "message.includes('custom trigger')",
  "action": {
    "type": "invoke-agent",
    "agent": "code-review-expert"
  }
}
```

#### Adjust Agent Behavior

Edit agent markdown files to modify instructions:
- `agents/code-review-expert.md` - Change review criteria
- `agents/documentation-orchestrator.md` - Adjust doc update logic

---

## Roadmap

### Phase 2: Gaming & Microservices (Week 2)
- `slot-game-specialist` - Slot mechanics, Phaser, game math
- `microservices-orchestrator` - Service communication, API validation
- `/sync-service-docs` - Cross-service documentation sync

### Phase 3: Analytics & Planning (Week 2-3)
- `analytics-champion` - Dashboard design, data validation
- `feature-architect` - Brainstorming, specs, planning
- `/implement-analytics` - Scaffold dashboards/reports
- `/brainstorm-feature` - Ideation to implementation pipeline

### Phase 4: Advanced Orchestration (Week 3)
- `agent-coordinator` - Meta-orchestration for complex tasks
- `/create-pr` - CTO-friendly PR generation
- `/orchestrate` - Handle any complexity

---

## Best Practices

### When to Use /smart-commit
- ✅ After completing a feature or fix
- ✅ Before creating a pull request
- ✅ When you've made multiple related changes
- ✅ Anytime you want quality assurance

### When to Invoke Agents Manually
- Use `code-review-expert` for pre-implementation review
- Use `documentation-orchestrator` for doc-only updates
- Let `/smart-commit` handle both automatically

### Working with Multiple Projects
- Plugin adapts to each project automatically
- No configuration needed between projects
- Claude.md in each project defines project-specific rules

---

## Troubleshooting

### Plugin Not Loading
```bash
# Check plugin status
claude plugins list

# Reinstall if needed
claude plugins uninstall playeola-plugins
claude plugins install /path/to/playeola-plugins
```

### Hooks Not Triggering
- Check `hooks/hooks.json` for `"enabled": false`
- Verify hook conditions match your usage
- Some hooks require Phase 2/3 agents

### Agent Not Found
- Verify agent exists in `agents/` directory
- Check `plugin.json` has correct agent path
- Ensure agent name matches in commands/hooks

---

## Contributing

This is an internal Playeola tool, but improvements are welcome:

1. Test changes in a development project first
2. Update documentation if behavior changes
3. Add hooks for new automation opportunities
4. Create issues for bugs or feature requests

---

## Support

**Questions or issues?**
- Check Claude Code docs: https://docs.claude.com/claude-code
- Review agent markdown files for detailed behavior
- Test in a non-critical project first

---

## License

Internal use for Playeola projects.

---

## Version History

### v1.0.0 (Current - Phase 1)
- Initial release with core foundation
- `code-review-expert` agent
- `documentation-orchestrator` agent
- `/smart-commit` command
- Basic automation hooks

### Coming in v1.1.0 (Phase 2)
- Gaming specialists
- Microservices orchestration
- Service documentation sync

### Coming in v1.2.0 (Phase 3)
- Analytics workflows
- Feature planning system
- Brainstorming tools

### Coming in v2.0.0 (Phase 4)
- Advanced orchestration
- PR automation
- Full ecosystem integration

---

**Built with ❤️ by Playeola for production-ready iGaming development**
