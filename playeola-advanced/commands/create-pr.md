---
name: create-pr
description: Comprehensive pull request creation workflow - reviews code quality, updates documentation, generates detailed PR descriptions, and creates production-ready pull requests
---

Execute a comprehensive pull request creation workflow that ensures high-quality, well-documented, and CTO-ready pull requests.

## Workflow

### Phase 0: Context Gathering

**IMPORTANT: Before creating the PR, gather context to write a comprehensive PR description.**

1. **Review Recent Conversation History**
   ```
   - Read the last 10-15 messages before this command was invoked
   - Understand what work was done and why
   - Note any design decisions, trade-offs, or discussions
   - Identify the problem being solved or feature being added
   - Look for testing approaches mentioned
   - Note any blockers or issues encountered and resolved
   ```

2. **Check Git Context**
   ```
   Run these commands:
   - `git status` - Verify there are changes/commits
   - `git branch --show-current` - Get current branch name
   - `git log origin/main..HEAD --oneline` - See all commits for PR
   - `git diff origin/main...HEAD --stat` - Overview of all changes
   - `git diff origin/main...HEAD` - Full diff for analysis
   ```

3. **Synthesize Work Context**
   ```
   Build understanding of the work:
   - What was implemented/fixed/changed?
   - Why was this work needed? (from conversation)
   - What approach was taken? (from conversation + commits)
   - What files were modified and why?
   - Were there any challenges overcome?
   - What testing was done? (from conversation)
   ```

4. **Use Context for PR Description**
   ```
   The gathered context will be used to:
   - Write accurate "Summary" section
   - Detail the "Motivation" clearly
   - List specific "Changes" based on commits
   - Document "Technical Details" from discussions
   - Fill "Testing" section with actual testing done
   - Note any "Breaking Changes" discussed
   ```

### Phase 1: Pre-PR Validation

1. **Check Git Status**
   ```
   - Verify there are uncommitted changes
   - Check current branch name
   - Ensure not on main/master branch
   - Verify remote tracking is set up
   ```

2. **Branch Name Analysis**
   ```
   Parse branch name for context:
   - feature/ABC-123-bonus-buy → Issue: ABC-123, Type: feature
   - fix/performance-dashboard → Type: fix
   - refactor/api-cleanup → Type: refactor

   Extract:
   - Issue number (if present)
   - PR type (feature/fix/refactor/docs/etc.)
   - Brief description
   ```

3. **Commit Analysis**
   ```
   Review recent commits on branch:
   - Read commit messages for context
   - Identify commit message style
   - Extract key changes mentioned
   - Determine PR scope
   ```

### Phase 2: Quality Checks

1. **Code Review**
   ```
   Invoke code-review-expert agent:
   - Review all uncommitted/unpushed changes
   - Identify critical issues that should block PR
   - Note important suggestions
   - Document any security concerns
   ```

2. **Fix Critical Issues** (if found)
   ```
   If critical issues found:
   - Present issues to user
   - Ask if they want to fix before creating PR
   - If yes: implement fixes, re-review
   - If no: include issues in PR description as "Known Issues"
   ```

3. **Documentation Check**
   ```
   Invoke documentation-orchestrator agent:
   - Check if documentation needs updates
   - Update relevant docs if needed
   - Ensure API docs match code changes
   - Update specs/plans if they exist
   ```

4. **Cross-Service Impact** (if applicable)
   ```
   If changes affect multiple services:
   - Invoke microservices-orchestrator
   - Analyze service impact
   - Ensure all affected service docs updated
   - Note any breaking changes
   ```

### Phase 3: PR Description Generation

1. **Analyze Changes**
   ```
   Review git diff since branch point:
   - Identify modified files and their purposes
   - Categorize changes (backend, frontend, config, tests)
   - Count additions/deletions
   - Identify key files
   ```

2. **Generate PR Title**
   ```
   Format: <type>: <brief description>

   Examples:
   - feat: add bonus buy feature to slot games
   - fix: resolve dashboard performance issues
   - refactor: improve API error handling
   - docs: update RGS integration guide

   Rules:
   - Start with type (feat/fix/refactor/docs/test/chore)
   - Use imperative mood ("add" not "added")
   - Keep under 72 characters
   - Be specific but concise
   ```

