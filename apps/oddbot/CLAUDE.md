# CLAUDE.md - OddBot

## Project Overview

OddBot is the Google Chat bot integration for OJPM field technicians. It enables time tracking, job management, photo uploads, and coordinator notifications directly from the Google Chat interface.

**Target Users**: OJPM field technicians

**Note**: OddBot is part of the WorkFlow-1.0 repository, not a standalone project.

## Location in WorkFlow Repo

```
WorkFlow-1.0/
└── backend/
    └── src/
        └── chat/          # OddBot lives here
            ├── handlers/  # Message handlers
            ├── commands/  # Command implementations
            └── utils/     # Chat utilities
```

## Tech Stack

- **Platform**: Google Chat API
- **Runtime**: Node.js + TypeScript (part of WorkFlow backend)
- **Database**: Firestore
- **Hosting**: Cloud Run (with WorkFlow backend)

## Commands

OddBot responds to these commands from technicians:

| Command | Description |
|---------|-------------|
| `clock in` | Start work session |
| `clock out` | End work session |
| `start job [address]` | Begin a job at location |
| `complete job` | Mark current job as done |
| `photos` | Upload job photos |
| `notes [text]` | Add notes to current job |
| `status` | Check current status |

## Firestore Collections Used

- `tech_sessions` - Technician clock in/out records
- `active_jobs` - Currently active job assignments
- `technicians` - Technician profiles and settings
- `workOrders` - Work order documents (read-only)

## Coordinator Notifications

OddBot sends notifications to coordinators when:
- Technician clocks in/out
- Job is started or completed
- Photos are uploaded
- Notes are added

## Environment Configuration

OddBot uses the same environment as WorkFlow backend:
- **GCP Project**: `work-order-tracker-3a515`
- **Service Account**: `ojpm-integration-sa@work-order-tracker-3a515.iam.gserviceaccount.com`

## Known Issues

1. **Test vs Production Chat Space**: Ensure you're testing in the correct Google Chat space
2. **Message Threading**: Some commands must be sent as direct messages, not in threads
3. **Photo Upload Limits**: Large photos may timeout - consider compression

## Development

Since OddBot is part of WorkFlow, development follows the same workflow:

```bash
cd WorkFlow-1.0/backend
npm run dev
```

Test commands locally using the Google Chat API test tools or deploy to staging.

## Related Files in WorkFlow

- `backend/src/chat/` - All OddBot code
- `backend/src/services/technicianService.ts` - Technician business logic
- `backend/src/services/jobService.ts` - Job management logic
