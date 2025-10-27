# Playeola Foundation Plugin

**Phase 1: Core Foundation** - Essential code review, documentation, and smart commit workflows for TypeScript/Node.js development.

## What's Included

### Agents

#### `code-review-expert`
Comprehensive code review specialist for TypeScript/Node.js projects.

**Capabilities:**
- Enforces project-specific Claude.md rules
- Validates TypeScript best practices
- Identifies bugs, security issues, and anti-patterns
- Suggests specific fixes with code examples
- Adapts to each project's unique requirements

#### `documentation-orchestrator`
Documentation maintenance expert that keeps docs in sync with code.

**Capabilities:**
- Discovers all documentation in your project
- Updates docs when code changes (API docs, specs, plans)
- Ensures consistency across all documentation files
- Adapts to any documentation structure
- Maintains formatting and style

### Commands

#### `/smart-commit`
Intelligent commit workflow that ensures quality before committing.

**What it does:**
1. **Code Review** - Runs comprehensive review via `code-review-expert`
2. **Fix Issues** - Implements fixes for critical/important issues
3. **Update Docs** - Syncs documentation via `documentation-orchestrator`
4. **Create Commit** - Generates proper commit message and commits

#### `/optimize-docs`
Comprehensive documentation optimization workflow that proactively audits all project documentation.

**What it does:**
1. **Discover** - Finds all documentation files across the project
2. **Analyze** - Identifies obsolete files, outdated content, and structural issues
3. **Optimize** - Removes obsolete docs, updates outdated content, reorganizes structure
4. **Validate** - Ensures code examples work and references are accurate
5. **Summary** - Provides clear navigation guide for optimized documentation

**Use when:**
- Starting work on an unfamiliar project
- Documentation feels scattered or outdated
- Preparing for team onboarding
- Planning a major feature (need accurate context)

### Hooks

Smart automation that triggers at the right moments:
- Auto code review suggestions after edits
- Smart commit reminders when you're done
- Claude.md rules enforcement
- Secret commit prevention

## Installation

This plugin is installed via the Playeola marketplace:

```bash
# Add marketplace (if not already added)
/plugin marketplace add Play-E-Ola/playeola-plugins

# Install this plugin
/plugin install playeola-foundation@playeola-marketplace
```

## Usage

### Manual Invocation
```
Please review my code using the code-review-expert agent
Please update the documentation
```

### Workflow Commands
```
/smart-commit
/optimize-docs
```

**`/smart-commit`** will:
1. Review your code
2. Fix any issues
3. Update documentation
4. Create a quality commit

**`/optimize-docs`** will:
1. Audit all documentation
2. Identify obsolete/outdated files
3. Update and reorganize documentation
4. Ensure accuracy and improve navigation

## Works With

- **RGS** (Remote Game Server)
- **Game Engine** (Phaser-based)
- **Math Simulator**
- **Backoffice**
- **Website**
- Any TypeScript/Node.js project

## Project Adaptation

This plugin automatically adapts to each project:

- **Claude.md Rules**: Enforces project-specific rules if Claude.md exists
- **Documentation Structure**: Discovers and maintains your doc layout
- **Commit Style**: Matches your repository's commit conventions

## Version

**v1.0.0** - Initial release with core foundation features

## Part of Playeola Marketplace

This is Phase 1 of the Playeola plugin ecosystem. Future phases include:
- **Phase 2**: Gaming specialists & microservices orchestration
- **Phase 3**: Analytics workflows & feature planning
- **Phase 4**: Advanced orchestration & PR automation