3. **Generate PR Body**
   ```
   Structure:

   ## Summary
   [2-3 sentences explaining what and why]

   ## Changes
   - [Key change 1]
   - [Key change 2]
   - [Key change 3]

   ## Motivation
   [Why was this change needed? What problem does it solve?]

   ## Technical Details
   [Any implementation details reviewers should know]

   ## Testing
   - [ ] Unit tests added/updated
   - [ ] Integration tests added/updated
   - [ ] Manual testing performed
   - [ ] Tested in [environment]

   ## Documentation
   - [ ] API documentation updated
   - [ ] README updated (if needed)
   - [ ] Comments added for complex logic

   ## Checklist
   - [ ] Code follows project guidelines
   - [ ] No console.log or debug code left
   - [ ] All tests passing
   - [ ] No merge conflicts
   - [ ] Reviewed own code first

   ## Screenshots/Examples (if applicable)
   [Add if UI changes or API examples]

   ## Breaking Changes
   [List any breaking changes or "None"]

   ## Related Issues
   Closes #[issue-number]
   Related to #[issue-number]

   ---
   🤖 Generated with [Claude Code](https://claude.com/claude-code)
   ```

4. **Enhance with Context**
   ```
   Add relevant details from:
   - Code review findings
   - Documentation updates made
   - Service impact analysis
   - Performance implications
   - Security considerations
   ```

### Phase 4: Reviewer Selection

1. **Analyze Changed Files**
   ```
   Identify file patterns:
   - Backend files → Backend engineers
   - Frontend files → Frontend engineers
   - Game logic → Game developers
   - Infrastructure → DevOps/Platform team
   - Documentation only → Technical writers
   ```

2. **Determine Reviewers**
   ```
   Based on changes:
   - Primary reviewer: Main domain expert
   - Secondary reviewer: Code quality/architecture
   - Optional: Stakeholders for significant features

   Note: Actual assignment depends on team structure
   Provide recommendations in PR description
   ```

### Phase 5: PR Creation

1. **Commit Any Remaining Changes**
   ```
   If documentation updates or fixes were made:
   - Stage all changes
   - Create commit with descriptive message
   - Push to remote branch
   ```

2. **Push Branch to Remote**
   ```
   If branch not yet pushed or has new commits:
   git push -u origin [branch-name]
   ```

3. **Create PR with gh CLI**
   ```bash
   gh pr create \
     --title "[generated title]" \
     --body "$(cat <<'EOF'
   [generated PR body]
   EOF
   )" \
     --base main \
     --head [branch-name]
   ```

4. **Add Labels** (if applicable)
   ```
   Based on PR content:
   - feature / bug / enhancement / documentation
   - frontend / backend / infrastructure
   - needs-review / ready-for-review
   - breaking-change (if applicable)

   gh pr edit [pr-number] --add-label "feature,backend"
   ```

5. **Link Issues**
   ```
   If issue numbers detected:
   - Automatically linked via "Closes #123" in description
   - Verify linking worked
   ```

### Phase 6: Summary & Next Steps

1. **Generate Summary Report**
   ```markdown
   ## PR Creation Complete! 🎉

   **PR #[number]:** [title]
   **URL:** [pr-url]

   ### Quality Checks
   ✅ Code Review: [summary]
   ✅ Documentation: [summary]
   ✅ [Other checks performed]

   ### PR Details
   - **Files Changed:** [count]
   - **Additions:** [count] / **Deletions:** [count]
   - **Reviewers:** [recommendations]
   - **Labels:** [labels added]

   ### Next Steps
   1. Review the PR yourself at [url]
   2. Notify your team
   3. Address any review comments
   4. Merge when approved

   💡 **Tip:** Keep an eye on CI/CD checks
   ```

## PR Description Templates

### Feature PR Template

```markdown
## Summary
Added [feature name] to [component/service]. This feature allows users to [benefit].

## Changes
- Added new API endpoint `POST /api/[endpoint]`
- Created [Component] component for [purpose]
- Updated database schema with [table/field]
- Added tests for [scenarios]

## Motivation
[Why was this feature needed? What user problem does it solve?]

## Technical Details
- Used [technology/library] for [reason]
- Implemented [pattern/approach] to handle [challenge]
- Performance considerations: [details]

## Testing
- [x] Unit tests added (coverage: [%])
- [x] Integration tests added
- [x] Manual testing in staging
- [x] Load testing performed

## Documentation
- [x] API documentation updated
- [x] User guide updated
- [x] Code comments added

## Checklist
- [x] Code follows project style guide
- [x] All tests passing
- [x] No merge conflicts
- [x] Reviewed own code

## Screenshots
[Add UI screenshots or API response examples]

## Breaking Changes
None

## Related Issues
Closes #123

---
🤖 Generated with [Claude Code](https://claude.com/claude-code)
```

### Bug Fix PR Template

```markdown
## Summary
Fixed [issue description] in [component/service].

## Changes
- Modified [file/function] to handle [case]
- Added validation for [scenario]
- Updated tests to cover [edge case]

## Root Cause
[What was causing the bug?]

## Solution
[How did you fix it?]

## Testing
- [x] Reproduced bug before fix
- [x] Verified fix resolves issue
- [x] Added regression test
- [x] Tested related functionality

## Checklist
- [x] Bug no longer reproducible
- [x] No side effects introduced
- [x] Tests passing

## Related Issues
Fixes #456

---
🤖 Generated with [Claude Code](https://claude.com/claude-code)
```

