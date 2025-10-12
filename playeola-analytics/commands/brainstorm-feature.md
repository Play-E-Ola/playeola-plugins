---
name: brainstorm-feature
description: Interactive feature brainstorming and planning workflow - guides from initial idea through technical specification and implementation plan creation
---

Execute a comprehensive feature brainstorming workflow that facilitates ideation, creates technical specifications, and generates actionable implementation plans.

**Feature idea from command:** $ARGUMENTS

## Workflow

### Phase 0: Context Gathering

**IMPORTANT: Before starting brainstorming, gather context about the feature idea.**

1. **Review Recent Conversation History**
   ```
   - Read the last 10-15 messages before this command was invoked
   - Identify what feature ideas were discussed
   - Note any user needs, pain points, or problems mentioned
   - Look for any business goals or success metrics discussed
   - Check for any technical constraints or considerations mentioned
   - Identify stakeholder mentions or target users
   ```

2. **Check Project Context**
   ```
   Run these commands:
   - `pwd` - Identify which project (RGS, Game Engine, Backoffice, etc.)
   - `git status` - See if any related work is in progress
   - `git branch --show-current` - Check branch name for hints
   - `ls -la specs/` or `ls -la plans/` - Check for existing specs/plans
   ```

3. **Synthesize Feature Context**
   ```
   Build understanding:
   - What feature idea needs brainstorming? (from $ARGUMENTS or conversation)
   - Why is this feature being considered?
   - What problem does it solve?
   - Who benefits from this feature?
   - Are there existing designs or discussions to build upon?
   ```

4. **Determine Starting Point**
   ```
   Priority order:

   a) If $ARGUMENTS provided: Use as starting point
      Example: `/brainstorm-feature sticky wilds for slot games`
      → Start brainstorming sticky wilds

   b) If conversation discussed a feature idea: Reference and confirm
      Example: User mentioned wanting to add tournaments
      → Say: "I see you were discussing tournament features. Should I brainstorm that?"

   c) If no clear context: Ask what to brainstorm
      → Say: "What feature would you like to brainstorm?"
      → Provide examples: "I can help brainstorm:
         - New game features (bonus rounds, jackpots, special symbols)
         - Analytics dashboards
         - Player engagement features
         - Backend optimizations
         - Cross-service features"
   ```

### Phase 1: Ideation & Discovery

1. **Understand the Idea**
   ```
   Invoke feature-architect agent to:
   - Ask probing questions about the feature idea
   - Understand the problem being solved
   - Identify user personas and use cases
   - Explore business goals and success metrics
   - Validate feasibility and scope
   ```

2. **Facilitated Brainstorming**
   ```
   Interactive questions:
   - What problem are we solving?
   - Who will use this feature?
   - What does success look like?
   - What are the constraints (time, resources, tech)?
   - What are potential risks?

   Exploration:
   - Discuss alternative approaches
   - Consider trade-offs
   - Identify technical challenges
   - Surface edge cases
   ```

3. **Summarize Ideas**
   ```
   Present summary:
   - Problem statement
   - Proposed solution
   - Key alternatives considered
   - Selected approach and rationale
   - Known risks and constraints
   ```

### Phase 2: Requirements Definition

1. **Define Requirements**
   ```
   Invoke feature-architect agent to:
   - Document functional requirements
   - Document non-functional requirements:
     * Performance targets
     * Security requirements
     * Scalability needs
     * Integration points
   - Define user stories
   - Establish acceptance criteria
   ```

2. **Scope Definition**
   ```
   Use MoSCoW method:
   - Must Have: Critical functionality for MVP
   - Should Have: Important but not critical
   - Could Have: Nice to have
   - Won't Have: Out of scope for this iteration

   Define MVP:
   - Minimum viable features
   - Phased rollout plan
   ```

3. **Present Requirements**
   ```
   Show user:
   - Functional requirements list
   - Non-functional requirements
   - User stories
   - MVP definition
   - Out of scope items
   ```

### Phase 3: Technical Design

1. **Architecture Design**
   ```
   Invoke feature-architect agent to:
   - Design system architecture
   - Define data models
   - Specify API contracts
   - Plan service interactions
   - Consider scalability
   - Design for failure handling
   ```

2. **Identify Dependencies**
   ```
   - Which services are affected?
   - What external systems are involved?
   - Are there library dependencies?
   - What infrastructure is needed?
   - Are there team dependencies?
   ```

3. **Technical Decisions**
   ```
   Document key decisions:
   - Technology choices
   - Architecture patterns
   - Data storage approach
   - Integration patterns
   - Rationale for each decision
   ```

