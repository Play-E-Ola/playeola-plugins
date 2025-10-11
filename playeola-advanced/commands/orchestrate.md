---
name: orchestrate
description: Ultimate workflow orchestration command - analyzes complex tasks, coordinates multiple agents across all phases, and delivers comprehensive end-to-end solutions
---

Execute the most powerful workflow in the Playeola plugin ecosystem. This command analyzes any complex task, determines the optimal workflow, and coordinates all necessary agents to deliver a complete solution.

## Overview

The `/orchestrate` command is your go-to for complex, multi-domain tasks that require coordination across code quality, gaming, microservices, analytics, and planning domains. It leverages the `agent-coordinator` to intelligently route work to the right specialists at the right time.

## Workflow

### Phase 1: Task Understanding

1. **Accept Task Description**
   ```
   User provides task in natural language:
   - "Implement bonus buy feature with full validation and documentation"
   - "Build player analytics dashboard with optimal performance"
   - "Add progressive jackpot across all services"
   - "Plan and implement sticky wilds feature"
   ```

2. **Parse and Clarify**
   ```
   Ask clarifying questions if needed:
   - What's the scope? (MVP or full feature)
   - Any specific requirements?
   - Timeline constraints?
   - Which services/games affected?
   ```

### Phase 2: Analysis & Planning

1. **Invoke Agent-Coordinator**
   ```
   Pass task to agent-coordinator for analysis:
   - Classify task complexity
   - Identify required domains
   - Determine which agents needed
   - Plan execution workflow (sequential/parallel)
   - Identify dependencies
   ```

2. **Present Execution Plan**
   ```
   Show user the plan:

   ## Task Analysis
   - **Complexity**: [Simple/Complex/Multi-phase]
   - **Domains**: [List of domains involved]
   - **Estimated Effort**: [Time estimate if applicable]

   ## Execution Plan
   **Phase 1:** [Description]
   - Agent: [name] - [purpose]

   **Phase 2:** [Description]
   - Agent: [name] - [purpose]
   - Agent: [name] - [purpose] (parallel)

   **Phase 3:** [Description]
   - Command: [command] - [purpose]

   Would you like to proceed? (yes/continue/modify plan)
   ```

3. **Get User Approval**
   ```
   Options:
   - Yes/Continue: Execute the plan
   - Modify: User can adjust the plan
   - Cancel: Abort orchestration
   ```

### Phase 3: Execution

1. **Execute Workflow**
   ```
   agent-coordinator coordinates execution:

   For each phase:
   - Update status to user
   - Invoke required agents in proper order
   - Pass context between agents
   - Handle errors/blockers
   - Aggregate results
   ```

2. **Progress Tracking**
   ```
   Continuous updates:

   ## Orchestration Progress

   ✅ Phase 1: Planning Complete
      feature-architect: Implementation plan created

   🔄 Phase 2: Design In Progress
      ✅ slot-game-specialist: Math model designed
      🔄 microservices-orchestrator: Analyzing service impact...

   ⏳ Phase 3: Pending
      Waiting for Phase 2 completion...
   ```

3. **Error Handling**
   ```
   If agent encounters issues:
   - Report clearly to user
   - Suggest resolution
   - Options:
     * Continue with remaining tasks
     * Retry failed step
     * Abort orchestration
     * Manual intervention needed
   ```

### Phase 4: Post-Execution

1. **Result Aggregation**
   ```
   agent-coordinator aggregates all results:
   - Organize by phase/domain
   - Highlight key outcomes
   - List actions taken
   - Note any outstanding items
   ```

