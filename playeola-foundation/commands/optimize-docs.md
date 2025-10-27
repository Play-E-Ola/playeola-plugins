---
name: optimize-docs
description: Comprehensive documentation optimization workflow - audits all docs, removes obsolete files, updates outdated content, and improves structure for better navigation
---

Execute a comprehensive documentation optimization workflow that proactively audits, cleans up, and improves all project documentation to ensure accuracy, relevance, and ease of navigation.

## Overview

Unlike reactive documentation maintenance (which updates docs when code changes), this command performs a **proactive, comprehensive audit** of ALL documentation in the project. It identifies obsolete files, updates outdated content, improves organization, and validates technical accuracy.

**Use this when:**
- Starting work on an unfamiliar project (understand the docs landscape)
- Documentation feels scattered or outdated
- Want to ensure docs match current codebase
- Planning a major feature (need accurate context)
- Preparing for team onboarding

## Workflow

### Phase 0: Context Gathering

**IMPORTANT: Before analyzing documentation, gather context about the project.**

1. **Understand Project Type**
   ```
   - Check PWD and git remote to identify which Playeola project:
     * RGS (Remote Game Server)
     * Game Engine (Phaser-based slot games)
     * Math Simulator (RTP calculations)
     * Backoffice (Admin platform)
     * Website (Public platform)
   - Read Claude.md (if exists) to understand project-specific rules
   - Check package.json for tech stack and dependencies
   ```

2. **Review Recent Activity**
   ```
   Run these commands:
   - `git log --oneline -20` - See recent development activity
   - `git status` - Check current working state
   - `git branch -a` - Identify active branches

   This helps understand:
   - What areas of code are actively developed?
   - What might be legacy/deprecated?
   - What documentation is most likely outdated?
   ```

3. **Check Project Structure**
   ```
   - Identify key directories (src/, docs/, etc.)
   - Note any special documentation patterns
   - Understand how the project is organized
   ```

### Phase 1: Documentation Discovery

1. **Find All Documentation Files**
   ```
   Use ChunkHound MCP to discover documentation:

   Search queries:
   - "documentation files markdown"
   - "README spec plan guide"
   - "API documentation"

   Also use Glob to find:
   - All .md files: **/*.md
   - Common doc locations: docs/**/*.md, specs/**/*.md

   Build complete inventory of:
   - README files (project root, subdirectories)
   - Claude.md / development guidelines
   - API documentation (docs/api/, OpenAPI specs)
   - Feature specifications (specs/, docs/features/)
   - Implementation plans (plans/, SESSION_STATE.md)
   - Architecture docs (docs/architecture/)
   - Integration guides (docs/integration/)
   - Migration guides
   - Changelogs
   - Any other .md files in the project
   ```

2. **Categorize Documentation**
   ```
   Organize findings by type:

   **Core Documentation:**
   - README.md (project overview)
   - Claude.md / CLAUDE.md (dev guidelines)

   **Technical Documentation:**
   - API documentation files
   - Architecture diagrams/docs
   - Database schemas
   - Service contracts

   **Process Documentation:**
   - Feature specifications
   - Implementation plans
   - Session state files
   - Meeting notes

   **Reference Documentation:**
   - Integration guides
   - Migration guides
   - Troubleshooting guides
   - Changelog
   ```

3. **Present Documentation Inventory**
   ```
   Show user:
   - Total number of documentation files found
   - Breakdown by category
   - File sizes and last modified dates
   - Documentation structure (organized vs scattered)
   ```

### Phase 2: Documentation Analysis

For each documentation file, analyze:

1. **Relevance Assessment**
   ```
   Questions to answer:
   - Does this doc reference code that still exists?
   - Is the feature/service still active?
   - Are file paths/references still valid?
   - Has this been superseded by newer docs?

   Use ChunkHound to verify:
   - Search for functions/classes mentioned in docs
   - Check if API endpoints still exist
   - Validate file paths referenced
   - Find related code to verify relevance

   Mark as:
   ✅ Relevant (still accurate and needed)
   ⚠️ Partially outdated (needs updates)
   ❌ Obsolete (should be removed or archived)
   ```

