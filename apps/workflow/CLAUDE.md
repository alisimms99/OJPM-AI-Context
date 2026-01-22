# CLAUDE.md - OJPM WorkFlow 1.0

## Project Overview

OJPM WorkFlow is a full-stack property maintenance management system that streamlines operations from work order intake through completion. It manages technician dispatch, route optimization, AI-powered estimation, and financial integration.

**Target Users**: Admin staff (dispatchers, office managers) and field technicians

## Tech Stack

### Frontend
- **Framework**: React 18 + TypeScript + Vite
- **Routing**: React Router v6 (client-side)
- **Styling**: Tailwind CSS + Shadcn UI
- **State**: React Context + TanStack Query
- **HTTP**: Axios
- **Maps**: Google Maps React API

### Backend
- **Runtime**: Node.js + Express.js + TypeScript
- **Primary Database**: Google Cloud Firestore (NoSQL)
- **Secondary Data Store**: Airtable (operational data)
- **Auth**: Firebase Auth with Google OAuth + JWT
- **Storage**: Firebase Storage

### External Integrations
- Google Maps API (Places, Routes, Geocoding)
- Airtable API
- QuickBooks API (OAuth)
- Gmail API (document processing)
- Google Gemini & OpenAI (AI services via Delta Engine)
- Google Document AI (work order parsing)

## Project Structure

```
WorkFlow-1.0/
├── frontend/           # React frontend
│   ├── src/
│   │   ├── components/ # UI components
│   │   ├── pages/      # Route pages
│   │   ├── hooks/      # Custom hooks
│   │   ├── services/   # API services
│   │   └── utils/      # Utilities
├── backend/            # Express backend
│   ├── src/
│   │   ├── routes/     # API routes
│   │   ├── services/   # Business logic
│   │   ├── middleware/ # Auth, logging
│   │   └── chat/       # OddBot integration
├── functions/          # Firebase Cloud Functions
├── shared/             # Shared types/utilities
└── docs/               # Documentation
```

## Environment Configuration

### Production
- **GCP Project**: `work-order-tracker-3a515`
- **Firebase Project**: `work-order-tracker-3a515`
- **Region**: us-central1
- **Frontend URL**: Firebase Hosting
- **Backend URL**: Cloud Run

### Service Account
- Email: `ojpm-integration-sa@work-order-tracker-3a515.iam.gserviceaccount.com`

## Key Firestore Collections
- `workOrders` - Work order documents
- `technicians` - Technician profiles
- `clients` - Client information
- `tech_sessions` - Technician time tracking
- `active_jobs` - Currently active job assignments

## Development Commands

```bash
# Frontend
cd frontend && npm run dev

# Backend
cd backend && npm run dev

# Type checking
npm run typecheck

# Build
npm run build
```

## Deployment

```bash
# Frontend (Firebase Hosting)
cd frontend && npm run build && firebase deploy --only hosting

# Backend (Cloud Run)
cd backend && gcloud run deploy workflow-backend --source . --region us-central1
```

## Critical Notes

1. **Always verify GCP project** before deploying: `gcloud config get-value project`
2. **Airtable is source of truth** for operational data - Firestore syncs from it
3. **OddBot** lives in `backend/src/chat/` - handles Google Chat integration
4. **Delta Engine** handles AI estimation - uses Gemini for route optimization
