# OJPM AI Context Setup Summary

Created: January 21, 2026

## What Was Created

### Repository Structure
```
OJPM-AI-Context/
├── README.md                          ✅ Created
├── SETUP_SUMMARY.md                   ✅ This file
├── apps/
│   ├── workflow/
│   │   └── CLAUDE.md                  ✅ Created (based on existing)
│   ├── ubermensch/
│   │   └── CLAUDE.md                  ✅ Created (based on repo analysis)
│   ├── bank-statement-parser/
│   │   └── CLAUDE.md                  ✅ Created (based on repo analysis)
│   └── oddbot/
│       └── CLAUDE.md                  ✅ Created (based on WorkFlow analysis)
├── shared/
│   ├── CONVENTIONS.md                 ✅ Created
│   ├── GCP_ENVIRONMENT.md             ✅ Created
│   └── DEPLOYMENT_CHECKLIST.md        ✅ Created
└── agents/
    ├── DIGITAL_CTO_GUIDE.md           ✅ Created
    ├── TASK_TEMPLATES.md              ✅ Created
    └── OVERNIGHT_WORKFLOW.md          ✅ Created
```

## What Was Discovered

### WorkFlow-1.0
- **Existing CLAUDE.md**: Yes (188 lines, comprehensive)
- **Tech Stack**: React 18 + TypeScript + Vite frontend, Node.js + Express + TypeScript backend
- **Database**: Firestore (primary), Airtable (source of truth for operational data)
- **GCP Project**: `work-order-tracker-3a515`
- **Service Account**: `ojpm-integration-sa@work-order-tracker-3a515.iam.gserviceaccount.com`
- **Contains OddBot**: Yes, in `backend/src/chat/`
- **Documentation Files Found**: 40+ .md files including ARCHITECTURE.md, DEPLOYMENT.md, CHANGELOG.md, and many feature-specific docs

### UBERMENSCH-1.0
- **Existing CLAUDE.md**: Yes (57 lines, basic)
- **Tech Stack**: React (Vite) frontend, Flask + SQLite backend
- **Languages**: JavaScript 59.5%, Python 39.7%
- **Video Library**: 1,318+ video files managed
- **Current Sprint**: 1 - Foundation & Quick Wins
- **Active Issues**: #28, #27

### bank-statement-parser
- **Existing CLAUDE.md**: No (created new)
- **Tech Stack**: TypeScript 97.7%, client/server structure
- **Infrastructure**: Google Cloud Platform, Firebase, Google Document AI
- **Commit History**: 353 commits
- **Documentation Found**: ARCHITECTURE.md, ROADMAP.md, README.md, FINDINGS.md, GPT_CONFIGURATION.md

### OddBot
- **Location**: Part of WorkFlow-1.0 repo at `backend/src/chat/`
- **Purpose**: Google Chat bot for field technicians
- **Commands**: clock in, clock out, start job, complete job, photos, notes, status
- **Firestore Collections**: tech_sessions, active_jobs, technicians, workOrders

## Repo Cleanup Recommendations

### WorkFlow-1.0 (40+ .md files)

**KEEP (Active/Essential)**:
- CLAUDE.md - AI context file
- README.md - Project overview
- ARCHITECTURE.md - System architecture
- DEPLOYMENT.md - Deployment instructions
- CHANGELOG.md - Version history

**REVIEW (May need consolidation)**:
- Multiple feature-specific .md files may overlap
- Consider consolidating into `/docs/` folder
- Some may be outdated based on implementation status

**ARCHIVE Candidates**:
- Historical implementation plans that are complete
- Old migration guides if migrations are done

### UBERMENSCH-1.0

**KEEP**:
- CLAUDE.md
- README.md
- IMPLEMENTATION_PLAN.md (active)
- UBERMENSCH_DESIGN_SPEC.md
- DEVELOPMENT_LOG.md

### bank-statement-parser

**KEEP**:
- README.md
- ARCHITECTURE.md
- ROADMAP.md
- FINDINGS.md

**ADD** (done via this setup):
- CLAUDE.md (created in this repo, should be copied to bank-statement-parser root)

## Next Steps for Ali

### Immediate (Today)

1. **Review and commit files to GitHub**
   - All files are created locally in `/sessions/hopeful-laughing-franklin/mnt/outputs/OJPM-AI-Context/`
   - Push to the `OJPM-AI-Context` repository

2. **Copy CLAUDE.md files to app repos**
   ```bash
   # Copy bank-statement-parser CLAUDE.md (it doesn't have one)
   cp apps/bank-statement-parser/CLAUDE.md ~/code/bank-statement-parser/CLAUDE.md

   # For WorkFlow and UBERMENSCH, compare and merge if needed
   # They already have CLAUDE.md files - decide if you want to replace or merge
   ```

### This Week

3. **Create Claude Project**
   - Go to claude.ai → Projects → New Project
   - Name: "OJPM App Development"
   - Upload all files from this repo
   - Set custom instructions (see below)

4. **Fill in placeholders in GCP_ENVIRONMENT.md**
   - UBERMENSCH GCP project (if any)
   - bank-statement-parser GCP project details

5. **Test the workflow**
   - Pick a small GitHub issue
   - Use TASK_TEMPLATES.md
   - Verify AI agent reads CLAUDE.md

### Optional

6. **Set up overnight workflow**
   - Start with one simple task
   - Use OVERNIGHT_WORKFLOW.md guide

## Claude Project Setup Instructions

1. Go to claude.ai and click "Projects" in the sidebar
2. Click "New Project"
3. Name it: "OJPM App Development"
4. Add description: "AI context for all OJPM applications - WorkFlow, UBERMENSCH, bank-statement-parser, OddBot"
5. Upload these files from this repo:
   - All files in /apps/
   - All files in /shared/
   - All files in /agents/
6. Set custom instructions:

```
You are helping with development of OJPM applications. Always read the relevant CLAUDE.md file before working on any app. Follow the conventions in shared/CONVENTIONS.md. Use the deployment checklist before any deployment. When unsure, reference the Digital CTO Guide for workflow guidance.

Key apps:
- WorkFlow 1.0: Main business management platform
- UBERMENSCH 1.0: Personal fitness app
- bank-statement-parser: PDF transaction extraction
- OddBot: Google Chat bot (part of WorkFlow)

Always verify GCP project before any deployment:
- Production: work-order-tracker-3a515
- Never use deprecated test projects
```

## Open Questions

1. **UBERMENSCH GCP Setup**: Does UBERMENSCH use GCP/Firebase? If so, what's the project ID?

2. **bank-statement-parser Deployment**: Is this deployed anywhere or just run locally?

3. **WorkFlow Documentation**: The repo has 40+ .md files - should we consolidate these? Many appear to be implementation plans that may be outdated.

4. **OddBot Separation**: OddBot currently lives in WorkFlow. Should it remain there or be extracted? The current setup works but means OddBot changes require WorkFlow deployment.

5. **Sync Strategy**: How often should CLAUDE.md files be synced between this central repo and individual app repos?

## Summary

✅ Central repository created: `OJPM-AI-Context`
✅ CLAUDE.md files created for all 4 apps
✅ Shared documentation created (Conventions, GCP Environment, Deployment Checklist)
✅ Agent guides created (Digital CTO Guide, Task Templates, Overnight Workflow)
✅ Audit completed with recommendations

The AI context infrastructure is ready. Next step is to push these files to GitHub and create the Claude Project for daily use.
