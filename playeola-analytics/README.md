# Playeola Analytics Plugin

**Phase 3: Analytics & Planning** - Analytics workflows, dashboard design expertise, and feature planning tools for Playeola's iGaming development stack.

## What's Included

### Agents

#### `analytics-champion`
Analytics and dashboard design expert for data-driven features.

**Capabilities:**
- Dashboard design and implementation (TanStack Query, Recharts)
- Data validation with Zod schemas
- Analytics API design patterns
- Performance optimization for queries and visualizations
- Database query optimization
- Real-time analytics and caching strategies
- Backoffice analytics expertise

**When to Use:**
- Building dashboards or analytics features
- Designing data visualization
- Optimizing query performance
- Implementing data validation
- Creating analytics APIs
- Working on Backoffice analytics

#### `feature-architect`
Feature planning and brainstorming expert that transforms ideas into actionable plans.

**Capabilities:**
- Facilitated ideation and brainstorming sessions
- Technical specification writing
- Implementation plan creation (SESSION_STATE.md style)
- Task breakdown and estimation
- Scope management (MVP definition)
- Architecture decision documentation
- Risk identification and mitigation planning

**When to Use:**
- Planning new features
- Brainstorming solutions
- Creating technical specifications
- Breaking down complex features
- Estimating effort and timeline
- Defining project scope
- Documenting architecture decisions

### Commands

#### `/implement-analytics`
Comprehensive analytics implementation workflow.

**What it does:**
1. **Requirements Discovery** - Understands analytics needs via `analytics-champion`
2. **Technical Design** - Designs data models, APIs, and dashboard architecture
3. **Implementation** - Scaffolds database, API, and frontend components
4. **Testing & Documentation** - Adds tests and updates documentation

**When to Use:**
- Implementing new dashboards
- Creating analytics features
- Building data visualization
- Setting up analytics APIs

#### `/brainstorm-feature`
Interactive feature brainstorming and planning workflow.

**What it does:**
1. **Ideation** - Facilitates brainstorming via `feature-architect`
2. **Requirements** - Documents functional and non-functional requirements
3. **Technical Design** - Creates architecture and API designs
4. **Implementation Planning** - Breaks down tasks with estimates
5. **Documentation** - Generates spec and implementation plan documents

**When to Use:**
- Planning new features
- Starting complex projects
- Need structured ideation
- Creating technical specifications
- Breaking down large features

### Hooks

Smart automation for analytics and planning:
- **Analytics context detection** - Suggests `analytics-champion` for dashboard work
- **Feature planning detection** - Suggests `feature-architect` for planning
- **Dashboard performance reminders** - Alerts on query optimization
- **Data validation prompts** - Reminds to add Zod validation
- **Testing strategy reminders** - Prompts for test coverage
- **Documentation update alerts** - When analytics APIs change

## Installation

This plugin is installed via the Playeola marketplace:

```bash
# Add marketplace (if not already added)
/plugin marketplace add Play-E-Ola/playeola-plugins

# Install this plugin
/plugin install playeola-analytics@playeola-marketplace
```

## Usage Examples

### Scenario 1: Building Analytics Dashboard

```
You: I need to build a game performance dashboard

Claude: [invokes analytics-champion agent]

Agent Analysis:
- Identifies key metrics (spins, revenue, RTP, players)
- Designs efficient database queries
- Plans dashboard architecture with TanStack Query
- Recommends Recharts for visualization
- Suggests caching strategy

You: /implement-analytics

Claude:
✅ Requirements gathered
✅ Database schema designed
✅ API endpoints implemented
✅ Dashboard components created
✅ Tests added
✅ Documentation updated

Result: Production-ready analytics dashboard
```

### Scenario 2: Planning New Feature

```
You: /brainstorm-feature

Claude: What feature would you like to explore?

You: Progressive jackpot system across all games

Claude: [invokes feature-architect agent]

Agent Facilitation:
- Asks discovery questions about requirements
- Explores technical approaches
- Designs system architecture
- Creates implementation plan
- Documents decisions and risks

Result:
📄 Created specs/progressive-jackpots.md
📄 Created plans/progressive-jackpots-implementation.md

Ready to implement with clear roadmap!
```

### Scenario 3: Analytics Optimization

```
You: Our analytics dashboard is loading slowly

Claude: [invokes analytics-champion agent]

Agent Analysis:
- Reviews database queries
- Identifies missing indexes
- Suggests materialized views
- Recommends caching strategy
- Optimizes frontend data fetching

Recommendations:
1. Add indexes on game_id, created_at
2. Create materialized view for daily aggregates
3. Add Redis caching (5 min TTL)
4. Implement pagination for large datasets

Result: Dashboard loads in <2 seconds
```

### Scenario 4: Complex Feature Planning

```
You: Need to plan a new bonus buy feature

Claude: [invokes feature-architect agent]

Agent Process:
1. Discovery: Understands requirements and goals
2. Design: Creates technical architecture
3. Planning: Breaks down into tasks with estimates
4. Documentation: Generates comprehensive spec

Created Documents:
- specs/bonus-buy-feature.md
- plans/bonus-buy-implementation.md

Estimate: 9 days across 3 phases
Next steps clearly defined
```

## Works With

### Analytics Use Cases
- **Backoffice** - Admin dashboards and reports
- **RGS** - Game performance analytics
- **Math Simulator** - RTP and simulation analytics
- **Website** - Player engagement metrics
- **Game Engine** - Client-side analytics

