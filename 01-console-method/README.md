## 🔗 Official Links
- [Firebase Console](https://console.firebase.google.com/)
- [Firebase App Distribution Docs](https://firebase.google.com/docs/app-distribution/android/distribute-console)
- [Download App Tester](https://appdistribution.firebase.google.com/)

____________________________________________________________________________
### 1. Login to Firebase
```bash
firebase login
```

### 2. Activate FlutterFire CLI
```bash
dart pub global activate flutterfire_cli
```

### 3. Configure Firebase in Your Project
```bash
flutterfire configure
```
### 4. Build Android APK
```bash
flutter build apk
```
The APK will be located at:
```
build/app/outputs/flutter-apk/app-release.apk
```
### 5. Distribute via Firebase Console
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select your project
3. Navigate to App Distribution
4. Click "Distribute" button
5. Upload your APK
6. Add testers
7. Send invitation
______________________________________________
download app tester =>
https://appdistribution.firebase.google.com/
______________________________________________