2. **Generate Summary**
   ```markdown
   ## Orchestration Complete! 🎉

   ### Task
   [Original task description]

   ### Execution Summary

   **Phase 1: Planning** ✅
   - feature-architect created comprehensive plan
   - Estimated: [time]

   **Phase 2: Design & Implementation** ✅
   - slot-game-specialist validated RTP at 96.5%
   - microservices-orchestrator coordinated API contracts
   - Implementation completed

   **Phase 3: Quality & Documentation** ✅
   - code-review-expert: 0 critical issues
   - documentation-orchestrator: All docs updated

   ### Key Outcomes
   - [Outcome 1]
   - [Outcome 2]
   - [Outcome 3]

   ### Files Modified
   - [Count] files changed
   - [List of key files]

   ### Next Steps
   1. [Action item]
   2. [Action item]
   3. Consider running `/create-pr` to create pull request
   ```

3. **Suggest Follow-up Actions**
   ```
   Based on what was done:
   - Run `/create-pr` if code changes made
   - Run `/smart-commit` if need to commit
   - Run tests if applicable
   - Deploy to staging for testing
   - Notify stakeholders
   ```

## Task Types & Workflows

### Type 1: Feature Implementation

**Example**: "Implement bonus buy feature"

**Workflow**:
```
Phase 1: Planning
├─ feature-architect → Create implementation plan

Phase 2: Design
├─ slot-game-specialist → Design math model
├─ microservices-orchestrator → Design API contracts

Phase 3: Implementation Guidance
├─ [Provide implementation guidance to user]
├─ [User implements based on designs]

Phase 4: Validation
├─ slot-game-specialist → Validate RTP
├─ code-review-expert → Review code quality
├─ microservices-orchestrator → Validate integration

Phase 5: Documentation & PR
├─ documentation-orchestrator → Update all docs
├─ Suggest /create-pr
```

### Type 2: Analytics Dashboard

**Example**: "Build player analytics dashboard"

**Workflow**:
```
Phase 1: Requirements
├─ feature-architect → Define requirements and scope

Phase 2: Design
├─ analytics-champion → Design dashboard architecture
├─ analytics-champion → Design database queries

Phase 3: Implementation
├─ [Guide user through implementation]
├─ Or use /implement-analytics command

Phase 4: Optimization
├─ analytics-champion → Optimize query performance
├─ code-review-expert → Review implementation

Phase 5: Documentation
├─ documentation-orchestrator → Update docs
```

### Type 3: Cross-Service Feature

**Example**: "Add progressive jackpot across all services"

**Workflow**:
```
Phase 1: Planning
├─ feature-architect → Create comprehensive plan
├─ feature-architect → Document architecture decisions

Phase 2: Service Design
├─ microservices-orchestrator → Design service contracts
├─ microservices-orchestrator → Plan data flow

Phase 3: Game Integration
├─ slot-game-specialist → Design game integration
├─ slot-game-specialist → Validate RTP impact

Phase 4: Implementation Phases
├─ [Phase 4a: Jackpot Service]
├─ [Phase 4b: RGS Integration]
├─ [Phase 4c: Game Engine UI]

Phase 5: Testing & Documentation
├─ code-review-expert → Review all implementations
├─ microservices-orchestrator → Validate integration
├─ documentation-orchestrator → Update all service docs
```

### Type 4: Planning & Specification

**Example**: "Plan new tournament system"

**Workflow**:
```
Phase 1: Ideation
├─ feature-architect → Facilitate brainstorming
├─ Or use /brainstorm-feature command

Phase 2: Technical Design
├─ microservices-orchestrator → Design service architecture
├─ analytics-champion → Design analytics requirements

Phase 3: Documentation
├─ feature-architect → Create technical spec
├─ feature-architect → Create implementation plan

Result: Complete specification ready for implementation
```

### Type 5: Optimization & Refactoring

**Example**: "Optimize dashboard query performance"

**Workflow**:
```
Phase 1: Analysis
├─ analytics-champion → Analyze current queries
├─ code-review-expert → Review code quality

Phase 2: Optimization
├─ analytics-champion → Recommend optimizations
├─ [User implements recommendations]

Phase 3: Validation
├─ analytics-champion → Validate performance improvements
├─ code-review-expert → Review changes

Phase 4: Documentation
├─ documentation-orchestrator → Document optimizations
```

