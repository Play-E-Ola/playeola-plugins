# Playeola Gaming Plugin

**Phase 2: Gaming & Microservices** - Specialized gaming expertise and microservices orchestration for Playeola's iGaming development stack.

## What's Included

### Agents

#### `slot-game-specialist`
Expert in slot game mechanics, Phaser engine, and game math validation.

**Capabilities:**
- RTP calculations and validation
- Slot mechanics (wilds, scatters, free spins, bonus features)
- Phaser 3 best practices and performance optimization
- Game math verification and paytable configuration
- Game Engine ↔ RGS integration patterns
- Animation and UX optimization

**When to Use:**
- Building or modifying slot games
- Validating game math and RTP
- Optimizing Phaser performance
- Implementing game features (wilds, bonuses, etc.)
- Troubleshooting game logic issues

#### `microservices-orchestrator`
Expert in microservices architecture across Playeola's service ecosystem.

**Capabilities:**
- Service communication patterns (REST, WebSocket, events)
- API contract design and validation
- Cross-service workflow orchestration
- Service boundary analysis
- Breaking change detection
- Reliability and resilience patterns

**Service Coverage:**
- **RGS** (Remote Game Server)
- **Game Engine** (Phaser-based client)
- **Math Simulator** (RTP validation)
- **Backoffice** (admin platform)
- **Website** (public platform)

**When to Use:**
- Making API changes that affect multiple services
- Designing new service integrations
- Troubleshooting cross-service issues
- Reviewing service communication patterns
- Planning service architecture

### Commands

#### `/sync-service-docs`
Cross-service documentation synchronization workflow.

**What it does:**
1. **Detect Changes** - Identifies API/contract modifications
2. **Analyze Impact** - Maps affected services via `microservices-orchestrator`
3. **Update Documentation** - Syncs docs across all affected services
4. **Handle Breaking Changes** - Creates migration guides when needed

**When to Use:**
- After modifying any service API
- When adding new endpoints
- After changing request/response schemas
- When updating service contracts

### Hooks

Smart automation for gaming development:
- **Gaming context detection** - Suggests `slot-game-specialist` for game-related work
- **Service changes detection** - Suggests `microservices-orchestrator` for API work
- **RTP validation reminders** - Alerts when game math changes
- **Phaser performance tips** - Reminds about performance when scenes modified
- **Breaking change warnings** - Alerts on API contract modifications
- **Auto sync suggestions** - Prompts `/sync-service-docs` when APIs change

## Installation

This plugin is installed via the Playeola marketplace:

```bash
# Add marketplace (if not already added)
/plugin marketplace add Play-E-Ola/playeola-plugins

# Install this plugin
/plugin install playeola-gaming@playeola-marketplace
```

## Usage Examples

### Scenario 1: Adding Sticky Wilds Feature

```
You: I need to add sticky wilds to Wild West Slots

Claude: [invokes slot-game-specialist agent]

Agent Analysis:
- Reviews current wild symbol implementation
- Designs sticky wild mechanics
- Calculates feature impact on RTP
- Provides implementation in both math and presentation layers
- Suggests Phaser animation patterns
- Creates test cases

Result: Feature implemented with verified math and smooth animations
```

### Scenario 2: New RGS API Endpoint

```
You: I added a bonus buy endpoint to RGS

Claude: [invokes microservices-orchestrator agent]

Agent Analysis:
- Identifies consumers (Game Engine, Backoffice)
- Validates API contract
- Checks backward compatibility
- Suggests integration tests

You: /sync-service-docs

Claude:
✅ Updated RGS: docs/api/bonus-buy.md
✅ Updated Game Engine: docs/integration/rgs-client.md (added bonus buy example)
✅ Updated Backoffice: docs/analytics/game-features.md

Result: All services have updated documentation
```

### Scenario 3: RTP Investigation

```
You: The Math Simulator shows 95.8% RTP but we designed for 96.5%

Claude: [invokes slot-game-specialist agent]

Agent Analysis:
- Reviews paytable configuration
- Analyzes symbol weights
- Checks feature contribution to RTP
- Identifies discrepancy in free spin calculation
- Provides corrected configuration

Result: RTP corrected to match design spec
```