2. **Accuracy Validation**
   ```
   For relevant docs, check accuracy:

   **Code Examples:**
   - Do code snippets use current syntax?
   - Are imports/dependencies correct?
   - Would examples actually run?

   **API References:**
   - Do endpoints still exist?
   - Are request/response formats current?
   - Are authentication methods up to date?

   **Technical Details:**
   - Are architecture diagrams current?
   - Do configuration examples work?
   - Are version numbers accurate?

   **File References:**
   - Do linked files still exist?
   - Are paths still valid?
   - Are cross-references working?
   ```

3. **Quality Assessment**
   ```
   Evaluate documentation quality:

   **Clarity:**
   - Is the purpose clear?
   - Are instructions easy to follow?
   - Is terminology consistent?

   **Completeness:**
   - Are there missing sections?
   - Do examples cover common use cases?
   - Is error handling documented?

   **Organization:**
   - Is structure logical?
   - Are headers hierarchical?
   - Is navigation easy?

   **Maintenance:**
   - Is there a clear update date?
   - Are deprecated sections marked?
   - Is ownership/contact info present?
   ```

4. **Structure Analysis**
   ```
   Assess overall documentation organization:

   - Is there a clear entry point (main README)?
   - Are related docs grouped logically?
   - Is there duplication across files?
   - Are there obvious gaps in coverage?
   - Would reorganization improve navigation?
   ```

### Phase 3: Optimization Plan

**CRITICAL: Present findings and get user approval before making changes.**

1. **Generate Findings Report**
   ```markdown
   ## Documentation Audit Results

   ### Summary
   - Total files: X
   - Relevant: Y (keep and maintain)
   - Outdated: Z (need updates)
   - Obsolete: N (recommend removal)
   - Gaps: M (missing critical docs)

   ### Files to Remove (Obsolete)

   1. **docs/old-api.md**
      - Reason: References deprecated v1 API removed in 2023
      - Last updated: 2022-03-15
      - No code references found
      - Recommendation: Remove (archive if needed)

   2. **specs/feature-x.md**
      - Reason: Feature was abandoned, code never merged
      - Last updated: 2023-06-01
      - Recommendation: Remove

   ### Files to Update (Outdated Content)

   1. **README.md**
      - Issues:
        * Setup instructions reference old Node version
        * Missing new analytics service in architecture
        * Code examples use deprecated syntax
      - Recommendation: Update sections 2, 4, and 7

   2. **docs/api/games.md**
      - Issues:
        * Endpoint `/api/v1/games` changed to `/api/v2/games`
        * Response format differs from docs
        * Missing new error codes
      - Recommendation: Complete rewrite needed

   ### Structure Improvements

   1. **Consolidate scattered API docs**
      - Current: API docs in 5 different locations
      - Recommendation: Create docs/api/ directory, move all there

   2. **Create missing index/navigation**
      - Recommendation: Add docs/README.md with links to all docs

   3. **Organize by feature domain**
      - Recommendation: Group related docs in feature directories

   ### Critical Gaps

   1. **Missing: Authentication guide**
      - Analytics service API not documented
      - Used by multiple features but no docs exist

   2. **Missing: Deployment documentation**
      - No deployment process documented
      - Team knowledge not captured

   ### Validation Issues

   1. **Broken code examples in docs/integration/rgs-client.md**
      - Import paths changed
      - API method signatures updated
      - Recommendation: Update all examples

   2. **Dead links in README.md**
      - 3 broken internal links
      - Recommendation: Fix or remove
   ```

2. **Get User Approval**
   ```
   Present the findings report and ask:

   "I've completed the documentation audit. Here are my recommendations:
   - Remove X obsolete files
   - Update Y outdated files
   - Reorganize Z files for better structure
   - Create M missing critical docs

   Would you like me to:
   1. Proceed with all recommendations?
   2. Proceed with specific changes only?
   3. Skip certain changes?

   I'll show you a detailed plan before making any changes."
   ```

3. **Create Detailed Execution Plan**
   ```
   After user approval, create step-by-step plan:

   Phase 4 Actions:
   1. Remove obsolete files: [list]
   2. Update outdated content in: [list]
   3. Reorganize structure: [describe changes]
   4. Create missing docs: [list]
   5. Fix validation issues: [list]

   Estimated time: X minutes
   ```

### Phase 4: Execution

**ONLY execute after user approval. Make changes incrementally.**

