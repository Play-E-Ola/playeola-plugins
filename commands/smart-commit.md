---
name: smart-commit
description: Smart commit workflow - performs code review, fixes issues, updates documentation, and commits with proper message format
---

Execute a comprehensive smart commit workflow that ensures code quality before committing.

## Workflow

### Phase 1: Code Review
1. Invoke the `code-review-expert` agent to review all uncommitted changes
2. Analyze findings by severity (critical, important, suggestions)
3. Present review results to the user

### Phase 2: Fix Issues (if needed)
1. If critical or important issues found, ask user if they want to fix them
2. If user approves, implement the fixes
3. Re-run code review to verify fixes (optional)

### Phase 3: Documentation Update
1. Invoke the `documentation-orchestrator` agent to update relevant documentation
2. Ensure all docs reflect the code changes
3. Update implementation plans, specs, or API docs as needed

### Phase 4: Git Operations
1. Check git status to see all changes
2. Review recent commits to match commit message style
3. Stage all relevant files (`git add`)
4. Create descriptive commit message following this format:

```
<type>: <short summary>

<optional detailed description>

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

**Commit types:**
- `feat`: New feature
- `fix`: Bug fix
- `refactor`: Code refactoring
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

5. Execute commit with heredoc format for proper message formatting
6. Run `git status` after commit to verify success

### Phase 5: Summary
Present a summary of:
- Code review findings and fixes applied
- Documentation updates made
- Commit created with message

## Guidelines

### Code Review Analysis
- Focus on real issues, not nitpicks (unless it's a pattern)
- Prioritize critical bugs and security issues
- Consider performance implications
- Check adherence to project's Claude.md rules (if exists)

### Fixing Issues
- Only fix critical and important issues automatically
- For suggestions, present them but don't auto-fix
- Maintain code style consistency
- Test fixes work before committing

### Documentation Updates
- Update all affected documentation files
- Ensure API docs match code changes
- Update plan/status files if they exist
- Keep README current with significant changes

### Commit Messages
- Keep summary under 72 characters
- Use present tense ("add feature" not "added feature")
- Be specific about what changed and why
- Focus on the "why" in detailed description
- Follow existing commit message style in the repo

### What NOT to Commit
- Files containing secrets (.env, credentials.json)
- Temporary files or build artifacts
- node_modules or other dependencies
- Personal configuration files
- Large binary files (unless intentional)

## Example Usage

**User:** `/smart-commit`

**Assistant:**
```markdown
I'll perform a smart commit workflow for you.

### Phase 1: Code Review
Invoking code-review-expert agent...

#### Review Results
✅ No critical issues found
🟡 1 important issue:
- Missing error handling in `src/api/games/route.ts:45`

🟢 2 suggestions:
- Consider extracting business logic to service layer
- Add JSDoc comments for public API

### Phase 2: Fix Issues
The important issue (missing error handling) should be fixed before committing.
Should I implement the fix? (yes/no)

[User approves]

Fixed: Added try-catch block with proper error handling.

### Phase 3: Documentation Update
Invoking documentation-orchestrator agent...

Updated:
- `docs/api/games.md` - Added error response documentation
- `README.md` - Updated API examples with error handling

### Phase 4: Commit
Creating commit with message:

```
fix: add error handling to games API endpoint

Added try-catch block to handle API failures gracefully.
Updated documentation to reflect error responses.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

Committed successfully!

### Summary
- ✅ Code reviewed (1 issue fixed, 2 suggestions noted)
- ✅ Documentation updated (2 files)
- ✅ Commit created and verified
- 📝 Consider the 2 suggestions for future improvements

Ready to push or need to review the commit?
```

## Special Cases

### No Changes to Commit
If `git status` shows no changes:
```markdown
No changes detected to commit. Working directory is clean.
```

### Pre-commit Hooks Fail
If pre-commit hooks modify files:
1. Check if commit succeeded but files were modified
2. Review hook changes
3. If safe, amend the commit (only if not pushed and authored by current user)
4. Otherwise, create a new commit with hook changes

### Merge Conflicts
If there are merge conflicts:
```markdown
⚠️ Merge conflicts detected. Please resolve conflicts first before committing.
```

### Large Changes
If changes span many files or are complex:
1. Break down commit message into sections
2. List key changes in detailed description
3. Suggest creating multiple commits if appropriate

## Integration

**Uses These Agents:**
- `code-review-expert` - For comprehensive code review
- `documentation-orchestrator` - For documentation updates

**Called By:**
- User manual invocation: `/smart-commit`
- Potentially suggested by hooks after significant edits

**Related Commands:**
- `/create-pr` - Creates pull request after committing
- `/orchestrate` - May invoke /smart-commit as part of larger workflow

## Configuration

### Project-Specific Behavior
- Reads `Claude.md` for project rules (via code-review-expert)
- Adapts to project's documentation structure (via documentation-orchestrator)
- Matches existing commit message style in repo
- Respects `.gitignore` for files to exclude

### User Preferences
- Can skip code review phase if user specifies
- Can skip documentation update if not needed
- Can customize commit message before committing
- Can abort at any phase

---

**Goal**: Make committing effortless while ensuring quality, consistency, and proper documentation. Every commit should be production-ready.
