# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Next.js 15 + Material-UI template project configured for modern development workflows. The project uses:

- **Next.js 15** with App Router and Turbopack
- **Material-UI v7** with Emotion styling and Next.js integration via `@mui/material-nextjs`
- **TypeScript** for type safety
- **Biome** for fast linting and formatting (replacing ESLint/Prettier)
- **pnpm** as the package manager
- **Lefthook** for Git hooks automation

## Key Architecture Decisions

### Styling Integration
The project uses Material-UI with Emotion and includes Next.js-specific optimizations:
- `AppRouterCacheProvider` wraps the app in `layout.tsx` for proper SSR hydration
- Geist fonts are configured as CSS variables for consistent typography
- MUI components are server-side rendered correctly with the App Router

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
    ├── layout.tsx         # Root layout
    ├── page.tsx           # Home page
    └── globals.css        # Global styles

```

## Biome Configuration

The project uses Biome with strict rules for React/Next.js development:
- React hooks and JSX best practices enforced
- TypeScript-specific rules for array types and imports
- Custom import organization (React/Next.js → packages → relative imports → styles)
- HTML accessibility rules enabled



## Git Workflow

Lefthook automatically runs on commits and pushes:
- **Pre-commit**: Auto-fixes code style issues and stages changes
- **Pre-push**: Validates code quality and runs type checking

This ensures consistent code quality without manual intervention.