4. **Present Technical Design**
   ```
   Show user:
   - Architecture overview
   - Data model diagrams
   - API contracts
   - Service interaction flows
   - Key technical decisions
   ```

### Phase 4: Implementation Planning

1. **Task Breakdown**
   ```
   Invoke feature-architect agent to:
   - Break feature into tasks
   - Estimate each task (t-shirt sizing)
   - Identify task dependencies
   - Organize into phases/sprints
   - Assign complexity levels
   ```

2. **Define Milestones**
   ```
   Create phased delivery plan:
   - Phase 1: Foundation (core infrastructure)
   - Phase 2: Implementation (main features)
   - Phase 3: Polish (testing, optimization)

   Set milestones:
   - MVP delivery date
   - Beta testing date
   - Production launch date
   ```

3. **Testing Strategy**
   ```
   Plan testing approach:
   - Unit tests for core logic
   - Integration tests for APIs
   - E2E tests for user flows
   - Performance testing if needed
   - Security testing if applicable
   ```

4. **Present Implementation Plan**
   ```
   Show user:
   - Task breakdown with estimates
   - Phase organization
   - Dependencies and milestones
   - Testing strategy
   - Overall timeline
   ```

### Phase 5: Documentation Creation

1. **Create Technical Specification**
   ```
   Generate spec document:
   - Feature overview
   - Problem statement and goals
   - Requirements (functional & non-functional)
   - Technical design
   - User flows
   - API specifications
   - Testing strategy
   - Rollout plan
   - Risks and mitigations
   ```

2. **Create Implementation Plan**
   ```
   Generate SESSION_STATE.md style document:
   - Current status section
   - Task list organized by phase
   - Completed work section
   - In progress section
   - Next steps section
   - Blockers section
   - Decisions made section
   - Notes section
   ```

3. **Save Documents**
   ```
   Create files:
   - specs/[feature-name].md (technical spec)
   - plans/[feature-name]-implementation.md (plan)

   Or update existing project documentation structure
   ```

### Phase 6: Summary & Next Steps

1. **Generate Summary Report**
   ```
   Feature Brainstorming Complete!

   📋 Documents Created:
   ✅ Technical Specification: specs/[feature-name].md
   ✅ Implementation Plan: plans/[feature-name]-implementation.md

   📊 Feature Summary:
   - Problem: [Brief description]
   - Solution: [Brief description]
   - Estimated effort: [X] days/weeks
   - Phases: [N] phases
   - Key risks: [List]

   🎯 Next Steps:
   1. Review documents with team
   2. Get stakeholder approval
   3. Refine estimates if needed
   4. Begin Phase 1 implementation
   5. Set up progress tracking
   ```

2. **Provide Recommendations**
   ```
   - Suggest which team members to involve
   - Identify stakeholders for approval
   - Recommend starting with MVP
   - Suggest regular check-ins
   ```

## Brainstorming Question Templates

### Problem Understanding Questions
- "What problem are we trying to solve?"
- "Who is experiencing this problem?"
- "How are they solving it today?"
- "What makes the current solution inadequate?"
- "What would success look like?"

### User & Stakeholder Questions
- "Who are the primary users of this feature?"
- "What are their goals and pain points?"
- "Who are the stakeholders?"
- "What are the business objectives?"
- "How will we measure success?"

### Technical Feasibility Questions
- "What technical constraints do we have?"
- "What systems/services will be affected?"
- "Are there performance requirements?"
- "What are the security implications?"
- "Do we have the necessary expertise?"

### Scope & Timeline Questions
- "What's the deadline or target date?"
- "What's the minimum viable version?"
- "What can we defer to later phases?"
- "What's the highest priority?"
- "Are there dependencies on other teams?"

### Risk & Challenge Questions
- "What could go wrong?"
- "What are the biggest risks?"
- "What are we most uncertain about?"
- "What assumptions are we making?"
- "How will we validate those assumptions?"

## Document Templates

### Technical Specification Template
```markdown
# Feature Specification: [Feature Name]

## Overview
[Brief description and purpose]

## Problem Statement
[What problem are we solving? Why is this important?]

## Goals & Success Metrics
- [Primary goal]
- [Success metric]

## User Stories
- As a [persona], I want [action] so that [benefit]

## Requirements

### Functional Requirements
- [FR-1] [Description]

### Non-Functional Requirements
- **Performance**: [Targets]
- **Security**: [Requirements]
- **Scalability**: [Targets]

## Technical Design

### Architecture
[Description or diagram]

### Data Model
[Schema definitions]

### API Contracts
[Endpoint specifications]

### Service Interactions
[How services communicate]

## User Flows
[Key user journeys]

## Testing Strategy
- Unit tests
- Integration tests
- E2E tests

## Rollout Plan
- Phase 1: [Description]
- Phase 2: [Description]

## Risks & Mitigations
- **Risk**: [Description]
  - **Mitigation**: [Strategy]

## Out of Scope
- [What is not included]

## Open Questions
- [Questions to be resolved]
```

