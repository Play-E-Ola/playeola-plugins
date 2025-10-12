---
name: sync-service-docs
description: Cross-service documentation synchronization - identifies API changes and updates documentation across all affected Playeola services
---

Execute a comprehensive cross-service documentation sync workflow that ensures API contracts, integration guides, and service documentation remain consistent across Playeola's microservices ecosystem.

## Overview

When API changes are made in one service (e.g., RGS), this command ensures that all consuming services and their documentation are updated accordingly. This prevents documentation drift and maintains accurate integration guides across the platform.

## Workflow

### Phase 0: Context Gathering

**IMPORTANT: Before detecting changes, gather context about what was modified and why.**

1. **Review Recent Conversation History**
   ```
   - Read the last 10-15 messages before this command was invoked
   - Identify what API changes were made
   - Understand why the changes were needed
   - Note if changes are breaking or non-breaking (from discussion)
   - Look for mentions of affected services or endpoints
   - Check for any migration considerations discussed
   ```

2. **Check Git Context**
   ```
   Run these commands:
   - `git status` - See modified files
   - `git diff` - Review changes to API files
   - `git branch --show-current` - Identify which service
   - `pwd` - Confirm current working directory/service
   ```

3. **Synthesize API Change Context**
   ```
   Build understanding:
   - Which service was modified? (RGS, Game Engine, etc.)
   - What API endpoints/contracts changed?
   - What was the nature of changes? (new endpoint, modified response, etc.)
   - Is this a breaking change?
   - Which services consume this API? (from conversation or analysis)
   ```

4. **Confirm Scope**
   ```
   Before proceeding:
   - State what changes you detected
   - Ask if there are other services that need doc updates
   - Clarify if this should sync docs in other service repos
     (or just document the changes in current service)
   ```

### Phase 1: Change Detection

1. **Identify the Current Service**
   ```
   - Determine which service is being modified (RGS, Game Engine, Math Simulator, Backoffice, Website)
   - Use git diff or file analysis to detect changes
   - Scan for API endpoint modifications (routes, controllers)
   - Check for schema/interface changes
   ```

2. **Analyze Impact**
   ```
   Invoke microservices-orchestrator agent to:
   - Map service dependencies and consumers
   - Identify which services consume the modified APIs
   - Determine if changes are breaking or non-breaking
   - List affected integration points
   ```

### Phase 2: Documentation Discovery

1. **Find Documentation Files**
   ```
   In current service, locate:
   - API documentation (docs/api/, README.md, OpenAPI specs)
   - Integration guides (docs/integration/)
   - Architecture diagrams (docs/architecture/)
   - Service contracts (contracts/, interfaces/)
   ```

2. **Cross-Service Documentation**
   ```
   For each consuming service, locate:
   - Integration docs referencing this service
   - Client implementation examples
   - Configuration guides
   - Testing documentation
   ```

3. **Present Findings**
   ```
   Show user:
   - Current service docs that need updating
   - Affected services and their integration docs
   - Breaking vs non-breaking changes
   ```

### Phase 3: Documentation Update

1. **Update Current Service Docs**
   ```
   Use documentation-orchestrator agent to:
   - Update API documentation with new endpoints/schemas
   - Add/modify examples with new request/response formats
   - Update OpenAPI/Swagger specifications
   - Refresh integration guides
   - Update changelog with breaking changes
   ```

2. **Update Consuming Service Docs**
   ```
   For each affected service:
   - Update integration documentation
   - Modify client implementation examples
   - Update configuration guides
   - Add migration notes for breaking changes
   ```

3. **Version Documentation**
   ```
   If breaking changes detected:
   - Create v2 documentation sections
   - Maintain v1 docs for backward compatibility
   - Add migration guide from v1 to v2
   ```

### Phase 4: Validation & Summary

1. **Cross-Reference Check**
   ```
   Verify:
   - All API references are updated consistently
   - No orphaned documentation references
   - Examples match new API contracts
   - Version numbers are consistent
   ```

2. **Generate Summary Report**
   ```
   Documentation Changes:

   Current Service (e.g., RGS):
   ✅ Updated docs/api/spin-endpoint.md
   ✅ Updated swagger.json
   ✅ Added migration guide

   Affected Services:
   ✅ Game Engine: Updated docs/integration/rgs-client.md
   ✅ Math Simulator: Updated docs/testing/rgs-integration.md
   ✅ Backoffice: Updated docs/analytics/game-events.md

   Breaking Changes:
   ⚠️ Migration guide created: docs/migrations/v1-to-v2.md
   ```

## Service-Specific Documentation Patterns

### RGS Documentation
```
docs/
├── api/
│   ├── authentication.md
│   ├── game-sessions.md
│   ├── spin-endpoint.md
│   └── websocket-events.md
├── integration/
│   ├── game-engine-setup.md
│   └── math-simulator-setup.md
└── swagger.json
```

### Game Engine Documentation
```
docs/
├── integration/
│   ├── rgs-client.md
│   └── api-communication.md
├── game-development/
│   └── phaser-patterns.md
└── examples/
    └── spin-request.ts
```

### Math Simulator Documentation
```
docs/
├── api/
│   ├── simulation-runs.md
│   └── rtp-validation.md
├── integration/
│   └── rgs-integration.md
└── examples/
    └── simulate-game.ts
```

