# Splitt

Auto ride-sharing for IIIT Jabalpur students. Split auto fares with batchmates going the same way.

## How it works

Two students both heading to the railway station at 10am shouldn't each pay ₹80 for a separate auto. Splitt connects them.

1. **Post a ride** — you're booking an auto and have spare seats. Set the destination, departure time, and fare per head.
2. **Post an intent** — you need a ride but don't have one yet. Set where you want to go and your time window.
3. **Match** — Splitt automatically finds rides that fit your intent (and intents that fit your ride). Both parties get a real-time notification.
4. **Confirm** — both sides confirm the match. A seat is reserved atomically.
5. **Connect** — once both confirm, each other's WhatsApp number is revealed.

Only `@iiitdmj.ac.in` Google accounts can sign in.

## Stack

|           |                                                                      |
| --------- | -------------------------------------------------------------------- |
| Frontend  | React 18, Vite, TailwindCSS, TanStack Query, React Router v6         |
| Backend   | Node.js 20, Express, Prisma, PostgreSQL                              |
| Real-time | Server-Sent Events                                                   |
| Auth      | Google Identity Services (ID token flow — no client secret needed)   |
| Infra     | Docker (local), Render (backend), Vercel (frontend), Neon (database) |

## Getting started

**Prerequisites:** Node.js 20+, Docker Desktop

```bash
# Install all workspace dependencies
npm install

# Start Postgres
docker compose up -d

# Copy env files and fill in values
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env

# Run migrations and seed dev users
npm --workspace backend run prisma:migrate
npm --workspace backend run db:seed

# Start backend (:3000) and frontend (:5173)
npm run dev:backend
npm run dev:frontend
```

Open [http://localhost:5173](http://localhost:5173), click **Dev Login**, and you're in.

For Google OAuth setup and the full command reference see [docs/SETUP.md](docs/SETUP.md).

## Contributing

Read [docs/CONTRIBUTING.md](docs/CONTRIBUTING.md) before opening a PR.
Open issues are tracked in [CLEANUP.md](CLEANUP.md) — pick one and claim it.

## Docs

|                                              |                                                                  |
| -------------------------------------------- | ---------------------------------------------------------------- |
| [docs/SETUP.md](docs/SETUP.md)               | Local setup, Google OAuth config, all dev commands               |
| [docs/DATA_SHAPES.md](docs/DATA_SHAPES.md)   | Every API endpoint with request and response examples            |
| [docs/CONTRIBUTING.md](docs/CONTRIBUTING.md) | Branch naming, commit format, PR process                         |
| [CLEANUP.md](CLEANUP.md)                     | Features not yet built — good place to find something to work on |
