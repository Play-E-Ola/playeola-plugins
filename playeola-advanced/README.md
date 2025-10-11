# Playeola Advanced Plugin

**Phase 4: Advanced Orchestration** - Meta-agent coordination, intelligent workflow routing, and comprehensive PR automation for Playeola's iGaming development stack.

## What's Included

### Agents

#### `agent-coordinator`
Meta-orchestrator that coordinates all agents from Phases 1-3.

**Capabilities:**
- Complex task analysis and classification
- Intelligent agent selection and routing
- Multi-agent workflow coordination
- Sequential and parallel execution management
- Dependency handling between tasks
- Progress tracking across complex workflows
- Error handling and recovery strategies
- Result aggregation from multiple agents

**When to Use:**
- Complex multi-domain tasks
- Tasks requiring multiple specialized agents
- Uncertain which agents to use
- Need coordinated workflow execution
- Handling end-to-end feature implementation

### Commands

#### `/orchestrate`
The ultimate workflow command that handles any complex task.

**What it does:**
1. **Analyzes Task** - Uses agent-coordinator to understand complexity and scope
2. **Plans Workflow** - Determines which agents needed and execution order
3. **Coordinates Execution** - Manages all agents working together
4. **Tracks Progress** - Provides real-time status updates
5. **Aggregates Results** - Combines outputs into unified summary

**When to Use:**
- Implementing complete features end-to-end
- Multi-domain tasks (gaming + services + analytics)
- Planning and implementing together
- Unsure how to approach a complex task
- Need full lifecycle support (plan → implement → test → doc)

**Example Tasks:**
- "Implement bonus buy feature with full validation and documentation"
- "Build player analytics dashboard with optimal performance"
- "Add progressive jackpot across all services"
- "Plan and implement sticky wilds feature"

#### `/create-pr`
Comprehensive pull request creation with quality checks.

**What it does:**
1. **Pre-PR Validation** - Checks git status, analyzes branch and commits
2. **Quality Checks** - Runs code-review-expert and documentation-orchestrator
3. **PR Description Generation** - Creates comprehensive, CTO-ready PR description
4. **Reviewer Selection** - Recommends reviewers based on changed files
5. **PR Creation** - Uses gh CLI to create PR with proper labels

**When to Use:**
- Ready to create pull request
- Want comprehensive PR description
- Need quality validation before PR
- Creating production-ready PRs
- Following best PR practices

### Hooks

Smart automation for advanced workflows:
- **Complex task detection** - Suggests `/orchestrate` for multi-domain work
- **PR readiness detection** - Suggests `/create-pr` when work complete
- **Multi-agent coordination hints** - Detects when multiple agents needed
- **Cross-phase workflow suggestions** - Hints when task spans all phases

## Installation

This plugin is installed via the Playeola marketplace:

```bash
# Add marketplace (if not already added)
/plugin marketplace add Play-E-Ola/playeola-plugins

# Install this plugin (requires Phases 1-3 to be useful)
/plugin install playeola-advanced@playeola-marketplace
```

**Note:** Phase 4 coordinates agents from Phases 1-3, so install those first for full functionality.

## Usage Examples

### Scenario 1: Complete Feature Implementation

```
You: /orchestrate Implement bonus buy feature with RTP validation

Claude: [invokes agent-coordinator]

Task Analysis:
- Complexity: Multi-phase
- Domains: Gaming, Microservices, Code Quality, Documentation
- Estimated: ~9 days

Execution Plan:
Phase 1: Planning
- feature-architect: Create implementation plan

Phase 2: Design
- slot-game-specialist: Design math model
- microservices-orchestrator: Design API contracts

Phase 3: Implementation
- [Guided implementation]

Phase 4: Validation
- slot-game-specialist: Validate RTP
- code-review-expert: Code review

Phase 5: Documentation
- documentation-orchestrator: Update docs

Proceed? yes

[Orchestration executes through all phases...]

Result:
✅ All phases complete
✅ RTP validated at 96.5%
✅ 0 critical issues
✅ All documentation updated

Next: Run /create-pr to create pull request
```

### Scenario 2: Production-Ready PR

```
You: /create-pr

Claude:
Pre-PR Validation:
- Branch: feature/ABC-123-bonus-buy ✓
- 15 files changed ✓
- No merge conflicts ✓

Quality Checks:
✅ code-review-expert: No critical issues
✅ documentation-orchestrator: All docs updated

Generating PR description...

PR Created! #456
Title: feat: add bonus buy feature to slot games

Description includes:
- Comprehensive summary
- Technical details
- Testing checklist
- Documentation updates
- Breaking changes (none)
- Links to ABC-123

Labels added: feature, backend, game-engine
Reviewers suggested: @game-team, @backend-leads

Next: Monitor CI/CD and address review comments
```

