# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Next.js 15 + Material-UI template project with full authentication system configured for modern development workflows. The project uses:

- **Next.js 15.5.3** with App Router and Turbopack
- **Material-UI v7.3.2** with Emotion styling and Next.js integration via `@mui/material-nextjs`
- **React 19.1.0** - Latest React version with concurrent features
- **Better Auth 1.3.18** for authentication with email/password
- **Prisma 6.16.2** with PostgreSQL for database management
- **TypeScript 5** for type safety
- **Biome 2.2.0** for fast linting and formatting (replacing ESLint/Prettier)
- **pnpm** as the package manager
- **Lefthook 1.13.1** for Git hooks automation

## Key Architecture Decisions

### Authentication Architecture
The project uses Better Auth for a complete authentication system:
- Email/password authentication via `~/lib/auth-client.ts`
- Session management with `useSession` hook
- Protected routes with automatic redirects
- Authentication server configuration in `~/lib/auth.ts`
- API routes at `/api/auth/[...all]` handle all auth operations

### Database & ORM
- **Prisma** with PostgreSQL backend
- Generated client output to `src/app/generated/prisma` (custom location)
- Docker Compose provides local PostgreSQL instance
- Schema includes User, Session, Account, and Verification models for complete auth flow

### Styling Integration
The project uses Material-UI with Emotion and includes Next.js-specific optimizations:
- `AppRouterCacheProvider` wraps the app in `layout.tsx` for proper SSR hydration
- Geist fonts are configured as CSS variables for consistent typography
- MUI components are server-side rendered correctly with the App Router
- All authentication pages (signup, signin, dashboard) use consistent MUI styling

### Code Quality Setup
- **Biome configuration** (`biome.jsonc`) includes strict React/Next.js rules and custom import organization
- **Git hooks** automatically run Biome checks and fixes on commits/pushes
- **TypeScript** is configured for strict mode with Next.js optimizations

## Development Commands

### Core Development
```bash
# Start development server with Turbopack
pnpm dev

# Build for production (also uses Turbopack)
pnpm build

# Start production server
pnpm start
```

### Database Operations
```bash
# Start local PostgreSQL via Docker
docker-compose up -d

# Generate Prisma client after schema changes
npx prisma generate

# Run database migrations
npx prisma migrate dev

# View database in Prisma Studio
npx prisma studio
```

### Code Quality
```bash
# Check all files (lint + format)
pnpm check

# Auto-fix issues (safe + unsafe fixes)
pnpm check:fix

# Format only
pnpm format:fix

# TypeScript type checking
pnpm typecheck
```

## Project Structure

```
src/
├── app/                   # Next.js App Router
│   ├── api/auth/          # Better Auth API routes
│   ├── dashboard/         # Protected dashboard page
│   ├── signin/            # Sign in page
│   ├── signup/            # Sign up page
│   ├── generated/         # Prisma generated client
│   ├── layout.tsx         # Root layout with MUI provider
│   └── page.tsx           # Landing page with auth links
├── lib/                   # Shared utilities
│   ├── auth.ts           # Better Auth server config
│   ├── auth-client.ts    # Better Auth client exports
│   └── prisma.ts         # Prisma client singleton
prisma/
└── schema.prisma         # Database schema
```

## Authentication Flow

1. **Landing Page** (`/`) - Links to signup/signin
2. **Sign Up** (`/signup`) - Creates new user account
3. **Sign In** (`/signin`) - Authenticates existing user
4. **Dashboard** (`/dashboard`) - Protected page showing user info
5. **Session Management** - Automatic redirects based on auth state

## Database Schema

- **User**: Core user information with email/name
- **Session**: Active user sessions with expiration
- **Account**: OAuth and credential storage
- **Verification**: Email verification tokens

## Git Workflow

Lefthook automatically runs on commits and pushes:
- **Pre-commit**: Auto-fixes code style issues and stages changes
- **Pre-push**: Validates code quality and runs type checking

This ensures consistent code quality without manual intervention.