### Scenario 4: Breaking API Change

```
You: I changed the RGS spin response format

Claude: [invokes microservices-orchestrator agent]

Agent Warning:
⚠️ Breaking change detected!
Affected services: Game Engine (critical), Math Simulator (important)

Recommendation: API versioning strategy
- Keep v1 for backward compatibility
- Introduce v2 endpoint
- Provide 6-week migration timeline

You: /sync-service-docs

Claude:
✅ Created docs/api/v2/spin-endpoint.md
✅ Created migration guide: docs/migrations/v1-to-v2.md
✅ Updated all consuming services with migration path
✅ Added deprecation notices

Result: Safe rollout with clear migration path
```

## Works With

### Game Development
- **Game Engine** - Phaser-based slot games
- **Math Simulator** - RTP validation and calculations
- **RGS** - Server-side game logic

### Microservices
- **RGS** ↔ **Game Engine** - Game round communication
- **RGS** ↔ **Math Simulator** - Math validation
- **RGS** ↔ **Backoffice** - Analytics and configuration
- **Website** ↔ **RGS** - Session management and game launching

## Integration with Phase 1

This plugin builds on `playeola-foundation`:

**Inherits from Phase 1:**
- `code-review-expert` - Still enforces code quality
- `documentation-orchestrator` - Powers `/sync-service-docs`
- `/smart-commit` - Still available for quality commits

**Adds Phase 2 Capabilities:**
- Gaming expertise (slot mechanics, Phaser)
- Microservices orchestration
- Cross-service documentation sync

**Recommendation:** Install both plugins for full functionality:
```bash
/plugin install playeola-foundation@playeola-marketplace
/plugin install playeola-gaming@playeola-marketplace
```

## Key Features

### For Game Developers
- Expert guidance on slot mechanics and features
- RTP calculation and validation assistance
- Phaser optimization and best practices
- Game math troubleshooting

### For Backend Engineers
- Cross-service API coordination
- Breaking change management
- Service architecture guidance
- Integration pattern recommendations

### For Full Stack Teams
- Synchronized documentation across services
- Clear service boundaries
- Automated cross-service updates
- Migration guides for breaking changes

## Project Adaptation

Like Phase 1, this plugin automatically adapts to your project:

**Game Configuration:**
- Discovers game config structure
- Adapts to your paytable format
- Works with any RTP target

**Service Architecture:**
- Maps your specific service dependencies
- Adapts to your API patterns
- Handles any communication protocol

**Documentation Structure:**
- Discovers each service's doc layout
- Maintains your existing organization
- No assumptions about file locations

## Version

**v1.1.0** - Phase 2 release with gaming and microservices features

## Part of Playeola Marketplace

This is Phase 2 of the Playeola plugin ecosystem:

- **Phase 1** ✅ `playeola-foundation` - Code review, documentation, smart commit
- **Phase 2** ✅ `playeola-gaming` - Gaming specialists & microservices (this plugin)
- **Phase 3** 🚧 `playeola-analytics` - Analytics workflows & feature planning
- **Phase 4** 🚧 `playeola-advanced` - Advanced orchestration & PR automation

## Tips for Maximum Effectiveness

1. **Let agents auto-invoke** - The hooks will suggest the right agent at the right time
2. **Use `/sync-service-docs` early** - Don't wait until all changes are done
3. **Leverage both agents together** - They collaborate on cross-service gaming features
4. **Trust the math validation** - `slot-game-specialist` knows RTP calculations
5. **Version breaking changes** - Follow the v1/v2 pattern for API changes

## Troubleshooting

### Agent Not Triggering
- Check that hooks are enabled in `hooks/hooks.json`
- Use gaming keywords (slot, rtp, phaser) to trigger `slot-game-specialist`
- Use service keywords (api, endpoint, rgs) to trigger `microservices-orchestrator`

### Documentation Not Syncing
- Ensure documentation directories exist in services
- Check that `/sync-service-docs` can detect your API changes
- Verify `documentation-orchestrator` from Phase 1 is available

### RTP Calculations Seem Wrong
- Invoke `slot-game-specialist` explicitly for deep analysis
- Review paytable configuration files
- Check Math Simulator integration

---

**Built for production iGaming development by Playeola**
