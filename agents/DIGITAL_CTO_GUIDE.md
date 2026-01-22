# Digital CTO Guide

A comprehensive guide for using AI agents to handle development with minimal oversight.

## What is the Digital CTO Concept?

The "Digital CTO" approach treats AI coding agents (Claude Code, Cursor, Copilot) as capable junior developers who can work autonomously on well-defined tasks. Instead of writing code yourself, you:

1. Define clear requirements in GitHub issues
2. Provide context via CLAUDE.md files
3. Set guardrails and constraints
4. Review and approve completed work

This shifts your role from "developer" to "technical product manager" - you focus on WHAT needs to be built while AI handles HOW.

## The CLAUDE.md Foundation

### Why It Matters

AI agents are stateless - they don't remember your codebase between sessions. CLAUDE.md files serve as persistent memory:

- Tech stack and architecture decisions
- Project structure and key files
- Environment configuration
- Known issues and gotchas
- Coding conventions

### Keeping It Updated

Update CLAUDE.md when:
- Adding new dependencies or services
- Changing deployment configuration
- Discovering new gotchas or issues
- Completing major features

Keep it concise - AI agents have context limits. Focus on information that changes behavior.

## Plan Mode Workflow

Claude Code has a powerful "Plan Mode" for complex tasks:

1. **Activate**: Press `Shift+Tab` twice in Claude Code
2. **Plan Phase**: AI analyzes the task and proposes an approach
3. **Review**: You approve, modify, or reject the plan
4. **Execute**: AI implements the approved plan

Use Plan Mode for:
- Multi-file changes
- Complex features
- Unfamiliar areas of codebase
- Anything that could go wrong

## Issue-Driven Development

### Writing AI-Friendly Issues

Good issues for AI include:

```markdown
## Problem
[What's wrong or what's missing - be specific]

## Acceptance Criteria
- [ ] Criterion 1 (testable)
- [ ] Criterion 2 (testable)
- [ ] Criterion 3 (testable)

## Technical Notes
- Relevant file: `src/components/UserProfile.tsx`
- Related to: #45, #47
- Constraint: Must maintain backward compatibility

## Out of Scope
- [What NOT to change]
```

### Bad Issues (Don't Do This)

- "Make the app better"
- "Fix the bugs"
- "Refactor the code"

These are too vague - AI will either do nothing or do too much.

## Overnight Autonomous Work

### Prerequisites

1. CLAUDE.md is accurate and up-to-date
2. Clear GitHub issues exist
3. You've tested similar tasks during the day

### Setup

1. Create `TONIGHT_TASKS.md` with prioritized tasks
2. Set clear constraints (no deploy, no main branch)
3. Define what "done" looks like for each task
4. Include escape hatches (what to do if stuck)

### Execution

```bash
claude "Read TONIGHT_TASKS.md and execute all tasks. Create OVERNIGHT_SUMMARY.md when complete."
```

### Morning Review (10 minutes)

1. Read OVERNIGHT_SUMMARY.md
2. Check PRs: `gh pr list`
3. Review and merge good PRs
4. Note any blockers for follow-up

## Guardrails: Safe vs. Needs Approval

### AI Can Safely Do

- Create feature branches
- Write and modify code in branches
- Run tests locally
- Create pull requests
- Add documentation
- Refactor existing code

### Needs Human Approval

- Merge to main
- Deploy to production
- Modify environment variables
- Change infrastructure (Cloud Run, Firebase settings)
- Delete data
- Modify security rules

### Never Allow (Hard Constraints)

Always include in task instructions:
- "Do NOT deploy"
- "Do NOT push to main"
- "Do NOT delete production data"

## Daily Workflow

### Morning (10 min)
1. Check overnight summary
2. Review PRs
3. Merge approved work
4. Create today's issues

### During Day
- Quick tasks: Direct Claude Code interaction
- Complex tasks: Plan Mode first
- Debugging: Pair with AI (you guide, it explores)

### Evening (5 min)
1. Create TONIGHT_TASKS.md
2. Prioritize issues for overnight
3. Start Claude Code with overnight prompt

## Measuring Success

Track these metrics to validate the approach:

### Time Metrics
- Hours coding before Digital CTO: _____
- Hours coding after Digital CTO: _____
- Hours reviewing AI work: _____

### Quality Metrics
- PRs merged without changes: ____%
- PRs requiring revisions: ____%
- Bugs introduced by AI: _____

### Target State
- Coding time reduced by 80%+
- Review time under 30 min/day
- AI work acceptance rate 85%+

## Common Pitfalls

1. **Too vague requirements** → AI produces wrong output
2. **No CLAUDE.md** → AI makes bad assumptions
3. **Skipping Plan Mode** → AI goes off track on complex tasks
4. **No constraints** → AI deploys when it shouldn't
5. **Not reviewing** → Bugs slip through

## Getting Started

1. Start with one simple, well-defined task
2. Use Plan Mode
3. Review the output carefully
4. Gradually increase complexity and autonomy
5. Add overnight runs once comfortable
