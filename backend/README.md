# MediAlert — Backend

REST API built with Node.js and Express. It handles authentication, admin user management, medicines, dose schedules and notifications.

## Features

- **Auth** — register, login, JWT access/refresh tokens, password hashing
- **Roles** — `user` and `admin`
- **User management (admin)** — list, view, block/unblock and delete users
- **Medicines** — add, update, remove and list medicines (name, category, strength, expiry date, quantity, batch, notes, photo)
- **Doses** — create schedules, record **Taken**, **Skip** and **Snooze**, view history and missed doses
- **Stock** — decrease quantity on Taken, refill threshold checks
- **Notifications** — push notifications (FCM) for expiry and refill alerts

## Planned Tech Stack

| Technology | Purpose |
|---|---|
| Node.js + Express | API server |
| MongoDB (Mongoose) or PostgreSQL | Database — to be decided |
| `jsonwebtoken`, `bcrypt` | Authentication |
| `zod` or `joi` | Request validation |
| `multer` | Medicine photo upload |
| `node-cron` | Scheduled expiry/refill checks |
| `firebase-admin` | Push notifications |

## Planned API

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Create account |
| POST | `/api/auth/login` | Login |
| GET | `/api/medicines` | List medicines |
| POST | `/api/medicines` | Add medicine |
| PUT | `/api/medicines/:id` | Update medicine |
| DELETE | `/api/medicines/:id` | Remove medicine |
| POST | `/api/doses/:id/taken` | Mark dose as taken |
| POST | `/api/doses/:id/skip` | Skip dose |
| GET | `/api/admin/users` | List users (admin) |
| PATCH | `/api/admin/users/:id` | Block/unblock user (admin) |
| DELETE | `/api/admin/users/:id` | Delete user (admin) |

## Getting Started

```bash
cd backend
npm install
cp .env.example .env
npm run dev
```

Example `.env`:

```env
PORT=5000
DATABASE_URL=
JWT_SECRET=
JWT_REFRESH_SECRET=
FCM_SERVICE_ACCOUNT_PATH=
```

Never commit `.env` files or Firebase service-account keys.
