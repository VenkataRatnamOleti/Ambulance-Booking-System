# Ambulance Booking — Project Documentation

This document provides a concise but practical reference for contributors, reviewers and anyone who wants to understand, build, test, or run the Ambulance Booking Android application.

## Overview

Ambulance Booking is a native Android application that enables users to request emergency transport quickly and reliably. The app focuses on a minimal, accessible user experience and accurate location reporting so that ambulances can be dispatched fast.

Core capabilities

- Request an ambulance with a few taps
- Share precise GPS coordinates with responders
- Real-time status updates (requested, accepted, en route, arrived)
- Local storage for recent requests and preferences

## Architecture

- Android app (module: `app/`) – native Java/Kotlin entry points, UI, and platform integrations.
- Build system – Gradle with the wrapper in `gradle/` and `gradlew` scripts for reproducible builds.
- Output artifacts – built APKs are placed under `output/` (e.g., `output/app-debug.apk`).

## Important files and folders

- `app/` — Android application module (source, resources, manifest)
- `output/` — prebuilt artifacts (APK) included for convenience
- `gradle/`, `gradlew`, `gradlew.bat` — Gradle wrapper and helpers
- `build.gradle`, `settings.gradle` — top-level Gradle configuration
- `DOCS.md` — this documentation file
- `README.md` — project readme (overview + quick access)

## Getting started (development)

1. Ensure you have Android Studio and the Android SDK installed.
2. Open the project directory in Android Studio.
3. Allow Android Studio to sync Gradle and install any required SDK components.
4. Connect a device or launch an emulator and run the app.

Build from the command line:

```bash
# From the repository root
./gradlew assembleDebug
# Windows PowerShell: use .\gradlew assembleDebug
```

The debug APK will be available under `app/build/outputs/apk/debug/` and a copy is often placed in `output/` depending on the CI/build steps.

## Permissions and settings

The app requires the following Android permissions at runtime:

- ACCESS_FINE_LOCATION — for precise GPS coordinates
- INTERNET — to reach backend services (if configured)
- ACCESS_COARSE_LOCATION — fallback for location where precise GPS is unavailable

Make sure you test permission flows on both Android 10+ and older devices. Use the runtime permission dialog in the app and check behavior when permissions are denied.

## Data and backend

This repository contains the client (Android app) side only. If you wire this client to backend services, typical endpoints will include:

- POST /requests — create a new ambulance request (location, contact, notes)
- GET /requests/:id — get request status and assigned responder
- WebSocket or push notifications for real-time status updates

Add your backend URL in the app configuration or secure it using BuildConfig or `gradle.properties` (do not commit secrets).

## Testing and debugging

- Use Android Studio's instrumentation tests and unit tests (if present) to run automated checks.
- Use `adb logcat` or the IDE logcat view to inspect logs while reproducing flows.
- Check the layout inspector to verify runtime UI across different screen sizes and orientations.

## Release and signing

For production releases:

1. Generate a release keystore and keep it secure.
2. Configure signing in `app/build.gradle` (keystore path, alias, and password via environment variables or CI secrets).
3. Run `./gradlew assembleRelease` and upload the generated bundle/APK to Google Play Console.

## Security and privacy notes

- Do not store unencrypted personal data in version control.
- If the app transmits personal or health-related data, secure communications with TLS and follow regional privacy regulations (HIPAA, GDPR, etc.) where applicable.

## Troubleshooting

- Gradle sync fails: open Android Studio's "Build" window and inspect the error; sometimes updating the Android Gradle Plugin or SDK resolves conflicts.
- Missing SDK components: install the requested SDK packages via SDK Manager.
- Permission-related issues: double-check runtime permission handling and the manifest declarations.

## Contribution guidelines

- Fork the repository and open a Pull Request against `main`.
- Use feature branches (e.g., `feature/xxx`) and clear commit messages.
- Include a brief description and screenshots for UI changes.

## Contact

If you need help or want to discuss features, open an issue or reach out via the GitHub project's issues.

---

Thank you for checking out Ambulance Booking. If you'd like, I can expand this documentation with an architecture diagram, API contract examples, or an onboarding guide for new contributors.