## Command Variations

### Basic Usage

```
/orchestrate
```
Then describe task when prompted.

### With Task Description

```
/orchestrate Implement sticky wilds feature with RTP validation
```

### With Specific Focus

```
/orchestrate [task] --focus=planning
/orchestrate [task] --focus=implementation
/orchestrate [task] --focus=review
```

(Note: Focus flags are conceptual - actual implementation depends on command parser)

## Example Scenarios

### Scenario 1: Complete Feature Implementation

```
User: /orchestrate Implement bonus buy feature with full validation

Claude:
### Task Analysis
- Complexity: Multi-phase
- Domains: Gaming, Microservices, Code Quality, Documentation
- Estimated Effort: ~9 days

### Execution Plan
**Phase 1:** Planning (1 day)
- feature-architect: Create implementation plan

**Phase 2:** Design (2 days)
- slot-game-specialist: Design math model and RTP
- microservices-orchestrator: Design API contracts

**Phase 3:** Implementation (4 days)
- [Guided implementation with spec]

**Phase 4:** Validation (1 day)
- slot-game-specialist: Validate RTP
- code-review-expert: Code review

**Phase 5:** Documentation (1 day)
- documentation-orchestrator: Update all docs

Proceed? (yes/modify/cancel)

User: yes

Claude:
## Orchestration Started

✅ Phase 1 Complete
feature-architect created comprehensive plan:
- 3 phases, 6 tasks
- RTP target: 96.5%
- Services: RGS, Game Engine, Backoffice

🔄 Phase 2 In Progress
✅ slot-game-specialist
   Math model designed:
   - Bonus buy cost: 100x bet
   - Expected value maintained
   - RTP contribution: +0.2%

🔄 microservices-orchestrator
   Analyzing service impacts...

[Continues through all phases...]

## Orchestration Complete! 🎉

All phases executed successfully.
- Plan created ✓
- Designs validated ✓
- Implementation guided ✓
- RTP validated at 96.5% ✓
- Code reviewed (0 critical issues) ✓
- Documentation updated ✓

Next Steps:
1. Test in staging environment
2. Run /create-pr when ready
3. Schedule deployment
```

### Scenario 2: Analytics Dashboard

```
User: /orchestrate Build game performance dashboard

Claude:
### Task Analysis
- Complexity: Complex
- Domains: Planning, Analytics, Code Quality, Documentation
- Estimated Effort: ~2 weeks

### Execution Plan
**Phase 1:** Requirements & Design
- feature-architect: Define scope
- analytics-champion: Design architecture

**Phase 2:** Implementation
- Use /implement-analytics command

**Phase 3:** Optimization & Review
- analytics-champion: Optimize queries
- code-review-expert: Review code

Proceed?

User: yes

Claude:
## Orchestration Started

✅ Phase 1 Complete
feature-architect defined requirements:
- Metrics: Spins, revenue, RTP, players
- Time ranges: Today, 7d, 30d, custom
- Filters: Game, game type

analytics-champion designed architecture:
- TanStack Query + Recharts
- Materialized views for performance
- Redis caching (5 min TTL)
- Database indexes planned

Ready for implementation.

🔄 Phase 2: Running /implement-analytics command...

[implement-analytics workflow executes...]

✅ Phase 2 Complete
Dashboard implemented:
- API endpoints created
- React components built
- Caching configured
- Tests added

🔄 Phase 3 In Progress
analytics-champion optimizing queries...

✅ Phase 3 Complete
Optimizations applied:
- Load time: <2 seconds ✓
- Added indexes
- Materialized view created

code-review-expert:
- Zod validation ✓
- Error handling ✓
- No performance issues ✓

## Orchestration Complete! 🎉

Game performance dashboard ready for production.

Files created: 12
- API: 3 endpoints
- Frontend: 5 components
- Tests: 8 test suites

Next Steps:
1. Test dashboard with production data
2. Run /create-pr to create pull request
3. Demo to stakeholders
```

