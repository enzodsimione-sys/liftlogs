# Lift Log

A free, offline weight-lifting log for Android. Built for one-handed use between sets: log a set in one tap, see last time's numbers, keep notes, and watch your top set progress. Kilograms, English, dark by default.

- Routines (Day A, Day B, Home) are preloaded and fully editable; supersets, per-side sets and timed holds are supported.
- Rest timer that vibrates when the rest is over, even with the screen locked.
- Double-progression hints: when every set hits the top of the rep range, it suggests the next weight.
- Your data stays on your phone. The app has **no internet permission**.
- Backups: JSON file (restores everything) and CSV (for spreadsheets).

The ready-to-install app is the file **`LiftLog-1.0-release.apk`** at the top of this repository.

## Install it on your phone (from GitHub)

1. On your phone, open this repository in your browser and tap **`LiftLog-1.0-release.apk`**.
2. Tap the download button on that page (it may say **View raw** or show a download arrow). Wait for the download to finish. If your browser asks "This type of file can harm your device, keep it anyway?", tap **Keep** / **Download anyway**: the file is the app itself.
3. Open the downloaded file (tap the "Download complete" notification, or open the **Downloads** / **My Files** app and tap the file).
4. Android will probably say your phone **isn't allowed to install unknown apps from this source**. Tap **Settings**, switch on **Allow from this source** (the switch is for the app you used: Chrome, Samsung Internet, Files...), then press **Back**. The wording differs between phone brands, but it is always "allow installing apps from this source / unknown apps".
5. Tap **Install**. If Google Play Protect says it doesn't know the app, tap **More details › Install anyway**: the app is not on the Play Store, that is all.
6. Tap **Open**. You can switch "allow from this source" off again afterwards.
7. Tap **Start Day A** (any workout will do). The first time you start a workout Android asks to send notifications: tap **Allow**, because that is what shows the "rest over" message. Then go back, open the **Settings** tab in the app and tap **Test the alert: tap, then lock your phone**. Lock the phone and wait 5 seconds: it must buzz. If Settings says "Notifications: blocked", open the phone's Settings › Apps › Lift Log › Notifications and switch them on (the buzz is designed to work either way and only the written message needs it, but this has not been tried on a real phone).

**Samsung phones:** if the buzz is missing or late, open the phone's **Settings › Battery › Background usage limits** and make sure Lift Log is *not* under **Sleeping apps** (add it to **Never sleeping apps**).

## Installing a newer version

Download the new `.apk` the same way and install it **over** the old one. Never uninstall the app first: uninstalling erases all your workouts. Before updating, save a backup (below). The update only works because every version is signed with the same key; keep your signing key safe (see `signing/README-BACKUP.txt` on the computer that built the app, it is deliberately not in this repository).

## Back up your data

Settings › **Save backup to a file**. Pick Google Drive or any folder: that file is a full copy of everything. The app reminds you on the Workout tab if the last backup is more than 14 days old.
To restore (new phone, or after a reset): install the app, then Settings › **Import a backup file**. The app shows what it will replace, keeps a safety copy of what was there, and offers **Undo last import**.
"Share a copy" sends a copy through other apps but does not count as a saved backup.
Android's own automatic cloud backup is also switched on, but it only works if your Google backup is turned on, so keep making backup files too.

## For developers

Kotlin, Jetpack Compose (Material 3), Room. All build tools are portable and live in the git-ignored `.tools/` folder; run Gradle through `tools/gw.ps1` (Windows PowerShell), e.g. `.\tools\gw.ps1 :app:testDebugUnitTest` or `.\tools\gw.ps1 :app:assembleRelease`. The tests run on the JVM with Robolectric (no emulator). The design is in `SPEC.md`, the working notes in `TASKS.md`, and the rules for contributors/agents in `CLAUDE.md`. The release build needs `signing/keystore.properties`, which is never committed.