### Implementation Plan Template
```markdown
# Implementation Plan: [Feature Name]

## Current Status
- **Phase**: Planning
- **Started**: [Date]
- **Target Completion**: [Date]
- **Overall Progress**: 0% complete

## Overview
[Brief summary of the feature and approach]

## Tasks

### Phase 1: Foundation
- [ ] Task 1 - [Estimate]
- [ ] Task 2 - [Estimate]

### Phase 2: Core Implementation
- [ ] Task 3 - [Estimate]
- [ ] Task 4 - [Estimate]

### Phase 3: Testing & Polish
- [ ] Task 5 - [Estimate]
- [ ] Task 6 - [Estimate]

## Completed Work
(Will be updated as work progresses)

## In Progress
(Will be updated as work progresses)

## Next Steps
1. [First action item]
2. [Second action item]

## Blockers
(None at this time)

## Decisions Made
- [Date] **Decision**: [Description]
  - **Rationale**: [Reasoning]

## Notes
- [Date] [Initial planning completed]

## Resources
- [Link to spec]
- [Link to designs]
```

## Example Usage Scenarios

### Scenario 1: New Slot Game Feature

```
User: /brainstorm-feature

Claude: I'll facilitate a feature brainstorming session. What feature would you like to explore?

User: Adding sticky wilds to our slot games

Claude:
Great! Let's explore this feature together.

### Discovery Questions
1. Which games should have sticky wilds? (All games or specific ones?)
2. How long should wilds stick? (One spin, multiple spins, entire session?)
3. Should sticky wilds affect RTP? How much?
4. Any special animations or effects needed?
5. Backend or client-side implementation? Both?

User: [Provides answers]

Claude:
### Ideation Summary
✅ Problem: Increase player engagement with exciting wild features
✅ Solution: Sticky wilds that remain for 3 spins
✅ Scope: Start with one game (Wild West Slots)
✅ RTP Impact: Adjust paytable to maintain 96.5% RTP

Invoking feature-architect for requirements...

### Requirements
**Functional:**
- Wild symbols stick for 3 consecutive spins
- Visual indicator showing sticky duration
- Works with existing wild substitution logic
- Trigger: Random chance on any wild appearance

**Non-Functional:**
- RTP maintained at 96.5%
- No performance impact on game speed
- Smooth animations (60fps)

Invoking slot-game-specialist for technical design...

### Technical Design
**Math Engine (RGS):**
- Track sticky wild positions and durations
- Adjust symbol probabilities for RTP balance
- Validate in Math Simulator

**Game Engine (Phaser):**
- Sticky wild indicator UI
- Countdown animation
- Sticky persist across spins

**Data Model:**
- Add stickyWilds array to game state
- Each entry: {position, remainingSpins}

### Implementation Plan
Created: plans/sticky-wilds-implementation.md

**Phase 1: Math Implementation** (3 days)
- Update RGS math engine
- Add sticky wild logic
- Validate RTP in simulator

**Phase 2: Game Engine** (4 days)
- Implement UI indicators
- Add animations
- Sync with RGS state

**Phase 3: Testing** (2 days)
- Math validation
- Integration testing
- QA in staging

Total: ~9 days

📄 Documents Created:
- specs/sticky-wilds-feature.md
- plans/sticky-wilds-implementation.md

🎯 Next Steps:
1. Review spec with game design team
2. Get RTP adjustment approved
3. Start Phase 1 implementation
```

### Scenario 2: Analytics Dashboard

