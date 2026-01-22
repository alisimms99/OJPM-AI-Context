# CLAUDE.md - Bank Statement Parser

## Project Overview

Bank Statement Parser is a TypeScript application that extracts and processes transaction data from bank statement PDFs. It provides automated parsing, categorization, and export capabilities for financial data management.

**Target Users**: OJPM finance/accounting operations

## Tech Stack

### Core
- **Language**: TypeScript (97.7%)
- **Runtime**: Node.js
- **Build**: TypeScript compiler

### Client
- **Location**: `/client`
- **Purpose**: Frontend interface for uploading and viewing parsed statements

### Server
- **Location**: `/server`
- **Purpose**: API and parsing logic
- **Database**: Drizzle ORM

### Infrastructure
- **Cloud**: Google Cloud Platform
- **Functions**: Firebase
- **Document Processing**: Google Document AI

## Project Structure

```
bank-statement-parser/
├── client/              # Frontend application
├── server/              # Backend API and parsing logic
├── shared/              # Shared types and utilities
├── drizzle/             # Database migrations and schema
├── scripts/             # Utility scripts
├── fixtures/            # Test data
├── test/
│   └── performance/     # Performance tests
├── monitoring/          # Monitoring configuration
├── patches/             # Dependency patches
├── docs/                # Documentation
├── Dockerfile           # Container configuration
├── ARCHITECTURE.md      # System architecture
├── ROADMAP.md           # Development roadmap
└── README.md            # Project overview
```

## Key Configuration Files
- `.env.example` - Environment variable template
- `.firebaserc` - Firebase project configuration
- `Dockerfile` - Production container setup

## Development Commands

```bash
# Install dependencies
npm install

# Development server
npm run dev

# Build
npm run build

# Run tests
npm test
```

## External Integrations
- **Google Document AI** - PDF text extraction
- **Google Sheets API** - Export to spreadsheets
- **Firebase** - Authentication and hosting

## Related Documentation
- `ARCHITECTURE.md` - Detailed system architecture
- `ROADMAP.md` - Feature roadmap and priorities
- `FINDINGS.md` - Parser audit findings
- `GPT_CONFIGURATION.md` - AI/LLM configuration
- `FIREBASE_SETUP.md` - Firebase setup instructions

## Notes

- Multi-bank support with custom parsers for different statement formats
- LLM-assisted transaction cleanup and categorization
- Performance benchmarking suite in `/test/performance`