### Backoffice Documentation
```
docs/
├── api/
│   ├── game-configuration.md
│   └── analytics-endpoints.md
├── integration/
│   └── rgs-events.md
└── dashboards/
    └── game-analytics.md
```

### Website Documentation
```
docs/
├── api/
│   └── game-launcher.md
├── integration/
│   ├── authentication.md
│   └── rgs-session.md
└── user-flows/
    └── game-loading.md
```

## Handling Breaking Changes

When breaking API changes are detected:

1. **Version the Documentation**
   ```
   docs/api/v1/spin-endpoint.md  (keep for reference)
   docs/api/v2/spin-endpoint.md  (new version)
   ```

2. **Create Migration Guide**
   ```markdown
   # Migration Guide: RGS API v1 → v2

   ## Breaking Changes

   ### Spin Endpoint Response Format

   **v1 (deprecated):**
   ```json
   {
     "result": {...},
     "balance": 1000
   }
   ```

   **v2 (current):**
   ```json
   {
     "round": {
       "id": "xyz",
       "outcome": {...}
     },
     "player": {
       "balance": 1000
     }
   }
   ```

   ## Migration Steps
   1. Update client to handle new response structure
   2. Test with both v1 and v2 endpoints
   3. Switch to v2 endpoint
   4. Remove v1 compatibility layer
   ```

3. **Notify Consuming Services**
   ```
   Add notices to all consuming service docs:

   ⚠️ **BREAKING CHANGE**: RGS Spin API updated to v2
   See [migration guide](../migrations/rgs-v1-to-v2.md)
   v1 will be deprecated on [date]
   ```

## Best Practices

1. **Always Update Examples**
   - Code examples should match current API contracts
   - Include request AND response examples
   - Show error handling patterns

2. **Maintain Changelog**
   - Document all API changes in CHANGELOG.md
   - Include version numbers and dates
   - Link to migration guides for breaking changes

3. **Cross-Link Documentation**
   - Link from API docs to integration guides
   - Link from consuming services back to source service
   - Create clear navigation paths

4. **Version OpenAPI Specs**
   - Update Swagger/OpenAPI specs with each change
   - Include version in spec file name (swagger-v2.json)
   - Auto-generate docs from specs when possible

5. **Test Documentation**
   - Ensure examples actually work
   - Validate API contracts match implementation
   - Check links aren't broken

## Example Usage

### Scenario 1: Non-Breaking API Addition
```
User: /sync-service-docs

Claude:
### Change Detection
- Service: RGS
- Change: Added /api/v1/games/{id}/bonus-buy endpoint
- Type: Non-breaking (addition)

### Affected Services
- Game Engine (will use new endpoint)
- Backoffice (needs to display bonus buy data)

### Documentation Updates
1. RGS: Added docs/api/bonus-buy.md
2. RGS: Updated swagger.json
3. Game Engine: Updated docs/integration/rgs-client.md with bonus buy example
4. Backoffice: Updated docs/analytics/game-features.md

✅ All documentation synchronized
```

### Scenario 2: Breaking API Change
```
User: /sync-service-docs

Claude:
### Change Detection
- Service: RGS
- Change: Modified /api/v1/games/{id}/spin response format
- Type: ⚠️ BREAKING CHANGE

### Affected Services
- Game Engine (critical - client will break)
- Math Simulator (important - testing affected)
- Backoffice (low - only analytics)

### Documentation Updates
1. RGS: Created docs/api/v2/spin-endpoint.md
2. RGS: Maintained docs/api/v1/spin-endpoint.md (deprecated)
3. RGS: Created docs/migrations/v1-to-v2.md
4. RGS: Updated swagger-v2.json
5. Game Engine: Updated integration docs with migration path
6. Math Simulator: Updated test examples
7. Backoffice: Updated analytics event parsing

⚠️ Breaking change detected - deprecation timeline recommended:
- 2 weeks: v1 and v2 run in parallel
- 4 weeks: v1 deprecated
- 6 weeks: v1 removed

✅ All documentation synchronized with migration guides
```

## Integration with Agents

- **microservices-orchestrator**: Identifies service dependencies and impact
- **documentation-orchestrator**: Performs actual documentation updates
- **code-review-expert**: Validates documentation accuracy
- **slot-game-specialist**: Reviews game-specific API documentation

## Output Format

When sync completes, provide:

```markdown
## Documentation Sync Complete

### Changes Detected
- Service: [service name]
- Change Type: [breaking/non-breaking]
- Affected APIs: [list of endpoints/contracts]

### Documentation Updated

**Current Service:**
- [list of updated docs with file paths]

**Consuming Services:**
- [service]: [list of updated integration docs]

### Migration Guides Created
- [list any migration guides created]

### Next Steps
- [ ] Review updated documentation
- [ ] Test API examples in documentation
- [ ] Notify team of breaking changes (if any)
- [ ] Update internal API registry/catalog
```

## Error Handling

If documentation sync encounters issues:

```markdown
⚠️ Documentation Sync Issues

### Unable to Update
- [service]: [reason - e.g., "docs directory not found"]

### Recommendations
- Create missing documentation structure
- Add OpenAPI spec for better automation
- Review service repository layout

Would you like me to create missing documentation structure?
```

---

**Remember**: This command ensures that when one service changes, all dependent services stay informed and their documentation remains accurate!
