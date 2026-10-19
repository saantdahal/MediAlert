# ExpiryAlert

**Track expiry dates. Reduce waste. Stay informed.**

ExpiryAlert is an offline-first Flutter application that helps users manage household products and keep track of their expiry dates. From packaged food and cosmetics to medicines and other date-sensitive items, ExpiryAlert makes it easier to organize inventory and receive timely reminders before products expire.

The app supports QR code and barcode scanning, OCR-based expiry date recognition, local notifications, and Firebase Cloud Messaging (FCM) for remote notifications.

## Features

- **Household Inventory** — Add, edit, delete, search, and organize products by category.
- **QR & Barcode Scanning** — Scan product codes to identify products and simplify item entry.
- **OCR Expiry Date Recognition** — Extract potential expiry dates from product packaging using on-device text recognition.
- **Expiry Reminders** — Schedule notifications before products expire.
- **Expiry Dashboard** — View expired items, upcoming expirations, and products that are still within their expiry period.
- **Offline-First Storage** — Store inventory locally and access it without an internet connection.
- **Firebase Cloud Messaging** — Support remote notifications and future cloud-connected features.
- **Quantity Tracking** — Keep track of household stock and product quantities.
- **Cross-Platform** — Built with Flutter for Android and iOS.

## Tech Stack

| Technology | Purpose |
|---|---|
| Flutter | Cross-platform application development |
| Dart | Programming language |
| BLoC | State management |
| Drift / SQLite | Local relational database |
| `mobile_scanner` | QR code and barcode scanning |
| Google ML Kit Text Recognition | On-device OCR |
| `flutter_local_notifications` | Local expiry reminders |
| Firebase Core | Firebase initialization |
| Firebase Cloud Messaging | Remote push notifications |
| GetIt | Dependency injection |
| `intl` | Date formatting and localization |

## How It Works

1. Add a household product manually or scan its QR code or barcode.
2. Enter or confirm the product name, quantity, category, and expiry date.
3. Optionally scan the packaging with OCR to detect a potential expiry date.
4. Review the detected information and correct it if necessary.
5. Save the product to the local inventory.
6. Receive scheduled local notifications before the product expires.

**Note:** A barcode does not necessarily contain an expiry date. Product identification and expiry-date recognition are separate processes. OCR results must be reviewed before saving.

## Notifications

ExpiryAlert uses two notification mechanisms:

### Local Notifications
- Scheduled expiry reminders.
- Configurable reminder intervals.
- Notifications that do not require an internet connection once scheduled, subject to device permissions and operating-system restrictions.

### Firebase Cloud Messaging
- Remote push notifications.
- Support for future announcements and cloud-connected functionality.
- A foundation for optional backend-driven notifications.

FCM requires a configured Firebase project and appropriate platform setup. Server-triggered notifications require a trusted backend or another authorized sender. FCM does not independently schedule expiry reminders.

## Architecture

The project follows a feature-oriented structure with BLoC state management, repository abstractions, and local persistence.

```text
lib/
├── core/
│   ├── database/
│   ├── di/
│   ├── notifications/
│   ├── services/
│   └── utils/
├── features/
│   ├── dashboard/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   ├── inventory/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   ├── scanner/
│   │   ├── data/
│   │   └── presentation/
│   └── settings/
│       └── presentation/
├── app/
└── main.dart
```

This is the proposed structure; directories and features may evolve during development.

## Getting Started

### Prerequisites

- Flutter SDK
- Dart SDK compatible with the selected Flutter version
- Android Studio or Xcode for platform-specific builds
- A Firebase project for FCM functionality

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/YOUR_USERNAME/expiry_alert.git
   cd expiry_alert
   ```

2. Install dependencies:

   ```bash
   flutter pub get
   ```

3. Configure Firebase for Android and iOS using the official FlutterFire setup instructions.

4. Generate any required database or code-generation files, if configured:

   ```bash
   dart run build_runner build --delete-conflicting-outputs
   ```

5. Run the application:

   ```bash
   flutter run
   ```

The code-generation step is needed only if the selected database or other dependencies use generated code.

## Firebase Configuration

To enable Firebase Cloud Messaging:

1. Create a Firebase project.
2. Register the Android and iOS applications.
3. Configure the platform-specific Firebase files.
4. Initialize Firebase in the Flutter application.
5. Request notification permissions where required.
6. Handle foreground messages, background messages, and notification taps.
7. Configure APNs for iOS push notifications.
8. If remote notifications need to be sent automatically, configure a trusted backend or Cloud Functions.

Do not commit service-account private keys, credentials, or other secrets to the repository.

## Privacy

ExpiryAlert is designed around local-first inventory management.

- Household inventory can be stored on the device.
- OCR can be performed on-device.
- Camera access is used for scanning products and reading packaging.
- Notification permissions are requested when needed.
- Any future cloud synchronization or analytics should clearly explain what data is collected and why.

## Roadmap

- [ ] Initialize the Flutter project and app theme.
- [ ] Implement BLoC-based state management.
- [ ] Set up local database and inventory CRUD.
- [ ] Build the expiry dashboard.
- [ ] Add QR and barcode scanning.
- [ ] Implement OCR-based expiry date detection.
- [ ] Add editable date confirmation.
- [ ] Schedule local expiry notifications.
- [ ] Integrate Firebase Cloud Messaging.
- [ ] Add inventory search and category filters.
- [ ] Test Android and iOS notification behavior.
- [ ] Prepare the Google Play Store and Apple App Store releases.

## Contributing

Contributions, bug reports, and feature suggestions are welcome. Please open an issue to discuss significant changes before submitting a pull request.

## License

This project is currently under development. A license will be added before distribution.

---

**ExpiryAlert** — A smarter way to manage household expiry dates.
