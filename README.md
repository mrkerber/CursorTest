# CursorTest

This is a monorepo application using Expo with Supabase backend.

## Setup
1. Clone the repository.
2. Install dependencies using `npm install` or `yarn`.
3. Create a `.env` file based on `.env.example`.

## Supabase Configuration
- Set up a Supabase project.
- Add your Supabase URL and Anon Key to the `.env` file:
  - `SUPABASE_URL=your_supabase_url`
  - `SUPABASE_ANON_KEY=your_anon_key`

## Running the App
- Use the following scripts to run the app:
  - `npm start` for Expo Go
  - `npm run build` for production build

## Folder Structure
```
/CursorTest
  ├── /apps
  │   ├── /mobile
  │   └── /web
  ├── /packages
  │   ├── /common
  ├── package.json
  └── README.md
```