### Refactoring PR Template

```markdown
## Summary
Refactored [component/module] to improve [code quality/performance/maintainability].

## Changes
- Extracted [logic] into [new module]
- Simplified [complex function]
- Removed duplicate code in [files]
- Improved type safety with [TypeScript features]

## Motivation
[Why was this refactoring needed?]

## Benefits
- Improved performance by [metric]
- Reduced code duplication
- Better separation of concerns
- Easier to test and maintain

## Testing
- [x] All existing tests still passing
- [x] No functional changes
- [x] Performance benchmarks maintained/improved

## Checklist
- [x] No breaking changes
- [x] Code coverage maintained
- [x] Documentation updated if needed

---
🤖 Generated with [Claude Code](https://claude.com/claude-code)
```

## Best Practices

### PR Title Best Practices
1. Use conventional commit format (feat:, fix:, etc.)
2. Be specific: "Add bonus buy" not "Add feature"
3. Use imperative mood: "Add" not "Added" or "Adds"
4. Keep under 72 characters
5. Don't end with period

### PR Description Best Practices
1. **Start with why** - Explain the problem before the solution
2. **Be comprehensive but concise** - Include all necessary info, nothing more
3. **Use checklists** - Makes it clear what was done and what needs review
4. **Include visuals** - Screenshots for UI, examples for API
5. **Link issues** - Use "Closes #123" to auto-close issues
6. **Highlight breaking changes** - Make them obvious
7. **Add testing evidence** - Show that changes work
8. **Think like a reviewer** - What would you want to know?

### Quality Standards
Before creating PR, ensure:
- No critical issues from code review
- Documentation is up to date
- Tests are added/passing
- No debug code left behind
- No merge conflicts
- Branch is up to date with main

## Special Cases

### Large PRs

If PR is very large (>1000 lines):
```markdown
## ⚠️ Large PR Notice
This is a large PR with [X] files changed. To make review easier:

### Review Suggested Order
1. [Core changes] - Start here
2. [Supporting changes]
3. [Tests and docs]

### Key Files to Review
- `[file1]` - [why important]
- `[file2]` - [why important]

### Quick Context
[High-level summary of what changed and why]
```

### Breaking Changes

If PR contains breaking changes:
```markdown
## ⚠️ BREAKING CHANGES

### What's Breaking
- [Specific breaking change 1]
- [Specific breaking change 2]

### Migration Guide
1. [Step to update consumer code]
2. [Step to update configuration]
3. [Step to test changes]

### Timeline
- v1 API deprecated on [date]
- v1 API removed on [date]
- Migration deadline: [date]

### Support
[Who to contact for help]
```

### Security-Sensitive Changes

If PR touches security:
```markdown
## 🔒 Security Considerations

### Changes
- [What security-related changes were made]

### Security Review
- [x] No credentials in code
- [x] Input validation added
- [x] Authentication checked
- [x] Authorization verified
- [x] SQL injection prevented
- [x] XSS prevention confirmed

### Reviewed By
Security team review requested: @security-team
```

## Error Handling

### No Changes to Commit

```markdown
❌ Cannot create PR: No changes to commit

Your working directory is clean. Make some changes first, then run `/create-pr`.
```

### On Main/Master Branch

```markdown
❌ Cannot create PR from main/master branch

Please create a feature branch first:
```bash
git checkout -b feature/your-feature-name
```
Then make your changes and run `/create-pr` again.
```

### Critical Issues Found

```markdown
⚠️ Critical Issues Found

The code review found [N] critical issues that should be addressed before creating the PR:

[List of critical issues]

Options:
1. Fix these issues now (recommended)
2. Create PR anyway and document as "Known Issues"
3. Cancel PR creation

What would you like to do?
```

### gh CLI Not Available

```markdown
❌ GitHub CLI (gh) not found

To create PRs, please install GitHub CLI:
- macOS: `brew install gh`
- Linux: See https://cli.github.com/
- Windows: See https://cli.github.com/

After installing, authenticate: `gh auth login`
```

## Integration with Other Agents/Commands

- **Uses `code-review-expert`**: For quality validation
- **Uses `documentation-orchestrator`**: To update docs before PR
- **Uses `microservices-orchestrator`**: For cross-service impact
- **Works after `/smart-commit`**: Natural flow from commit to PR
- **Works with `agent-coordinator`**: For complex multi-agent coordination

---

**Goal**: Create production-ready, CTO-approved pull requests that are comprehensive, well-documented, and easy to review. Every PR should make reviewers think "This is exactly what I needed to see."
