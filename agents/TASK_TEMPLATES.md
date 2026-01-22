# Task Templates for AI Agents

Copy and customize these templates when assigning work to Claude Code or other AI agents.

## Template 1: Feature Implementation

```
## Context
Read CLAUDE.md first. Verify environment before making any changes.

## Task
Implement GitHub Issue #[XX]: [Title]

## Requirements
1. Create feature branch: feature/issue-[XX]-[short-description]
2. Implement the feature per the issue acceptance criteria
3. Make incremental commits with clear messages
4. Create a PR when complete

## Constraints
- Do NOT deploy
- Do NOT push to main
- If unsure about anything, STOP and document your question
```

## Template 2: Bug Fix

```
## Context
Read CLAUDE.md first. This is a bug fix - be careful not to introduce regressions.

## Task
Fix GitHub Issue #[XX]: [Bug Title]

## Requirements
1. Create fix branch: fix/issue-[XX]-[short-description]
2. Identify root cause before implementing fix
3. Implement minimal fix that resolves the issue
4. Add test if applicable
5. Create PR with explanation of what caused the bug and how the fix resolves it

## Constraints
- Do NOT deploy
- Do NOT change unrelated code
- If the bug is more complex than expected, STOP and report findings
```

## Template 3: Code Audit

```
## Context
Read CLAUDE.md first. This is an audit task - do not make changes unless specified.

## Task
Audit the codebase for [specific concern]

## Audit Areas
- [Area 1]
- [Area 2]
- [Area 3]

## Output
Create a report (AUDIT_REPORT.md) with:
1. Summary of findings
2. Specific issues found (file, line, description)
3. Recommended fixes (prioritized)
4. Estimated effort for each fix

## Constraints
- Do NOT make changes during audit
- Do NOT create PRs
- Just produce the report
```

## Template 4: Overnight Task List

```
## Context
Read CLAUDE.md first. This is an overnight run - work autonomously but safely.

## Tasks (in priority order)

### Task 1: [Description]
- Branch: [branch-name]
- Issue: #[XX]
- Expected output: PR ready for review

### Task 2: [Description]
- Branch: [branch-name]
- Issue: #[XX]
- Expected output: PR ready for review

## Constraints
- Do NOT deploy anything
- Do NOT push to main
- Do NOT merge PRs
- If you encounter errors, document them and move to next task
- Create OVERNIGHT_SUMMARY.md with status of each task when complete
```

## Template 5: Documentation Update

```
## Context
Read CLAUDE.md first. This is a documentation task.

## Task
Update documentation for [feature/component]

## Requirements
1. Review current documentation in [location]
2. Update to reflect current implementation
3. Add missing sections: [list specific sections]
4. Ensure code examples work
5. Create PR with changes

## Constraints
- Do NOT change code (documentation only)
- Keep same documentation style as existing docs
- If code examples are broken, note in PR but don't fix code
```

## Template 6: Test Coverage

```
## Context
Read CLAUDE.md first. This is a test-writing task.

## Task
Improve test coverage for [component/module]

## Requirements
1. Create test branch: test/[component-name]-coverage
2. Identify untested code paths
3. Write tests for critical paths first
4. Target [XX]% coverage (or reasonable increase)
5. Create PR with coverage report

## Constraints
- Do NOT modify implementation code
- Tests should be fast and deterministic
- Mock external services
- If you find bugs while testing, note them but don't fix (create issues instead)
```

## Template 7: Refactoring

```
## Context
Read CLAUDE.md first. This is a refactoring task - behavior must not change.

## Task
Refactor [component/module] to [improvement goal]

## Requirements
1. Create refactor branch: refactor/[short-description]
2. Ensure tests pass before starting
3. Make incremental, atomic commits
4. Ensure tests pass after each commit
5. Create PR with explanation of changes

## Constraints
- Do NOT change external behavior
- Do NOT add new features
- If refactoring reveals bugs, note them but maintain existing behavior
- If tests are insufficient, note this but proceed carefully
```

## Usage Tips

1. **Always include CLAUDE.md reference** - This ensures AI has context
2. **Be specific about constraints** - What NOT to do is as important as what to do
3. **Define "done" clearly** - Acceptance criteria should be testable
4. **Include escape hatches** - What should AI do if stuck?
5. **Scope appropriately** - Smaller, focused tasks get better results
