# Daily Flow — Android APK Source Project (iOS 27.3 Liquid Glass Edition)

This archive contains a complete, ready-to-compile **Android Studio / Gradle APK project** wrapping the **Daily Flow** interactive mobile productivity prototype with native Android edge-to-edge rendering, persistent storage, haptic feedback, and native system push notifications.

## Project Structure

```text
DailyFlow-Android-APK/
├── build.gradle                     # Root Gradle configuration
├── settings.gradle                  # Module includes (:app)
├── gradle.properties                # AndroidX & JVM build flags
├── capacitor.config.json            # Optional Capacitor CLI metadata
├── README.md                        # Build & signing guide
└── app/
    ├── build.gradle                 # Android APK build config (com.dailyflow.app, minSdk 24, targetSdk 35)
    └── src/main/
        ├── AndroidManifest.xml      # Permissions (POST_NOTIFICATIONS, SCHEDULE_EXACT_ALARM, VIBRATE)
        ├── assets/www/
        │   └── index.html           # Complete Daily Flow iOS 27.3 Liquid Glass web app + AndroidBridge
        ├── java/com/dailyflow/app/
        │   ├── MainActivity.java    # Edge-to-edge WebView host + JS-to-Native Notification/Haptic bridge
        │   └── ReminderReceiver.java# BroadcastReceiver for scheduled Android push notifications
        └── res/
            ├── drawable/            # Adaptive icon background & Liquid Glass squircle foreground
            ├── mipmap-anydpi-v26/   # Launcher icon XMLs
            ├── values/              # strings.xml & edge-to-edge Theme.DailyFlow
            └── xml/                 # Android 12+ backup & data extraction rules
```

## How to Build the `.apk` File

### Option A: Using Android Studio (Recommended)
1. Extract `DailyFlow-Android-APK-Source.zip`.
2. Open **Android Studio** -> **Open** -> select the `DailyFlow-Android-APK` folder.
3. Wait for Gradle Sync to finish automatically.
4. From the top menu bar, click **Build** -> **Build Bundle(s) / APK(s)** -> **Build APK(s)**.
5. Once complete, click **locate** in the notification popup to find your installable APK at:
   `app/build/outputs/apk/debug/app-debug.apk`

### Option B: Using Command Line (Gradle)
```bash
cd DailyFlow-Android-APK
gradle assembleDebug
# Output APK: app/build/outputs/apk/debug/app-debug.apk
```

### Installing on Your Android Phone
1. Transfer `app-debug.apk` to your Android device (or connect via USB with USB Debugging enabled and run `adb install -r app/build/outputs/apk/debug/app-debug.apk`).
2. Allow **Install unknown apps** if prompted, open **Daily Flow**, and grant **Notifications** permission when prompted so scheduled task reminders also appear in your Android notification shade.
