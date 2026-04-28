# Ambulance Booking — Native Android

![GitHub stars](https://img.shields.io/github/stars/VenkataRatnamOleti/Ambulance-Booking-System?style=for-the-badge&logo=github)
![GitHub forks](https://img.shields.io/github/forks/VenkataRatnamOleti/Ambulance-Booking-System?style=for-the-badge&logo=github)
![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

One-tap ambulance booking, built for speed and reliability. This repository contains the native Android source and a ready-to-install APK so you can try the app immediately on a device.

## Quick Access — Download the APK

Click the badge to download the latest debug APK directly from this repository:

[![Download APK](https://img.shields.io/badge/Download-APK-blue?style=for-the-badge&logo=android)](https://github.com/VenkataRatnamOleti/Ambulance-Booking-System/raw/main/output/app-debug.apk)

Direct raw link: https://github.com/VenkataRatnamOleti/Ambulance-Booking-System/raw/main/output/app-debug.apk

Note: If you host releases, replace the link above with your release asset for a stable download.

Documentation: [DOCS.md](DOCS.md) — detailed project documentation and developer notes.

## Table of contents

- [About](#about)
- [Highlights](#highlights)
- [Try it (install)](#try-it-install)
- [Project layout](#project-layout)
- [Development](#development)
- [Contributing](#contributing)
- [License](#license)

## About

Ambulance Booking is a focused Android app that helps users request emergency transport quickly. The app emphasizes minimal taps, accurate geolocation, and clear status updates so patients can get help faster.

## Highlights

- Native Android codebase for responsive device-level behavior
- Real-time GPS location handling
- Simple, accessible UI optimized for emergencies

## Try it (install)

Safety first: only install APKs you trust. The APK included here is a debug build for evaluation.

Option A — Download and install on your Android device

1. Open this README on your phone and tap the "Download APK" badge above (or use the direct link).
2. On the device, enable installation from unknown sources (Settings → Security → Install unknown apps) for your browser or file manager.
3. Tap the downloaded file to install.

Option B — Install from your computer using ADB

1. Connect your Android device with USB debugging enabled.
2. From a terminal (PowerShell), run:

   ```powershell
   adb install -r output/app-debug.apk
   ```

   If you prefer a direct URL install via ADB (device must have network and allow installs):

   ```powershell
   adb shell pm install -r "https://github.com/VenkataRatnamOleti/Ambulance-Booking-System/raw/main/output/app-debug.apk"
   ```

   Verifying the file: you can compute a SHA256 or MD5 locally before installing. In PowerShell:

   ```powershell
   Get-FileHash .\output\app-debug.apk -Algorithm SHA256
   ```

## Project layout

Top-level structure (important files/folders):

```
.
├── app/                 # Android app module
├── gradle/              # Gradle wrapper
├── output/              # Built artifacts (APK)
│   └── app-debug.apk
├── build.gradle
├── gradlew
└── README.md
```

## Development

1. Open the project in Android Studio.
2. Let Gradle sync and install any SDK components requested by the IDE.
3. Build and run on an emulator or physical device.

Tips:

- Use the Android Studio logcat and on-device layout inspector when debugging UI or permissions.
- Update the SDK targets in `app/build.gradle` if Android Studio prompts you.

## Contributing

Contributions are welcome. A simple workflow:

1. Fork the repository
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -am "Add feature"`
4. Push and open a pull request

Please include screenshots and a short description of what you changed.

## License

This project is provided under the MIT license. See `LICENSE` for details.

---

_If you want I can also add a release with the APK attached, or compute and display the SHA256 checksum for the APK in this README — tell me which you prefer._
