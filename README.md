# 🔐 Google Sign-In with Flutter

Welcome to this tutorial on integrating **Google Sign-In** with **Flutter**! This guide walks you through setting up Firebase, configuring your Flutter project, and allowing users to sign in using their Google accounts.
 
📁 **Tutorial Reel:** [Coming Soon]

- `starter` – Start here and follow along with the video
- `main` – Final version of the completed project

---

## ✨ What You'll Learn

- Set up Firebase for authentication  
- Integrate Google Sign-In into a Flutter app  
- Authenticate users and fetch profile data  
- Display the user's name, email, and profile photo  

---

## 🧰 Prerequisites

- Flutter SDK installed  
- Firebase account and project  
- Basic knowledge of Flutter  
- A connected device or emulator  

---

## 🚀 Getting Started

### 1. Clone the Project

```bash
git clone https://github.com/lumberjack-programmer/google_oauth_flutter.git
```

```bash
cd google_oauth_flutter
```

```bash
git checkout start
```

```bash
flutter pub get
```

### 2. Set Up Firebase
1. Go to Firebase Console

2. Create a new project

3. Add Android/iOS app to the project

4. Download:

`google-services.json` → place it in `android/app/`

`GoogleService-Info.plist` → drag & drop it in `ios/Runner/` using XCode!


3. Enable Google Sign-In Provider in the Authentication > Sign-in method section

### 3. Android Configuration
In `android/build.gradle`:

```bash
classpath 'com.google.gms:google-services:4.4.2'
```

In `android/app/build.gradle`:

```bash
apply plugin: 'com.google.gms.google-services'
```

### 4. iOS Configuration

In `ios/Runner/Info.plist`, add:

```xml
<key>CFBundleURLTypes</key>
<array>
  <dict>
    <key>CFBundleURLSchemes</key>
    <array>
      <string>[REVERSED_CLIENT_ID]</string>
    </array>
  </dict>
</array>
```

Replace `[REVERSED_CLIENT_ID]` with the value from your `GoogleService-Info.plist`.

📦 Dependencies Used

```yml
dependencies:
  firebase_core: ^3.13.0
  firebase_auth: ^5.5.3
  google_sign_in: ^6.3.0
```

🧭 Folder Structure

```
lib/
├── main.dart
├── screens/
│   ├── login/
│   │   └── login_screen.dart
│   ├── home/
│   │   └── home_screen.dart

```

### 🛠️ Troubleshooting
🔐 SHA-1 Not Registered for Android: Use keytool to get SHA-1 and register it in Firebase settings.

Genearte SHA-1 key (With Android Studio)

```
keytool -genkeypair -v \
  -keystore my-release-key.jks \
  -keyalg RSA \
  -keysize 2048 \
  -validity 10000 \
  -alias my-key-alias

```

or 

Run these commands (no Android Studio):

```bash
cd android

./gradlew signingReport
```

🔑 After the keytool is available. Run the following command to display:

```bash
keytool -list -v -alias androiddebugkey -keystore ~/.android/debug.keystore -storepass android -keypass android
```

Copy the SHA-1 and paste it in your Firebase project under:

`Project settings` → ` Your Android app` → `Add fingerprint`


⚠️ Client ID Mismatch: Make sure the downloaded Firebase config files are correct.

🍏 iOS Setup (IMPORTANT)
✅ Do NOT just move `GoogleService-Info.plist` into the folder manually.

To properly configure Firebase on iOS:

Open your Flutter project in Xcode:
1. open `ios/Runner.xcworkspace`

2. Drag & Drop the `GoogleService-Info.plist` file into the Runner project in the Xcode Project Navigator (left panel), ideally under the `Runner` folder.

3. In the dialog that appears:
- ✅ Check "Copy items if needed"
- ✅ Make sure `Runner` target is selected
- Click Finish

4. Make sure `GoogleService-Info.plist` appears in Xcode under `Runner`.

### 🙌 Contributions
Pull requests are welcome! If you find an issue or want to enhance the tutorial, feel free to contribute.

### 📫 Contact
Follow me on:

Instagram: [@lumberjack-programmer](https://www.instagram.com/lumberjack_programmer) 

X (Twitter): [@dmPedan](https://x.com/DmPedan) 
 
LinkedIn: [Dmytro Pedan](https://www.linkedin.com/in/dmytro-pedan/)

TikTok: [@lumberjackprogram](https://www.tiktok.com/@lumberjackprogram)
