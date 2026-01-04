## 🔗 Official Links
- [Firebase Console](https://console.firebase.google.com/)
- [Fastlane Docs](https://docs.fastlane.tools/getting-started/android/setup/)
- [Firebase App Distribution Docs](https://firebase.google.com/docs/app-distribution/android/distribute-fastlane?apptype=apk)
  

________________________________________________
### 1. Download ruby
- Go to [ruby-lang.org]( https://www.ruby-lang.org/en/downloads/) and download the latest version of Ruby.
________________________________________________
### 2. Verify ruby installation
```bash
ruby --version
```
________________________________________________
### 3. Install bundler
```bash
gem install bundler
```
________________________________________________
### 4. Go to android folder 
 
```bash
cd android
```
________________________________________________
### 5. initialize fastlane
```bash
fastlane init
```
________________________________________________
### 6. Install fastlane firebase plugin
```bash
fastlane add_plugin firebase_app_distribution

```
### 7. Authenticate with Firebase
- Go to [Firebase Service Accounts](https://console.cloud.google.com/projectselector2/iam-admin/serviceaccounts) and generate a new private key .

### 8. fastfile
```ruby
default_platform(:android)

platform :android do
  desc "Build and distribute Android app to Firebase"
  lane :distribute_to_firebase do
    # Build the Flutter app
    sh "flutter clean"
    sh "flutter build apk --release --no-tree-shake-icons"
    
    # Upload to Firebase App Distribution
    firebase_app_distribution(
      app: "",
      testers: "",
      release_notes: "",
      android_artifact_type: "APK",
      android_artifact_path: "../build/app/outputs/flutter-apk/app-release.apk",
      upload_timeout: 800,
      service_credentials_file: "C:/s.json"
    )
  end
end
```
