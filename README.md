# Media Log (Movies • Books • Games)

A cross-platform **web + mobile** app for tracking media you consume (movies, books, games, and more) and rating each item from **1–10**.

This repository is intentionally structured so multiple agents can work in parallel (UI, backend, data model, and infra) with a shared plan and conventions.

## What the app is supposed to do

### Core concept
Users maintain a personal library of media entries. For each entry they can:
- Choose a **media type** (starting with: Movie, Book, Game; expandable later)
- Record **title** and optional details
- Assign a **rating (1–10)**
- Track **status** (e.g., Want, In Progress, Completed)
- Add optional **review/notes**
- Add **tags** (genre, mood, platform, etc.)
- See their library with filters and stats

### MVP features (ship first)
- **Auth**: sign up / sign in / sign out
- **Library**: list of logged items with sorting + filtering
- **Add/Edit/Delete** entries
- **Rating**: integer 1–10
- **Status**: Want / In Progress / Completed
- **Basic search** by title
- **Profile settings** (minimal)
- **Export** your data (JSON/CSV)

### Post-MVP / stretch goals
- Metadata lookup (covers + details) from external APIs (TMDb/OpenLibrary/IGDB, etc.)
- Duplicate detection
- Stats dashboard (charts, top-rated, by type over time)
- Sharing / social (optional): public profile, friends, recommendations
- Offline-first with sync
- Notifications / reminders for backlogs

## How it will be built

### Tech stack (defaults)
- **Client (Web + Mobile)**: Expo (React Native) targeting iOS/Android and Web
- **Backend**: Supabase (Postgres + Auth + Row Level Security)
- **Language**: TypeScript
- **Styling/UI**: React Native components (optionally a UI kit later)

> Note: The repo currently has `apps/mobile` and `apps/web` placeholders. The intended direction is to converge to **one Expo app that runs on mobile and web** unless we explicitly decide to keep two separate clients.

### Data model (planned)
Supabase Postgres tables (initial plan):
- `profiles`
  - `id` (uuid, matches `auth.users.id`)
  - `username` (text, optional)
  - `created_at`
- `media_entries`
  - `id` (uuid)
  - `user_id` (uuid, FK -> auth.users)
  - `type` (enum-ish text: `movie` | `book` | `game` | ...)
  - `title` (text)
  - `creator` (text, optional: author/director/studio)
  - `year` (int, optional)
  - `status` (text: `want` | `in_progress` | `completed`)
  - `rating` (int 1–10, nullable until completed if desired)
  - `review` (text, optional)
  - `tags` (text[], optional)
  - `completed_on` (date, optional)
  - `created_at`, `updated_at`

Row Level Security (RLS) policy intent:
- Users can only read/write their own `media_entries`

### Repo structure
```
/apps
  /mobile        # placeholder (will likely become the main Expo app OR be replaced)
  /web           # placeholder (optional if using Expo Web only)
/packages
  /common        # shared types, utilities, validation

.gitignore
package.json     # workspaces root
README.md
```

### Development workflow (planned)
- Create/maintain Supabase project
- Provide `.env.example` (never commit secrets)
- Implement screens and navigation
- Implement Supabase client + auth flows
- Build CRUD for `media_entries`
- Add filtering/sorting and basic stats

## Environment variables
Create a `.env` (or platform-appropriate env files) based on `.env.example` and set:
- `SUPABASE_URL=...`
- `SUPABASE_ANON_KEY=...`

## Contribution notes for other agents
- Keep commits small and focused (one feature per commit).
- Prefer shared types in `packages/common` so web/mobile stay consistent.
- Don’t commit secrets. Use `.env.example`.
- When adding a new feature, update this README with user-facing behavior + any schema changes.

## Current status
- Repo scaffolding in progress (workspaces + placeholders + gitignore).
- Next step: initialize an Expo app and wire Supabase auth + `media_entries` CRUD.
