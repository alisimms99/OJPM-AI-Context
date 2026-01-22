# Deployment Checklist

Run through this checklist before ANY deployment.

## Pre-Deployment Verification

### 1. Environment Check
```bash
# Verify GCP project
gcloud config get-value project
# Expected: [correct project for this app]

# Verify Firebase project (if applicable)
firebase use
# Expected: [correct project]

# Verify you're on the right branch
git branch --show-current
# Expected: main (for production) or your feature branch
```

### 2. Code Quality
```bash
# Run type checking
npm run typecheck
# Expected: No errors

# Run linter
npm run lint
# Expected: No errors (or only warnings you've accepted)

# Run tests (if available)
npm test
# Expected: All tests pass
```

### 3. Build Verification
```bash
# Build the project
npm run build
# Expected: Successful build with no errors
```

## Deployment Commands

### Frontend (Firebase Hosting)
```bash
cd frontend
npm run build
firebase deploy --only hosting
```

### Backend (Cloud Run)
```bash
cd backend
gcloud run deploy [service-name] --source . --region us-central1
```

## Post-Deployment Verification

1. Check the deployed URL loads correctly
2. Test one critical user flow
3. Check Cloud Run logs for errors:
```bash
gcloud logging read "resource.type=cloud_run_revision AND severity>=ERROR" --limit=10 --freshness=5m
```

## Rollback

If something goes wrong:
```bash
# List previous revisions
gcloud run revisions list --service=[service-name] --region=us-central1

# Route traffic to previous revision
gcloud run services update-traffic [service-name] --to-revisions=[previous-revision]=100 --region=us-central1
```