### Scenario 3: Analytics Dashboard with Full Lifecycle

```
You: /orchestrate Build game performance dashboard

Claude:
Task Analysis:
- Complexity: Complex
- Domains: Planning, Analytics, Code Quality, Documentation

Execution Plan:
Phase 1: Requirements
- feature-architect: Define scope

Phase 2: Design & Implementation
- analytics-champion: Design architecture
- Use /implement-analytics command

Phase 3: Optimization
- analytics-champion: Optimize queries
- code-review-expert: Review code

Proceed? yes

[Orchestration executes...]

✅ Phase 1: Requirements defined
   - Metrics: Spins, revenue, RTP, players
   - Time ranges with filters

✅ Phase 2: Dashboard implemented
   - TanStack Query + Recharts
   - Materialized views
   - Redis caching

✅ Phase 3: Optimized
   - Load time: <2 seconds
   - Database indexes added
   - Code review passed

Result: Production-ready analytics dashboard

Next: Run /create-pr or deploy to staging
```

### Scenario 4: Cross-Service Feature Planning

```
You: /orchestrate Plan progressive jackpot system

Claude:
Task Analysis:
- Complexity: High, multi-service
- Focus: Planning and specification
- Domains: Planning, Gaming, Microservices

Execution Plan:
Phase 1: Brainstorming
- Use /brainstorm-feature command

Phase 2: Technical Design
- microservices-orchestrator: Service architecture
- slot-game-specialist: Game integration

Phase 3: Documentation
- feature-architect: Create spec and plan

Proceed? yes

[Orchestration executes with user interaction...]

✅ Phase 1: Requirements defined
   - 4-tier jackpot system
   - New Jackpot Service needed
   - All games integrated

✅ Phase 2: Architecture designed
   - Service contracts defined
   - Event flow documented
   - Game integration planned

✅ Phase 3: Documentation created
   - Technical specification
   - 6-week implementation plan
   - Architecture decision record

Result: Complete spec ready for implementation

Files created:
- specs/progressive-jackpots.md
- plans/progressive-jackpots-implementation.md
- docs/architecture/ADR-001-jackpot-service.md

Next: Review with architecture team, then implement Phase 1
```

## Works With

Phase 4 coordinates ALL agents from previous phases:

### Phase 1 Agents (Foundation)
- **code-review-expert** - Code quality validation
- **documentation-orchestrator** - Documentation sync

### Phase 2 Agents (Gaming & Microservices)
- **slot-game-specialist** - Slot mechanics and Phaser
- **microservices-orchestrator** - Service coordination

### Phase 3 Agents (Analytics & Planning)
- **analytics-champion** - Dashboard and data expertise
- **feature-architect** - Feature planning and specs

### All Commands
Can invoke any command from Phases 1-3:
- `/smart-commit`
- `/sync-service-docs`
- `/implement-analytics`
- `/brainstorm-feature`

## Integration with Previous Phases

Phase 4 is the culmination of the entire plugin ecosystem:

**Builds on Phase 1 (Foundation):**
- Uses code-review-expert for quality
- Uses documentation-orchestrator for docs
- Enhances `/smart-commit` with orchestration

**Builds on Phase 2 (Gaming):**
- Coordinates slot-game-specialist for game features
- Uses microservices-orchestrator for services
- Extends `/sync-service-docs` capabilities

**Builds on Phase 3 (Analytics):**
- Leverages analytics-champion for dashboards
- Uses feature-architect for planning
- Integrates with `/implement-analytics` and `/brainstorm-feature`

**Adds Phase 4 Capabilities:**
- Meta-orchestration via agent-coordinator
- Intelligent task routing
- Multi-agent coordination
- Production-ready PR generation

**Recommendation:** Install ALL four plugins for maximum value:
```bash
/plugin install playeola-foundation@playeola-marketplace
/plugin install playeola-gaming@playeola-marketplace
/plugin install playeola-analytics@playeola-marketplace
/plugin install playeola-advanced@playeola-marketplace
```

## Key Features

### For Complex Projects
- End-to-end feature orchestration
- Intelligent workflow coordination
- Multi-domain task handling
- Automatic agent selection

### For Teams
- Production-ready PRs
- Comprehensive quality checks
- Consistent documentation
- Clear reviewer recommendations

### For Developers
- Simplified complex workflows
- Guided implementation
- Automatic coordination
- Clear next steps always provided

### For Managers
- CTO-ready pull requests
- Complete audit trail
- Professional documentation
- Quality assurance built-in

## When to Use Each Command

### Use `/orchestrate` when:
- Task is complex and spans multiple domains
- Unsure which agents to use
- Want end-to-end guidance
- Need coordinated workflow
- Implementing major features