1. **Remove Obsolete Files**
   ```
   For each file marked for removal:

   - Verify no other docs link to it (use Grep)
   - Check git history to confirm low value
   - Remove the file
   - Update any indices/navigation
   - Log the removal for summary

   Note: Consider archiving instead of deleting:
   - Create archive/ directory for historical reference
   - Move instead of delete if user prefers
   ```

2. **Update Outdated Content**
   ```
   Invoke documentation-orchestrator agent to:

   - Update technical accuracy (API references, code examples)
   - Fix broken links and file references
   - Update version numbers and dates
   - Improve clarity where needed
   - Ensure consistency with codebase

   For each update:
   - Use Edit tool for surgical changes
   - Maintain existing format and style
   - Preserve valuable historical context
   - Update "last modified" timestamps
   ```

3. **Reorganize Structure**
   ```
   If structure improvements needed:

   - Create new directories (docs/api/, docs/features/, etc.)
   - Move files to logical locations
   - Update all cross-references
   - Create index/navigation files
   - Ensure no broken links introduced

   Common reorganization patterns:

   **Before:**
   ```
   /
   ├── README.md
   ├── api-docs.md
   ├── feature-a.md
   ├── integration-guide.md
   └── random-notes.md
   ```

   **After:**
   ```
   /
   ├── README.md
   ├── docs/
   │   ├── README.md (index)
   │   ├── api/
   │   │   └── endpoints.md
   │   ├── features/
   │   │   └── feature-a.md
   │   └── integration/
   │       └── setup-guide.md
   ```
   ```

4. **Create Missing Documentation**
   ```
   For critical gaps identified:

   - Create documentation scaffolds
   - Add placeholders for sections
   - Document what's currently known
   - Mark TODOs for areas needing more detail
   - Add to documentation index

   Example: Creating missing API documentation:
   - Generate from code analysis
   - Extract endpoint signatures
   - Create example requests/responses
   - Document error cases
   - Add authentication requirements
   ```

5. **Fix Validation Issues**
   ```
   - Update broken code examples
   - Fix dead links
   - Correct file path references
   - Update deprecated syntax
   - Ensure examples run correctly
   ```

### Phase 5: Summary and Next Steps

1. **Generate Change Report**
   ```markdown
   ## Documentation Optimization Complete

   ### Changes Made

   **Removed (X files):**
   - docs/old-api.md - Deprecated API documentation
   - specs/abandoned-feature.md - Abandoned spec

   **Updated (Y files):**
   - README.md - Updated setup instructions, architecture, examples
   - docs/api/games.md - Rewrote for v2 API
   - docs/integration/client.md - Fixed code examples

   **Reorganized:**
   - Created docs/api/ directory
   - Moved 5 API docs to centralized location
   - Created docs/README.md navigation index

   **Created (Z files):**
   - docs/api/analytics.md - New analytics API documentation
   - docs/deployment.md - Deployment process guide

   **Fixed:**
   - 8 broken code examples
   - 3 dead links
   - 12 outdated file references

   ### Documentation Structure (After Optimization)

   ```
   /
   ├── README.md (updated - main entry point)
   ├── Claude.md (unchanged - current)
   ├── docs/
   │   ├── README.md (new - navigation index)
   │   ├── api/
   │   │   ├── analytics.md (new)
   │   │   ├── games.md (updated)
   │   │   └── authentication.md (updated)
   │   ├── features/
   │   │   └── feature-specs.md (updated)
   │   ├── integration/
   │   │   ├── setup-guide.md (reorganized)
   │   │   └── client.md (updated)
   │   └── deployment.md (new)
   └── archive/
       ├── old-api.md (moved)
       └── abandoned-feature.md (moved)
   ```

   ### Documentation Quality Metrics

   **Before:**
   - Total files: 25
   - Relevant: 15
   - Outdated: 7
   - Obsolete: 3
   - Quality score: 60%

   **After:**
   - Total files: 22
   - Relevant: 22
   - Outdated: 0
   - Obsolete: 0
   - Quality score: 95%

   ### Next Steps

   1. ✅ Documentation is now optimized and accurate
   2. 📝 Consider running `/smart-commit` to commit changes
   3. 🔄 Set up recurring optimization (monthly/quarterly)
   4. 📚 Share updated docs with team
   5. 🎯 Fill remaining TODO sections in new docs
   ```

