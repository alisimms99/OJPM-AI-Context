# GCP Environment Configuration

## Production Projects

| App | GCP Project | Firebase Project | Region |
|-----|-------------|------------------|--------|
| WorkFlow | work-order-tracker-3a515 | work-order-tracker-3a515 | us-central1 |
| UBERMENSCH | [TO BE FILLED] | [TO BE FILLED] | [TO BE FILLED] |
| bank-statement-parser | work-order-tracker-3a515 | work-order-tracker-3a515 | us-central1 |

## Service Accounts

| Purpose | Email | Used By |
|---------|-------|---------|
| OJPM Integration | ojpm-integration-sa@work-order-tracker-3a515.iam.gserviceaccount.com | WorkFlow, OddBot |

## Deprecated/Test Environments

⚠️ **DO NOT USE THESE** - They exist but are not configured properly:

| Project | Status | Notes |
|---------|--------|-------|
| ojpm-workflow-test | ABANDONED | Never fully configured, caused confusion |

## Verification Commands

Always run before deploying:

```bash
# Check current project
gcloud config get-value project

# Set correct project
gcloud config set project work-order-tracker-3a515

# List Cloud Run services
gcloud run services list --region=us-central1

# Check Firebase project
firebase use
```
