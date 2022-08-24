<p align="center">
  <img width="100" height="100" src="https://raw.githubusercontent.com/gdgcloudkol/ccd2022-app/main/android/app/src/main/res/mipmap-xxhdpi/ic_launcher.png">
</p>

<br>

## CCD Kolkata 2022

This repo contains source code for the official Flutter app of Cloud Community Days Kolkata 2022. 

 :construction:**Actively under development**:construction:
- <details>
  <summary><b>Screenshots</b></summary>
  <br>
  
  <img width = "200" height = "400" src="https://raw.githubusercontent.com/gdgcloudkol/ccd2022-app/main/data/Screenshots/Google%20Pixel%204%20XL%20Screenshot%201.png">
  &nbsp;
  <img width = "200" height = "400" src="https://raw.githubusercontent.com/gdgcloudkol/ccd2022-app/main/data/Screenshots/Google%20Pixel%204%20XL%20Screenshot%202.png">
  &nbsp;
  <img width = "200" height = "400" src="https://raw.githubusercontent.com/gdgcloudkol/ccd2022-app/main/data/Screenshots/Google%20Pixel%204%20XL%20Screenshot%203.png">
  &nbsp;
  <img width = "200" height = "400" src="https://raw.githubusercontent.com/gdgcloudkol/ccd2022-app/main/data/Screenshots/Google%20Pixel%204%20XL%20Screenshot%204.png">
  
</details>

- #### Features

  * Sessionize Api Integrated for speakers profile and schedule management
  * Support for multiple sessions in same timeslot
  * Self Hosted using Firebase
  * FCM for notification
  * Built using [Provider Architecture](https://pub.dev/packages/provider) for clean state management
  * Google Auth for User Authentication
  * Custom user management logic using Firestore
  * Data caching for optimised network calls
  * Ticket application and view
  * Dashboard Screen (**Bonus : Refer & Earn Logic Integrated**)
  * Profile Screen for event participants
  * Dynamic Partners Screen Using GitHub Hosted Json
  * Fluid animations
  * Custom Navigation Stack
  * Modern, Material UI (we all love this!)
  * Heavyily documented code (who doesn't like clean code)
  

## Getting Started

This project depends heavily on firebase. A few resources to get you started if this is your first Firebase project:

- [Lab: Firebase for Flutter](https://firebase.google.com/codelabs/firebase-get-to-know-flutter#0)
- [FlutterFire Plugins](https://firebase.flutter.dev/)

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

Project Setup :

* Flutter App:
  * [Install Flutter](https://docs.flutter.dev/get-started/install)
  * [Setting up your ide](https://flutter.io/ide-setup/)
  * Fork and clone this repository.
  * cd into `ccd2022-app` directory.
  * Run `flutter clean` command.
  * Run `flutter pub get` command.
  * Run `flutter run` command.
  
* Firebase:
  * Create a firebase project
  * Add android app with your package name in firebase console.
  * Enable Google Auth from `Authentication` menu in Firebase.
  * Generate `SHA-1 key hash` for your debug keystore from your pc. This needs to be added to `SHA certificate fingerprints` section under your android app in `Firebase project settings`. Without this step **Google login** won't work.
  * Enable ***Cloud Firestore***
    * Recommended rules for Firestore 
    
        ```JS
          rules_version = '2';
          service cloud.firestore {
            match /databases/{database}/documents {

             match /tickets/{ticket} {
              allow read : if request.auth != null;
              allow write: if false;
             }

            match /{document=**} {
              allow read, write: if request.auth != null;
            }

          }
         }
       ```
    * Recommended Rules for Cloud Storage
        
        ```JS
          rules_version = '2';
          service firebase.storage {
            match /b/{bucket}/o {
              match /{allPaths=**} {
                allow read: if true;
                allow write: if false;
                allow create: if false;
                allow update: if false;
              }
            }
          }
        ```
        
  * Enable ***Cloud Storage***
  * Download `google_services.json` from `Console` -> `Project Settings`. File is present in app section. SDK instructions found in the same page
  * (Optional) Enable ***Cloud Messaging*** from Firebase Console if you wan't notifications to work in your app
  * (Optional) If released to play store get `SHA-1 key hash` from playstore and upload them to firebase, otherwise google sign in won't work in play store app.

* ## How to Contribute to this repo?
  
    Check [Contributing.md](https://github.com/gdgcloudkol/ccd2022-app/blob/main/CONTRIBUTING.md) for guidelines on contributing to this repo.

## Contact Us

If you have a question, please feel free to [contact us](https://gdgcloud.kolkata.dev/#Contact) through email or our telegram community channel.

<br><br><br><br>

<p align="center">
  Made with ❤️ by GDG Cloud Kolkata
  <br><br>
  <a href="https://opensource.org/licenses/MIT"> <img src="https://img.shields.io/badge/License-MIT-yellow.svg" /> </a>
</p>