2. **Provide Navigation Guide**
   ```
   Help user understand the optimized documentation:

   "Here's how to navigate the documentation now:

   **Start here:**
   - README.md - Project overview and quick start

   **For API integration:**
   - docs/api/README.md - API documentation index
   - docs/integration/ - Integration guides

   **For feature development:**
   - Claude.md - Development guidelines
   - docs/features/ - Feature specifications

   **For deployment:**
   - docs/deployment.md - Deployment process

   All documentation is now accurate and reflects the current codebase!"
   ```

3. **Suggest Follow-up Actions**
   ```
   - Run `/smart-commit` to commit documentation improvements
   - Schedule regular doc optimization (monthly recommended)
   - Set up documentation linting/validation
   - Create documentation contribution guidelines
   - Consider auto-generating API docs from code
   ```

## Guidelines

### Analysis Best Practices

1. **Be Thorough**
   - Check every documentation file
   - Validate all code examples
   - Test all links and references
   - Don't skip "small" docs

2. **Use ChunkHound Effectively**
   - Search for code referenced in docs
   - Verify API endpoints exist
   - Find related implementations
   - Discover documentation patterns

3. **Preserve History**
   - Archive rather than delete when uncertain
   - Keep valuable historical context
   - Document why things changed
   - Maintain attribution

### Update Best Practices

1. **Maintain Style**
   - Match existing documentation tone
   - Keep consistent formatting
   - Preserve project-specific conventions
   - Don't over-engineer

2. **Improve Incrementally**
   - Fix obvious issues first
   - Don't rewrite unnecessarily
   - Preserve working examples
   - Update progressively

3. **Validate Changes**
   - Test updated code examples
   - Verify links work
   - Check cross-references
   - Ensure accuracy

### Organization Best Practices

1. **Logical Structure**
   - Group by domain/feature
   - Separate API from guides
   - Create clear navigation
   - Use consistent naming

2. **Discoverability**
   - Create index/README files
   - Use descriptive filenames
   - Add front matter metadata
   - Cross-link related docs

3. **Scalability**
   - Organize for growth
   - Don't create deep nesting
   - Keep flat when possible
   - Use subdirectories purposefully

## Project-Specific Patterns

### RGS Projects
```
Common docs structure:
docs/
├── api/          # Game session, spin endpoints
├── services/     # Microservices documentation
├── integration/  # Client integration guides
└── architecture/ # System design docs

Focus on:
- API contract accuracy
- Service communication docs
- WebSocket event documentation
```

### Game Engine Projects
```
Common docs structure:
docs/
├── games/        # Individual game documentation
├── phaser/       # Phaser integration guides
├── features/     # Game feature specs
└── math/         # Game math documentation

Focus on:
- Game configuration accuracy
- Phaser API usage examples
- Math formula documentation
```

### Math Simulator Projects
```
Common docs structure:
docs/
├── api/          # Simulation API
├── simulations/  # Simulation scenarios
├── rtp/          # RTP calculation docs
└── validation/   # Validation guides

Focus on:
- RTP calculation accuracy
- Simulation parameter docs
- Statistical analysis guides
```

### Backoffice Projects
```
Common docs structure:
docs/
├── api/          # Admin API endpoints
├── dashboards/   # Dashboard documentation
├── features/     # Feature specifications
└── analytics/    # Analytics guides

Focus on:
- API endpoint accuracy
- Dashboard component docs
- Analytics integration guides
```

### Website Projects
```
Common docs structure:
docs/
├── api/          # Public API
├── components/   # UI component docs
├── integration/  # Third-party integrations
└── deployment/   # Deployment guides

Focus on:
- Public API documentation
- Component usage examples
- Integration guides
```

## Special Considerations

### Handling Sensitive Documentation

Some docs may contain sensitive information:
```
- Don't accidentally commit secrets
- Redact sensitive examples
- Mark confidential sections
- Archive securely if needed
```

### Documentation Versioning

For versioned projects:
```
- Maintain docs for supported versions
- Mark deprecated versions clearly
- Create migration guides between versions
- Archive old version docs properly
```

### Multi-Repository Projects