### Scenario 3: Planning Only

```
User: /orchestrate Plan progressive jackpot system

Claude:
### Task Analysis
- Complexity: Multi-phase, High complexity
- Domains: Planning, Gaming, Microservices
- Focus: Planning and Specification

### Execution Plan
**Phase 1:** Brainstorming
- Use /brainstorm-feature command

**Phase 2:** Technical Design
- microservices-orchestrator: Service architecture
- slot-game-specialist: Game integration design

**Phase 3:** Documentation
- feature-architect: Create comprehensive spec

Proceed?

User: yes

Claude:
## Orchestration Started

🔄 Phase 1: Running /brainstorm-feature...

[brainstorm-feature workflow executes with user interaction...]

✅ Phase 1 Complete
Requirements defined:
- 4-tier jackpot (Mini, Minor, Major, Grand)
- 1% contribution per bet
- Random trigger mechanism
- Requires new Jackpot Service

🔄 Phase 2 In Progress
microservices-orchestrator designing architecture...

✅ microservices-orchestrator
Jackpot Service architecture designed:
- New microservice recommended
- API contracts defined
- Event flow documented
- Services affected: RGS, Game Engine, Backoffice, Website

✅ slot-game-specialist
Game integration designed:
- Contribution logic
- Trigger probability calculation
- Win celebration flow
- RTP impact assessment

✅ Phase 3 Complete
feature-architect created:
- Technical specification (comprehensive)
- Implementation plan (6-week timeline)
- Architecture decision record (ADR-001)
- Risk analysis and mitigations

## Orchestration Complete! 🎉

Progressive jackpot system fully planned.

Documents created:
- specs/progressive-jackpots.md
- plans/progressive-jackpots-implementation.md
- docs/architecture/ADR-001-jackpot-service.md

Ready for implementation!

Next Steps:
1. Review spec with architecture team
2. Get stakeholder approval
3. Begin Phase 1 implementation
4. Set up staging infrastructure
```

## Best Practices

1. **Be specific in task description** - More detail = better workflow
2. **Review the execution plan** - Ensure it matches your expectations
3. **Let it run** - Avoid interrupting the orchestration
4. **Trust the agents** - They're specialized experts
5. **Follow next steps** - The suggested actions are important
6. **Use for complex tasks** - Simple tasks don't need orchestration
7. **Provide feedback** - Help improve the workflow by noting issues

## When to Use /orchestrate

### Perfect For:
- Multi-domain tasks (gaming + services + analytics)
- Complex features requiring coordination
- Full feature lifecycle (plan → implement → test → doc)
- Tasks you're unsure how to start
- New features with unknown scope

### Not Needed For:
- Simple single-agent tasks
- Quick code reviews
- Minor documentation updates
- Tasks with clear, single-step solutions

### Use Other Commands Instead:
- Simple commit → `/smart-commit`
- Just analytics → `/implement-analytics`
- Just planning → `/brainstorm-feature`
- Just PR → `/create-pr`
- Cross-service docs → `/sync-service-docs`

## Error Recovery

If orchestration encounters errors:

```
⚠️ Phase [N] encountered an issue

Error: [Description]

Options:
1. Retry this phase
2. Skip and continue with remaining phases
3. Abort orchestration
4. Get help resolving the issue

What would you like to do?
```

User can choose how to proceed based on the situation.

## Integration

The `/orchestrate` command:
- Uses `agent-coordinator` for workflow management
- Can invoke any Phase 1-3 agent
- Can call other commands (`/smart-commit`, `/implement-analytics`, etc.)
- Coordinates with all plugin phases
- Provides end-to-end solutions

---

**Goal**: Make complex, multi-domain tasks feel simple. Let the orchestrator handle the coordination while you focus on the implementation. From idea to production-ready feature with intelligent guidance every step of the way.
