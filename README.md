# ReactNativeFirebase

React Native app with **Firebase** (App, Auth, Firestore) for Android and iOS.

- **React Native** 0.82.1  
- **@react-native-firebase/app**, **auth**, **firestore** (v23.x)  
- **Node** >= 22.11.0  

---

## Prerequisites

- [React Native environment](https://reactnative.dev/docs/set-up-your-environment) (Node, JDK, Android Studio / Xcode)
- A [Firebase project](https://console.firebase.google.com/) with your app registered for Android and iOS
- **iOS:** Ruby (for CocoaPods), Xcode, CocoaPods  
- **Android:** Android Studio, SDK 24+, Gradle  

---

## Installation

```bash
npm install
```

---

## iOS setup

### Already configured in the project

- **AppDelegate** (`ios/ReactNativeFirebase/AppDelegate.swift`): `FirebaseCore` imported and `FirebaseApp.configure()` called in `didFinishLaunchingWithOptions`.
- **Podfile** (`ios/Podfile`): `use_frameworks! :linkage => :static` and `$RNFirebaseAsStaticFramework = true` for React Native Firebase.

### What you need to do

1. **Add Firebase config file**
   - In [Firebase Console](https://console.firebase.google.com/) → Project settings → Your apps → iOS app, download **GoogleService-Info.plist**.
   - Put it in: `ios/ReactNativeFirebase/GoogleService-Info.plist`.
   - Add it to the Xcode project (drag into the `ReactNativeFirebase` group and ensure “Copy items if needed” and the app target are checked).

2. **Install CocoaPods and pods**

   ```bash
   cd ios
   bundle install
   bundle exec pod install
   cd ..
   ```

3. **Run the app**

   ```bash
   npm run ios
   ```

---

## Android setup

### Already configured in the project

- **Application ID:** `com.reactnativefirebase` (in `android/app/build.gradle` and `AndroidManifest.xml`).
- **MainApplication.kt** uses React Native’s default setup; Firebase packages are linked via autolinking.

### What you need to do

1. **Add Firebase config file**
   - In [Firebase Console](https://console.firebase.google.com/) → Project settings → Your apps → Android app, download **google-services.json**.
   - Put it in: `android/app/google-services.json`.

2. **Enable Google Services plugin**
   - **Root** `android/build.gradle`: in `buildscript.dependencies`, add:
     ```gradle
     classpath("com.google.gms:google-services:4.4.2")
     ```
   - **App** `android/app/build.gradle`: at the bottom of the file, add:
     ```gradle
     apply plugin: "com.google.gms.google-services"
     ```

3. **Run the app**

   ```bash
   npm run android
   ```

---

## Running the app

1. Start Metro (from project root):

   ```bash
   npm start
   ```

2. In another terminal:

   - **iOS:** `npm run ios`  
   - **Android:** `npm run android`  

---

## Project structure (relevant parts)

| Path | Purpose |
|------|--------|
| `App.tsx` | Root component (SafeAreaProvider, NewAppScreen) |
| `ios/ReactNativeFirebase/AppDelegate.swift` | iOS entry; Firebase init |
| `ios/Podfile` | iOS pods; Firebase static framework flags |
| `android/app/build.gradle` | App ID, signing, dependencies |
| `android/app/src/main/.../MainApplication.kt` | Android app entry |

---

## Scripts

| Command | Description |
|--------|-------------|
| `npm start` | Start Metro bundler |
| `npm run ios` | Run iOS app |
| `npm run android` | Run Android app |
| `npm run lint` | Run ESLint |
| `npm test` | Run Jest tests |

---

## Learn more

- [React Native](https://reactnative.dev)
- [React Native Firebase](https://rnfirebase.io/)
