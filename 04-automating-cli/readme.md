## 🔗 Official Links
- [Firebase Console](https://console.firebase.google.com/)
- [github-actions Docs](https://docs.github.com/en/actions/get-started/understand-github-actions)

________________________________________________
###  system images
- Go to [ruby-lang.org]( https://github.com/actions/runner-images) 
________________________________________________

###  firebase_cli_app_distribution.yml
```yml
name: firebase cli workflow

on:
  push:
    branches:
      - main

jobs:
  build-and-distribute:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo
        uses: actions/checkout@v6

  

      - name: Set up Java
        uses: actions/setup-java@v5
        with:
          distribution: 'temurin'
          java-version: '21'

      - name: Set up Flutter
        uses: subosito/flutter-action@v2
        with:
          channel: 'stable'
          cache: true
      - name: Install dependencies
        run: flutter pub get

      - name: Build APK
        run: flutter build apk --release --no-tree-shake-icons

      - name: Upload artifact
        uses: actions/upload-artifact@v6
        with:
          name: upload release-apk
          path: build/app/outputs/flutter-apk/app-release.apk

      - name: Authenticate to Google Cloud
        uses: google-github-actions/auth@v2
        with: 
         credentials_json: ${{ secrets.GOOGLE_CREDENTIALS }}

      - name: Install Firebase CLI
        run: npm install -g firebase-tools
        

      - name: Distribute to Firebase
        run: |
           firebase appdistribution:distribute build/app/outputs/flutter-apk/app-release.apk \
            --app "1:550549398462:android:7cd28669c72c459c5f0fef" \
            --testers "m7mdmakenstudy@gmail.com" \
            --release-notes "test"
            
```
### last commit => release notes :
```
 RELEASE_NOTES=$(git log -1 --pretty=%B | tr '\n' ' ' | xargs)
 --release-notes "$RELEASE_NOTES"
```
