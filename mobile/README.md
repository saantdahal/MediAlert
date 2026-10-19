<p align="center">
  <img src="../brand/logo.png" alt="MediAlert logo" width="140">
</p>

# MediAlert — Mobile

Flutter app for tracking medicine expiry dates and daily dose schedules. Works offline-first and talks to the [backend](../backend/README.md) for login and optional sync.

## Features

- Medicine inventory: name, photo, category, strength, dosage form, expiry date, quantity, unit, batch number, notes
- Search, filter (Valid / Expiring Soon / Expired) and sort
- Expiry alerts at 30, 7, 3 and 1 day(s) before; expired medicines shown in red with a warning
- Dose schedules: daily, weekly or selected days; multiple doses per day; start and end date
- Local notifications with **Taken**, **Skip** and **Snooze** actions
- Dose history and missed-dose tracking
- Stock tracking and refill reminders
- Later: barcode/QR/OCR scanner, family profiles, adherence reports, backup/restore, PIN/biometric lock

## Planned Tech Stack

| Technology | Purpose |
|---|---|
| Flutter / Dart | App framework |
| BLoC | State management |
| Drift / SQLite | Local database |
| `flutter_local_notifications` | Expiry and dose reminders |
| Firebase Cloud Messaging | Push notifications from the backend |
| `dio` | API client |
| `mobile_scanner`, ML Kit Text Recognition | Barcode/QR and OCR (v1.1+) |

## Getting Started

```bash
cd mobile
flutter pub get
flutter run
```

Set the backend URL in the app configuration (e.g. `http://10.0.2.2:5000` for the Android emulator).

## Notes

- A barcode may not contain an expiry date; OCR results must be confirmed by the user before saving.
- Do not commit Firebase config files or secrets.