### Planning Use Cases
- **All Projects** - Feature planning and specifications
- **Cross-Service Features** - Coordinated feature development
- **Complex Features** - Structured breakdown and planning
- **Team Collaboration** - Shared technical specifications

## Integration with Other Phases

This plugin builds on Phases 1 & 2:

**Inherits from Phase 1:**
- `code-review-expert` - Ensures analytics code quality
- `documentation-orchestrator` - Keeps analytics docs updated
- `/smart-commit` - Quality commits with analytics features

**Inherits from Phase 2:**
- `slot-game-specialist` - For game analytics features
- `microservices-orchestrator` - For cross-service analytics
- `/sync-service-docs` - Sync analytics API docs

**Adds Phase 3 Capabilities:**
- Analytics implementation workflows
- Dashboard design expertise
- Feature planning and brainstorming
- Technical specification creation

**Recommendation:** Install all three plugins for full functionality:
```bash
/plugin install playeola-foundation@playeola-marketplace
/plugin install playeola-gaming@playeola-marketplace
/plugin install playeola-analytics@playeola-marketplace
```

## Key Features

### For Data Analysts & Operators
- Expert dashboard design guidance
- Performance-optimized analytics queries
- Real-time data visualization
- Data validation and integrity

### For Product Managers
- Structured feature brainstorming
- Clear technical specifications
- Implementation planning with estimates
- Progress tracking documentation

### For Developers
- Analytics implementation workflows
- Best practices for dashboards
- Query optimization guidance
- Testing strategy for analytics

### For Teams
- Shared technical specifications
- Clear implementation plans
- Architecture decision records
- Progress tracking (SESSION_STATE.md)

## Technology Stack Expertise

### Frontend
- React + TypeScript
- TanStack Query (React Query)
- Recharts / Chart.js
- Zod validation
- React Hook Form

### Backend
- Node.js + TypeScript
- REST & GraphQL APIs
- PostgreSQL optimization
- Redis caching
- Database migrations

### Analytics
- SQL query optimization
- Materialized views
- Data aggregation strategies
- Real-time updates
- Performance monitoring

## Project Adaptation

Like Phases 1 & 2, this plugin automatically adapts:

**Dashboard Patterns:**
- Discovers your existing dashboard structure
- Adapts to your data fetching patterns
- Works with your visualization preferences

**Planning Documentation:**
- Follows your documentation structure
- Matches your specification format
- Adapts to your project management style

**Analytics Requirements:**
- Adjusts to your data sources
- Adapts to your performance requirements
- Works with any database or API

## Best Practices Enforced

1. **Always validate data with Zod schemas**
2. **Use TanStack Query for data fetching and caching**
3. **Optimize database queries with indexes and materialized views**
4. **Implement proper loading and error states**
5. **Cache aggressively with appropriate invalidation**
6. **Start feature planning with "why" - understand the problem**
7. **Break features into MVP and phases**
8. **Document architecture decisions**
9. **Test with realistic data volumes**
10. **Monitor analytics query performance**

## Version

**v1.2.0** - Phase 3 release with analytics and planning features

## Part of Playeola Marketplace

This is Phase 3 of the Playeola plugin ecosystem:

- **Phase 1** ✅ `playeola-foundation` - Code review, documentation, smart commit
- **Phase 2** ✅ `playeola-gaming` - Gaming specialists & microservices
- **Phase 3** ✅ `playeola-analytics` - Analytics & feature planning (this plugin)
- **Phase 4** 🚧 `playeola-advanced` - Advanced orchestration & PR automation

## Tips for Maximum Effectiveness

1. **Use `/implement-analytics` for guided analytics implementation** - Don't start from scratch
2. **Use `/brainstorm-feature` for complex features** - Structure saves time
3. **Let agents auto-invoke** - Hooks will suggest the right agent at the right time
4. **Create SESSION_STATE.md for tracking** - Keep implementation progress visible
5. **Trust the performance guidance** - Analytics-champion knows optimization patterns
6. **Document decisions as you go** - Use feature-architect for ADRs
7. **Test with realistic data** - Always validate performance at scale
8. **Iterate on specifications** - Plans evolve, update documents accordingly

## Troubleshooting

### Agent Not Triggering
- Use analytics keywords (dashboard, metrics, visualization) for `analytics-champion`
- Use planning keywords (brainstorm, feature, plan) for `feature-architect`
- Check that hooks are enabled in `hooks/hooks.json`

### Slow Dashboard Performance
- Invoke `analytics-champion` explicitly for optimization guidance
- Check database indexes
- Review query execution plans
- Consider materialized views
- Add caching layer

### Feature Planning Overwhelming
- Start with `/brainstorm-feature` command for structure
- Focus on MVP first
- Break large features into phases
- Document one decision at a time

### Analytics Implementation Complex
- Use `/implement-analytics` for step-by-step guidance
- Start with simple metrics first
- Build incrementally
- Test each component separately

## Example Document Outputs

### Technical Specification
When using `/brainstorm-feature`, generates:
- `specs/[feature-name].md` - Complete technical specification
- Problem statement, requirements, design, user flows
- Testing strategy and rollout plan
- Risks, mitigations, and open questions

### Implementation Plan
Also generates:
- `plans/[feature-name]-implementation.md` - SESSION_STATE.md style
- Task breakdown by phase
- Progress tracking sections
- Decisions and notes sections
- Next steps clearly defined

---

**Built for data-driven decision making and systematic feature development by Playeola**
