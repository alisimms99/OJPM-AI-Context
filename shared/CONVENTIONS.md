# OJPM Coding Conventions

Standards that apply across all OJPM applications.

## TypeScript

- Use strict mode (`"strict": true` in tsconfig)
- Prefer interfaces over types for object shapes
- No `any` - use `unknown` with type guards if needed
- Use proper error handling with typed errors

## Naming

| Item | Convention | Example |
|------|------------|---------|
| Files (utilities) | camelCase | `userService.ts` |
| Files (components) | PascalCase | `UserProfile.tsx` |
| Functions | camelCase | `getUserById()` |
| Types/Interfaces | PascalCase | `UserProfile` |
| Constants | SCREAMING_SNAKE | `MAX_RETRY_COUNT` |
| Environment vars | SCREAMING_SNAKE | `FIREBASE_PROJECT_ID` |

## Git

- Branch naming: `feature/issue-XX-short-description` or `fix/issue-XX-short-description`
- Commit messages: `type: description` (e.g., `feat: add user profile page`, `fix: resolve auth timeout`)
- Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`

## Comments

- Use JSDoc for public functions
- Explain WHY, not WHAT (the code shows what)
- Mark technical debt with `// TODO:` or `// FIXME:`

## Error Handling

- Always catch and handle errors explicitly
- Log errors with context (what operation failed, what inputs)
- Return meaningful error messages to users
- Never swallow errors silently

## Security

- Never commit secrets (use environment variables)
- Never log sensitive data (passwords, tokens, PII)
- Validate all user input
- Use parameterized queries for database operations
