# OJPM AI Context Repository

Central repository for AI agent context files across all OJPM applications.

## Purpose

This repository contains CLAUDE.md files and shared documentation that AI coding agents (Claude Code, Cursor, Copilot, etc.) use to understand our codebase, conventions, and environment.

## Structure

- `/apps/` - App-specific CLAUDE.md files (copy to each repo's root)
- - `/shared/` - Cross-app conventions and environment info
  - - `/agents/` - Guides for using AI agents effectively
   
    - ## Usage
   
    - ### For Claude Code / Cursor / Copilot
    - Copy the relevant CLAUDE.md file to your app's repo root. AI agents will read it automatically.
   
    - ### For Claude Projects
    - Upload this entire repository to a Claude Project for comprehensive context.
   
    - ### Keeping in Sync
    - This repo is the source of truth. When updating, push changes here first, then sync to individual app repos.
   
    - ## Apps Covered
   
    - | App | Repo | Status |
    - |-----|------|--------|
    - | WorkFlow 1.0 | alisimms99/WorkFlow-1.0 | Production |
    - | UBERMENSCH 1.0 | alisimms99/UBERMENSCH-1.0 | Development |
    - | bank-statement-parser | alisimms99/bank-statement-parser | Development |
    - | OddBot | (part of WorkFlow) | Production |
   
    - ## Related Resources
   
    - - [Digital CTO Guide](agents/DIGITAL_CTO_GUIDE.md) - How to delegate development to AI
      - - [Deployment Checklist](shared/DEPLOYMENT_CHECKLIST.md) - Pre-deployment verification steps
