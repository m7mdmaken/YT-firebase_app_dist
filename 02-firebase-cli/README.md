## 🔗 Official Links
- [Firebase Console](https://console.firebase.google.com/)
- [Firebase App Distribution Docs](https://firebase.google.com/docs/app-distribution/android/distribute-cli?apptype=apk)
- [Download App Tester](https://appdistribution.firebase.google.com/)

____________________________________________________________________________
### 1. Build Android APK
```bash
flutter build apk
```
The APK will be located at:
```
build/app/outputs/flutter-apk/app-release.apk
```
### 2.in your project terminal
```bash
firebase appdistribution:distribute "path-to-apk" --app YOUR_FIREBASE_APP_ID --release-notes "release-notes" --testers "emails-with-comma-seperated"
```
with files 
```bash
firebase appdistribution:distribute "path-to-apk" --app YOUR_FIREBASE_APP_ID --release-notes-file "path-to-release-notes-file" --testers-file "path-to-testers-file"
```
___________________________________________________________________
### 3. vs code tasks
#### CTRL+SHIFT+P
#### Tasks: Open User Tasks

```bash
 {
      "label": "Flutter: Build Release APK",
      "type": "shell",
      "command": "flutter build apk --release",
      "problemMatcher": []
    },
    {
      "label": "Firebase: Distribute APK",
      "type": "shell",
      "command": "firebase appdistribution:distribute \"${workspaceFolder}/build/app/outputs/flutter-apk/app-release.apk\" --app ${input:firebaseAppId} --release-notes \"${input:releaseNotes}\" --testers \"${input:testers}\"",
      "problemMatcher": [],
      "presentation": {
        "reveal": "always",
        "panel": "new"
      },
      "dependsOn": [
        "Flutter: Build Release APK"
      ],
      "dependsOrder": "sequence"
    }
  ],
  "inputs": [
    {
      "id": "firebaseAppId",
      "type": "promptString",
      "description": "Firebase App ID (e.g., 1:xxxxx:android:xxxxx)"
    },
    {
      "id": "releaseNotes",
      "type": "promptString",
      "description": "Release notes"
    },
    {
      "id": "testers",
      "type": "promptString",
      "description": "Tester emails (comma-separated list)"
    }
```
#### CTRL+SHIFT+P
#### Tasks: Run Task