For microservices or multi-repo projects:
```
- Optimize docs in current repo only
- Note cross-repo documentation references
- Suggest running in other repos
- Maintain consistency across repos
```

### Large Documentation Sets

For projects with 50+ doc files:
```
- Prioritize critical documentation first
- Present summary-level findings
- Offer to optimize in phases
- Create optimization roadmap
```

## Error Handling

### When Documentation is Minimal
```markdown
📊 Documentation Audit Results

This project has minimal documentation (3 files found).

**Recommendations:**
1. Create foundational docs:
   - README.md (setup and overview)
   - Claude.md (development guidelines)
   - docs/api/ (if applicable)

Would you like me to create a documentation structure?
```

### When Documentation is Excellent
```markdown
✅ Documentation Audit Complete

Great news! Your documentation is in excellent shape:
- All files are relevant and accurate
- Structure is well-organized
- No obsolete content found
- Code examples are current

**Minor suggestions:**
- Add deployment guide
- Update Node version in README

Would you like me to implement these small improvements?
```

### When Changes Are Extensive
```markdown
⚠️ Extensive Changes Needed

The documentation audit found significant issues:
- 15 obsolete files
- 23 files need updates
- Major reorganization recommended

This is a substantial optimization project.

**Options:**
1. Proceed with full optimization (45-60 minutes)
2. Prioritize critical updates only (20 minutes)
3. Create optimization roadmap for incremental work

Which approach would you prefer?
```

## Integration with Other Commands

**Works with:**
- **`/smart-commit`** - Commit documentation improvements after optimization
- **`/sync-service-docs`** - Follow up with cross-service sync if APIs updated
- **`/create-pr`** - Create PR for documentation improvements
- **`/orchestrate`** - Can be part of larger project maintenance workflow

**Invokes:**
- **`documentation-orchestrator` agent** - For updating file content
- **ChunkHound MCP** - For code discovery and validation
- Uses Glob, Grep, Read, Edit, Write tools extensively

## Usage Examples

### Example 1: Starting on New Project
```
User: I just joined this project and the docs seem scattered. Can you help?

Claude: I'll run a comprehensive documentation audit using /optimize-docs.

[Runs workflow...]

Found 18 documentation files across 6 directories. Here's what I found:
- 3 obsolete files (old APIs removed last year)
- 7 files need updates (API changes not reflected)
- Documentation is scattered (no clear organization)

I can:
1. Remove the 3 obsolete files
2. Update the 7 outdated files
3. Reorganize into clear docs/ structure
4. Create navigation index

This will give you a clear, accurate documentation landscape. Proceed?
```

### Example 2: Pre-Feature Planning
```
User: I need to add a bonus buy feature. Let me check docs first.

Claude: Let me optimize the documentation first so you have accurate context.

[Runs /optimize-docs...]

Documentation is now optimized! Here's what changed:
- Updated API docs to reflect current endpoints
- Fixed game math documentation (RTP calculations)
- Created missing feature spec template

For bonus buy planning, check:
- docs/api/games.md - Updated game API endpoints
- docs/features/ - Feature spec templates
- docs/math/rtp.md - RTP calculation guidelines

Ready to start feature planning with accurate docs!
```

### Example 3: Team Onboarding
```
User: /optimize-docs

Claude: Running comprehensive documentation optimization...

[Analysis complete]

Optimized documentation for team onboarding:

**Created:**
- docs/README.md - Documentation navigation hub
- docs/onboarding.md - New developer guide
- docs/deployment.md - Deployment process

**Updated:**
- README.md - Current setup instructions
- All code examples now work with current codebase

**Reorganized:**
- Clear docs/ structure by domain
- Easy navigation from README

Your documentation is now onboarding-ready! New team members have a clear path from setup to deployment.
```

## Maintenance Schedule

Recommend running `/optimize-docs`:

- **Monthly**: For active projects with frequent changes
- **Quarterly**: For stable projects with occasional updates
- **Before major releases**: Ensure docs match release state
- **After large refactors**: Update all affected documentation
- **When onboarding**: Ensure newcomers have accurate docs
- **When documentation feels wrong**: Trust your instincts!

---

**Remember**: Documentation is the foundation for effective development. Well-organized, accurate docs accelerate feature development, reduce confusion, and enable better planning. Invest in your documentation, and it will pay dividends in development velocity and team understanding!
