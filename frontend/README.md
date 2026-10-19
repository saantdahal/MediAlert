# MediAlert — Admin Frontend

Admin web panel built with **Next.js** using **JSX** (JavaScript, no TypeScript). It talks to the [backend](../backend/README.md) API.

## Features

- Admin login
- Dashboard with user and medicine statistics
- User management: list, search, view, block/unblock, delete
- Role-protected routes (admin only)

## Planned Tech Stack

| Technology | Purpose |
|---|---|
| Next.js (App Router) | Framework |
| React (JSX) | UI |
| Tailwind CSS | Styling |
| `axios` | API requests |

## Getting Started

```bash
cd frontend
npx create-next-app@latest . --js --app --tailwind
npm run dev
```

Set the API URL in `.env.local`:

```env
NEXT_PUBLIC_API_URL=http://localhost:5000
```

The panel runs at http://localhost:3000.
