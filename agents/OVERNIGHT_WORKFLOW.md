# Overnight Autonomous Workflow

How to set up Claude Code to work while you sleep.

## Prerequisites

1. CLAUDE.md is in the repo root
2. Clear GitHub issues exist for the work
3. You've tested Claude Code on similar tasks during the day

## Setup

### 1. Create Tonight's Task File

Create a file called `TONIGHT_TASKS.md` in your repo:

```markdown
# Tonight's Tasks - [Date]

## Context
Read CLAUDE.md first. All work in feature branches, no deployments.

## Tasks

### 1. Issue #[XX] - [Title]
Priority: High
Branch: feature/issue-XX
Acceptance: [What "done" looks like]

### 2. Issue #[YY] - [Title]
Priority: Medium
Branch: feature/issue-YY
Acceptance: [What "done" looks like]

## If You Get Stuck
- Document the blocker in BLOCKERS.md
- Move to the next task
- Do not spend more than 30 minutes on any single error

## When Complete
Create OVERNIGHT_SUMMARY.md with:
- Tasks completed
- PRs created
- Blockers encountered
- Questions for morning review
```

### 2. Start Claude Code

```bash
cd /path/to/repo
claude "Read TONIGHT_TASKS.md and execute all tasks. Create OVERNIGHT_SUMMARY.md when complete."
```

### 3. Let It Run

- Keep terminal open (or use tmux/screen)
- Claude Code will work through tasks
- Check in the morning

## Morning Review (10 minutes)

```bash
# 1. Check the summary
cat OVERNIGHT_SUMMARY.md

# 2. Review PRs created
gh pr list

# 3. Check for blockers
cat BLOCKERS.md 2>/dev/null || echo "No blockers"

# 4. Review and merge good PRs
gh pr view [number]
gh pr merge [number] --squash

# 5. Clean up task files
rm TONIGHT_TASKS.md OVERNIGHT_SUMMARY.md BLOCKERS.md 2>/dev/null
```

## Tips for Success

1. **Start small** - First overnight run should be 1-2 simple tasks
2. **Clear acceptance criteria** - Vague tasks lead to vague results
3. **Include rollback instructions** - What to do if something breaks
4. **Check logs in morning** - Even successful runs may have warnings worth noting

## Example: Full Overnight Session

### Evening Setup (5 min)

```markdown
# TONIGHT_TASKS.md - January 21, 2026

## Context
Read CLAUDE.md. WorkFlow 1.0 app. No deployments.

## Tasks

### 1. Issue #142 - Add loading spinner to dispatch page
Priority: High
Branch: feature/issue-142-dispatch-spinner
Acceptance:
- Spinner shows while data loads
- Spinner hides when data arrives
- Spinner shows for error states with retry button

### 2. Issue #138 - Fix technician name sorting
Priority: Medium
Branch: fix/issue-138-tech-sorting
Acceptance:
- Names sort alphabetically (last name first)
- Sorting persists across page refresh
- Add test for sorting logic

### 3. Issue #145 - Update README with new env vars
Priority: Low
Branch: docs/issue-145-readme-env
Acceptance:
- Document GOOGLE_MAPS_API_KEY
- Document AIRTABLE_API_KEY
- Add example .env.example file

## Constraints
- NO deployments
- NO main branch changes
- NO merging PRs

## If Stuck
- Document in BLOCKERS.md
- Move to next task
- Max 30 min per blocker
```

### Morning Review

```markdown
# OVERNIGHT_SUMMARY.md

## Completed
- ✅ Issue #142: PR #156 created (dispatch spinner)
- ✅ Issue #138: PR #157 created (tech sorting)
- ✅ Issue #145: PR #158 created (README update)

## PRs Ready for Review
1. PR #156 - 3 files changed, tests passing
2. PR #157 - 2 files changed, new test added
3. PR #158 - 2 files changed, documentation only

## Blockers
None encountered.

## Questions
- Issue #138: Found inconsistent casing in existing names (e.g., "mcdonald" vs "McDonald"). Should I normalize? Created as Issue #159.

## Time Spent
- Task 1: 45 minutes
- Task 2: 30 minutes
- Task 3: 15 minutes
- Total: ~1.5 hours active work
```

## Troubleshooting

### Claude Code Stopped Mid-Task

Common causes:
- Network interruption
- Context limit reached
- Waiting for user input

Solution: Restart with same prompt. Claude Code will check existing branches and continue.

### PR Has Issues

Options:
1. Comment on PR with corrections, ask Claude to fix
2. Fix manually and push
3. Close PR and create new issue with clearer requirements

### Wrong Branch/Repo

Always verify at morning review:
```bash
git branch -a  # Check branches created
git log --oneline -5  # Check recent commits
gh pr list  # Check PRs
```

## Advanced: Multiple Repos

For overnight work across multiple repos, create a master task file:

```markdown
# TONIGHT_MASTER.md

## Repo 1: WorkFlow-1.0
cd ~/code/WorkFlow-1.0
Tasks: #142, #138

## Repo 2: bank-statement-parser
cd ~/code/bank-statement-parser
Tasks: #45

## Instructions
Complete Repo 1 tasks first, then Repo 2.
Create separate OVERNIGHT_SUMMARY.md in each repo.
```

Use a wrapper script or run separate Claude Code sessions.
