# MediAlert

**Never miss a dose. Never use an expired medicine.**

MediAlert is a medicine management system with two core purposes:

- **Medicine Expiry Alert** — store the expiry date of every medicine, get reminders as the date approaches, and clearly identify expired medicines.
- **Medicine Time Reminder** — set the times to take each medicine, keep a daily schedule with notifications, and mark doses as **Taken** once done.

The project is split into three parts:

| Folder | Description | Tech |
|---|---|---|
| [`mobile/`](mobile/README.md) | User-facing mobile app | Flutter (Dart) |
| [`backend/`](backend/README.md) | REST API, authentication, notifications | Node.js, Express |
| [`frontend/`](frontend/README.md) | Admin web panel for user management | Next.js (JSX) |

## Core Features — Version 1.0

### 1. Medicine Inventory
- Medicine name, photo and category
- Strength (e.g. 500 mg) and dosage form
- Expiry date, quantity and unit
- Batch number and optional notes
- Search, filter and sort

### 2. Expiry Date Alerts
- Reminders 30, 7, 3 and 1 day(s) before expiry
- Expired medicines clearly shown in red
- **Expiring Soon**, **Expired** and **Valid** filters
- Clear warning not to use expired medicines
- Customizable reminder days per user

### 3. Medicine Time Reminder
- Daily, weekly or selected-days schedule
- Multiple doses per day
- Start date and end date
- Local notification at dose time
- **Taken**, **Skip** and **Snooze** actions
- Dose history and missed-dose tracking

### 4. Stock & Refill Reminder
- Track remaining medicine quantity
- Reduce stock automatically when a dose is marked Taken
- Refill notification when stock reaches a threshold
- Update quantity when restocking

## Advanced Features — Version 1.1+

### 5. Barcode, QR & OCR Scanner
- Identify a product by scanning its barcode
- Read the name and printed expiry date from the packet using OCR
- User confirms scanned data before it is saved

> A barcode may not contain an expiry date, and OCR results must always be verified manually.

### 6. Family Profiles
- Separate medicine list per family member
- Member name and profile color
- Organize schedules for children or elderly family members
- Shared reminders and caregiver access (later)

### 7. Adherence & History
- Daily/weekly dose completion summary
- History of missed and skipped doses
- Medicine start/end history
- Exportable report

> Reports are for personal tracking only and are not a replacement for a doctor's advice.

### 8. Privacy & Backup
- Main features work offline
- Local database backup and restore
- Optional PIN/biometric lock
- Option to delete all data
- Optional cloud sync — **opt-in, never on by default**, since medicine data is sensitive

## System Overview

```text
 Flutter app (mobile)  ──REST──▶  Express API (backend)  ──▶  Database
        ▲                               ▲
        │ local + push notifications    │ REST (admin)
        │                               │
        └──────────────────────  Next.js admin panel (frontend)
```

- **Notifications** — local notifications on the device for expiry and dose reminders; push notifications from the backend where needed.
- **Authentication** — JWT-based login; roles: `user` and `admin`.
- **Admin** — manage users from the web panel.
- **Medicine data** — add, update, remove and mark medicines/doses as taken through the API, with offline-first storage on the device.

## Repository Structure

```text
MediAlert/
├── mobile/      # Flutter app
├── backend/     # Node.js + Express API
├── frontend/    # Next.js admin panel (JSX)
├── LICENSE
└── README.md
```

## Roadmap

- [ ] Set up `backend/` (Express, database, auth, roles)
- [ ] Medicine and dose APIs
- [ ] Set up `frontend/` admin panel (login, user management)
- [ ] Mobile: medicine inventory and expiry alerts
- [ ] Mobile: dose schedule, notifications, Taken/Skip/Snooze
- [ ] Mobile: stock and refill reminders
- [ ] Barcode / QR / OCR scanning
- [ ] Family profiles
- [ ] Adherence reports
- [ ] Backup, restore and app lock

## License

MediAlert is proprietary software. All rights are reserved by the copyright holder. See [LICENSE](LICENSE).