### Use `/create-pr` when:
- Ready to submit work for review
- Want comprehensive PR description
- Need quality validation
- Creating production PRs
- Following best practices

### Use other commands for specific needs:
- Simple commit → `/smart-commit`
- Analytics only → `/implement-analytics`
- Planning only → `/brainstorm-feature`
- Service docs → `/sync-service-docs`

## Best Practices

1. **Use /orchestrate for complex tasks** - Let it coordinate the workflow
2. **Review execution plans** - Understand what will happen before proceeding
3. **Trust the agent selection** - agent-coordinator knows which agents to use
4. **Follow next steps** - Suggestions are based on what was accomplished
5. **Use /create-pr for all PRs** - Ensures quality and completeness
6. **Install all phases** - Phase 4 is most powerful with all agents available
7. **Let hooks guide you** - They'll suggest the right commands at right times

## Workflow Patterns

### Pattern 1: Feature Implementation
```
Idea → /orchestrate → Implementation → /create-pr → Review → Merge
```

### Pattern 2: Analytics Development
```
Requirements → /orchestrate (uses /implement-analytics) → Optimization → /create-pr
```

### Pattern 3: Planning Then Building
```
/orchestrate (planning focus) → Spec created → /orchestrate (implementation) → /create-pr
```

### Pattern 4: Quick PR
```
Changes made → /create-pr → PR created
```

## Advanced Capabilities

### Multi-Agent Coordination
agent-coordinator can:
- Run agents in parallel when independent
- Run agents sequentially when dependent
- Pass context between agents
- Handle errors gracefully
- Aggregate results intelligently

### Intelligent Task Analysis
Automatically determines:
- Task complexity (simple/complex/multi-phase)
- Required domains (code/gaming/services/analytics)
- Which agents are needed
- Optimal execution order
- Estimated effort

### Comprehensive PR Generation
Creates PRs with:
- Professional, CTO-ready descriptions
- Complete testing checklists
- Documentation references
- Breaking change warnings
- Issue linkage
- Reviewer recommendations
- Proper labels

## Troubleshooting

### /orchestrate Not Working
- Ensure Phases 1-3 are installed
- Check that required agents are available
- Verify task description is clear
- Try breaking down into smaller tasks

### /create-pr Issues
- Verify gh CLI is installed and authenticated
- Check you're not on main/master branch
- Ensure there are changes to commit
- Verify remote is configured

### Agent Coordination Failures
- Review execution plan before proceeding
- Check for specific agent errors
- Use manual agent invocation if needed
- Report issues for improvement

## Version

**v2.0.0** - Phase 4 release with advanced orchestration

## Part of Playeola Marketplace

This is the final phase of the Playeola plugin ecosystem:

- **Phase 1** ✅ `playeola-foundation` - Code review, docs, smart commit
- **Phase 2** ✅ `playeola-gaming` - Gaming & microservices specialists
- **Phase 3** ✅ `playeola-analytics` - Analytics & feature planning
- **Phase 4** ✅ `playeola-advanced` - Advanced orchestration (this plugin)

## Complete Ecosystem

With all four phases installed, you have:

**6 Specialized Agents:**
1. code-review-expert (Phase 1)
2. documentation-orchestrator (Phase 1)
3. slot-game-specialist (Phase 2)
4. microservices-orchestrator (Phase 2)
5. analytics-champion (Phase 3)
6. feature-architect (Phase 3)
7. agent-coordinator (Phase 4) ← Meta-orchestrator

**7 Powerful Commands:**
1. /smart-commit (Phase 1)
2. /sync-service-docs (Phase 2)
3. /implement-analytics (Phase 3)
4. /brainstorm-feature (Phase 3)
5. /orchestrate (Phase 4)
6. /create-pr (Phase 4)

**Smart Automation:**
- 30+ intelligent hooks across all phases
- Auto-suggestions at the right moments
- Context-aware workflow guidance

## Tips for Maximum Effectiveness

1. **Start with /orchestrate** - For any complex task, it will figure out the workflow
2. **End with /create-pr** - Always creates better PRs than manual creation
3. **Trust the coordination** - agent-coordinator has the full context
4. **Use all phases** - Each phase adds specialized expertise
5. **Follow suggestions** - Hooks know when commands would be helpful
6. **Review plans** - Always understand what will happen before proceeding
7. **Provide feedback** - Help improve workflows by noting pain points

---

**Built for production-grade iGaming development by Playeola**

The complete Playeola plugin ecosystem transforms Claude Code into the ultimate development assistant for TypeScript/Node.js iGaming projects. From code review to feature planning to production deployment - everything is orchestrated intelligently.

Install all four phases and experience the future of AI-assisted development. 🚀
