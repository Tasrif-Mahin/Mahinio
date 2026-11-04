# Mahinio Android project

This is an Android Studio project wrapper for the current Mahinio HTML app.

## Important status
- The Android wrapper and device image picker bridge are included.
- The app data uses browser storage (localStorage) inside the WebView.
- **This is not yet a fully offline build.** The supplied HTML still references Tailwind CDN, Lucide CDN, Chart.js CDN, and Google Fonts. Those dependencies must be bundled locally before airplane-mode operation can be guaranteed.
- **No APK is included.** This build environment did not have Android SDK / platform tools / Gradle installed, and outbound DNS access to fetch dependencies was unavailable. I did not label an unbuilt project as an APK.

## Build on Windows with Android Studio
1. Install Android Studio and its recommended Android SDK (API 35).
2. Extract this ZIP.
3. Open the `Mahinio-Android-Project` folder in Android Studio.
4. Let Gradle sync and install any prompted SDK components.
5. Connect your Android phone with USB debugging enabled, or use an emulator.
6. Select **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
7. Android Studio will show the APK location, normally `app/build/outputs/apk/debug/app-debug.apk`.

## Before daily offline use
The four external web dependencies must be downloaded and referenced from `app/src/main/assets/` instead of their CDN URLs. Until then, first launch/rendering of some UI components requires internet. Do not rely on this version as an offline-only financial record store yet; export/backup your data regularly.


## Build the APK automatically with GitHub Actions

1. Create a new **public or private** GitHub repository named `Mahinio` (private is fine).
2. Extract this project ZIP on your PC.
3. In the new GitHub repository, choose **Add file > Upload files** and upload the *contents* of the `Mahinio-Android-Project` folder, including the hidden `.github` folder. If using GitHub Desktop, add the extracted folder as the repository and commit/push it.
4. Push the files to the `main` branch.
5. Open the repository's **Actions** tab. The workflow named **Build Mahinio APK** should run automatically after the push. You can also select it and click **Run workflow**.
6. Open the completed workflow run, scroll to **Artifacts**, and download `Mahinio-debug-APK`.
7. Extract that downloaded artifact ZIP; it contains `app-debug.apk`. Transfer it to your Android phone and install it.

### Important
- GitHub Actions builds the Android wrapper; it does not make the current web app fully offline. The HTML still references external Tailwind, Lucide, Chart.js, and Google Fonts CDN resources.
- This is a debug APK for personal testing, not a Play Store release.
- Do not commit passwords, signing keys, API keys, or personal financial data to GitHub.
