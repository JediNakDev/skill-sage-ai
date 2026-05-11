# Skill Sage AI

An AI-powered platform for skill assessment and personalized learning guidance.

## Tech Stack

Built on the [T3 Stack](https://create.t3.gg/):

- [Next.js 15](https://nextjs.org) (App Router)
- [NextAuth.js v5](https://next-auth.js.org) — authentication (LinkedIn provider)
- [Drizzle ORM](https://orm.drizzle.team) + PostgreSQL
- [tRPC](https://trpc.io) — end-to-end typesafe APIs
- [Tailwind CSS](https://tailwindcss.com)
- [TypeScript](https://www.typescriptlang.org/)

## Getting Started

### Prerequisites

- Node.js 20+
- PostgreSQL database
- LinkedIn OAuth credentials

### Setup

1. Install dependencies:

   ```bash
   npm install
   ```

2. Copy the environment file and fill in the values:

   ```bash
   cp .env.example .env
   ```

   Required variables:
   - `DATABASE_URL` — PostgreSQL connection string
   - `AUTH_SECRET` — generate with `npx auth secret`
   - `AUTH_LINKEDIN_ID` / `AUTH_LINKEDIN_SECRET` — LinkedIn OAuth credentials
   - `AUTH_URL` — base URL of the deployment

3. Push the database schema:

   ```bash
   npm run db:push
   ```

4. Start the dev server:

   ```bash
   npm run dev
   ```

   Open [http://localhost:3000](http://localhost:3000).

## Scripts

| Script | Description |
| --- | --- |
| `npm run dev` | Start the dev server (Turbo) |
| `npm run build` | Build for production |
| `npm run start` | Start the production server |
| `npm run check` | Lint + typecheck |
| `npm run db:push` | Push schema changes to the database |
| `npm run db:studio` | Open Drizzle Studio |
| `npm run format:write` | Format the codebase with Prettier |

## Project Structure

```
src/
├── app/              # Next.js App Router pages and API routes
├── server/
│   ├── api/          # tRPC routers
│   ├── auth/         # NextAuth configuration
│   └── db/           # Drizzle schema and client
├── trpc/             # tRPC client setup
├── styles/           # Global styles
└── env.js            # Validated environment variables
```

## Deployment

See the T3 Stack deployment guides for [Vercel](https://create.t3.gg/en/deployment/vercel), [Netlify](https://create.t3.gg/en/deployment/netlify), or [Docker](https://create.t3.gg/en/deployment/docker).
