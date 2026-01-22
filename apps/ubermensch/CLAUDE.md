# CLAUDE.md - UBERMENSCH 1.0

## Project Overview

UBERMENSCH is a personal fitness application that combines workout tracking, video exercise library, and progress metrics. It provides a comprehensive health and fitness management experience.

**Target Users**: Individual fitness enthusiasts

## Tech Stack

### Frontend
- **Framework**: React (Vite)
- **Language**: JavaScript
- **Styling**: CSS/Tailwind

### Backend
- **Framework**: Flask (Python)
- **Database**: SQLite
- **Video Storage**: NAS with server-side transcoding

## Project Structure

```
UBERMENSCH-1.0/
├── frontend/                    # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   └── Dashboard.jsx   # Main dashboard component
│   │   └── ...
├── backend/
│   ├── src/
│   │   ├── models/
│   │   │   └── models.py       # Database models
│   │   └── routes/             # API routes
├── video_index.json            # Video library index (1,318 entries)
├── IMPLEMENTATION_PLAN.md      # Development roadmap
└── UBERMENSCH_DESIGN_SPEC.md   # Design specifications
```

## Key Files
- **Models**: `backend/src/models/models.py`
- **Video index**: `video_index.json` (1,318 entries)
- **API routes**: `backend/src/routes/`
- **Dashboard**: `frontend/src/components/Dashboard.jsx`

## Current Development Status

**Current Sprint**: 1 - Foundation & Quick Wins
**Active Issues**: #28, #27

See `IMPLEMENTATION_PLAN.md` for detailed implementation order and sprint planning.

## Development Commands

```bash
# Frontend
cd frontend && npm run dev

# Backend
cd backend && python -m flask run
```

## Video Library

The application manages 1,318+ video files stored on NAS with server-side transcoding for optimal playback.

## Related Documentation
- `IMPLEMENTATION_PLAN.md` - Sprint planning and feature roadmap
- `UBERMENSCH_DESIGN_SPEC.md` - UI/UX design specifications
- `DEVELOPMENT_LOG.md` - Development history and decisions