```
User: /brainstorm-feature for a new analytics dashboard

Claude:
Let's brainstorm your analytics dashboard feature!

### Discovery
What analytics do you want to track?

User: Player behavior, game performance, and revenue metrics

Claude:
Great! More questions:
- Who will use this dashboard? (Operators? Analysts?)
- What time ranges? (Real-time? Historical?)
- Any specific KPIs you're targeting?
- Integration with existing tools?

User: [Answers]

Claude:
### Ideation Summary
✅ Audience: Operators and business analysts
✅ Metrics: Player engagement, game performance, revenue
✅ Time ranges: Last 24h, 7d, 30d, 90d, custom
✅ Real-time updates every 5 minutes

Invoking analytics-champion and feature-architect...

### Requirements
**Must Have:**
- Player count and active sessions
- Game performance (RTP, spins, revenue by game)
- Revenue trends and projections

**Should Have:**
- Player segmentation
- Retention cohorts
- Export to CSV

**Could Have:**
- Predictive analytics
- Anomaly detection

### Technical Design
**Backend:**
- Daily aggregation jobs
- Real-time metrics via Redis
- GraphQL API for flexibility

**Frontend:**
- TanStack Query + Recharts
- Dashboard with date range filters
- Responsive design

**Database:**
- Materialized views for performance
- Indexes on game_id, date, player_id

### Implementation Plan
Created: plans/analytics-dashboard-implementation.md

**Phase 1:** Backend (1 week)
**Phase 2:** Frontend (1 week)
**Phase 3:** Testing & Polish (3 days)

Total: ~2.5 weeks

📄 Documents Created:
- specs/analytics-dashboard.md
- plans/analytics-dashboard-implementation.md

Ready to proceed with implementation!
```

### Scenario 3: Cross-Service Feature

```
User: /brainstorm-feature for progressive jackpots across all games

Claude:
Excellent idea! Progressive jackpots are complex. Let's explore this thoroughly.

### Discovery Questions
1. Shared jackpot pool or per-game jackpots?
2. How are contributions calculated? (% of each bet)
3. What triggers the win? (Random, must-win-by amount?)
4. Multi-tier jackpots? (Mini, Minor, Major, Grand)
5. Regulatory requirements to consider?

User: [Provides detailed answers]

Claude:
### Ideation Summary
This is a high-complexity, cross-service feature!

Services affected:
- RGS (contribution, trigger logic)
- New Jackpot Service (pool management)
- Game Engine (jackpot display, win celebration)
- Backoffice (configuration, monitoring)
- Website (jackpot lobby display)

Invoking microservices-orchestrator and feature-architect...

### Requirements
**Functional:**
- 4-tier jackpot (Mini, Minor, Major, Grand)
- 1% of bet contributes to pool
- Random trigger with weighted probabilities
- Atomic transactions (win or rollback)

**Non-Functional:**
- 99.99% uptime (jackpot service is critical)
- Transaction log for audit trail
- Real-time updates to all clients
- Handle 10,000 concurrent players

### Technical Design
**New Jackpot Service:**
- Manages pools and contributions
- Trigger logic with weighted probabilities
- Transaction handling with rollback
- WebSocket for real-time updates

**API Contracts:**
- POST /jackpot/contribute
- POST /jackpot/trigger-check
- GET /jackpot/current-values
- WebSocket: jackpot-updates

**Database:**
- jackpot_pools table
- jackpot_transactions (audit trail)
- jackpot_wins (history)

### Implementation Plan
Created: plans/progressive-jackpots-implementation.md

**Phase 1:** Jackpot Service (2 weeks)
**Phase 2:** RGS Integration (1 week)
**Phase 3:** Game Engine UI (1 week)
**Phase 4:** Backoffice & Website (1 week)
**Phase 5:** Testing & Rollout (1 week)

Total: ~6 weeks

⚠️ **Critical Decisions Needed:**
1. New microservice vs RGS extension?
2. Database choice (PostgreSQL? Dedicated?)
3. Staging rollout strategy?

📄 Documents Created:
- specs/progressive-jackpots.md (comprehensive)
- plans/progressive-jackpots-implementation.md
- ADR-001: Jackpot service architecture decision

🎯 Next Steps:
1. Review with architecture team
2. Get stakeholder approval
3. Decide on microservice architecture
4. Plan staging environment setup
```

## Best Practices

1. **Ask questions early** - Don't make assumptions
2. **Explore alternatives** - Consider multiple approaches
3. **Think incrementally** - Define MVP and phases
4. **Document decisions** - Record why choices were made
5. **Be realistic** - Don't underestimate complexity
6. **Consider risks** - Surface challenges upfront
7. **Involve stakeholders** - Get input from the right people
8. **Keep it flexible** - Plans will evolve, that's okay

## Integration with Other Agents/Commands

- **Uses `feature-architect`**: Core agent for planning and design
- **May use `analytics-champion`**: For analytics features
- **May use `slot-game-specialist`**: For game features
- **May use `microservices-orchestrator`**: For cross-service features
- **Feeds into `/implement-analytics`**: For analytics features
- **Works with `/smart-commit`**: To commit plans and specs

---

**Goal**: Transform vague ideas into concrete, actionable plans. Make feature planning collaborative, thorough, and fun!
