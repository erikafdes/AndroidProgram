# Data Persistence Android Application

## Experiment 9 : Data Persistence using SharedPreferences and SQLite

This Android application demonstrates **data persistence** using **SharedPreferences** and **SQLite Database**. The application provides a simple login interface where the username and password are automatically saved and restored using SharedPreferences, while every login attempt is stored as a separate record in an SQLite database.

## Objectives
To understand the process of publishing an Android application on the Google Play Store.
To learn how to create and configure a Google Play Console developer account.
To generate a signed Android App Bundle (.aab) using Android Studio.
To prepare the application with the required store listing information, screenshots, icon, and descriptions.
To understand and complete the required app content, privacy, data safety, and content rating information.
To learn how to upload, test, and release an Android application through Google Play Console.
To understand the process of submitting an application for review and making it available to users.


## Procedure
Develop the Android application using Android Studio and test all its features using an emulator or physical Android device.
Create a Google Play Console developer account using a Google account and complete the required registration and verification process.
Open the completed Android project in Android Studio and check the application ID, version code, version name, application icon, permissions, and other release configurations.
Generate a signed Android App Bundle by selecting Build → Generate Signed Bundle / APK → Android App Bundle. Create or select a keystore and generate the release .aab file.
Log in to Google Play Console and select Create app. Enter the application name, default language, application type, free or paid status, and other required details.
Prepare the Store Listing by providing the application name, short description, full description, application icon, screenshots, category, and contact information.
Complete the required App Content sections, including privacy policy, app access, ads, target audience, content rating, and data safety information, according to the actual functionality of the application.
Create a testing release using the appropriate testing track and upload the generated signed .aab file.
Test the application with the selected testers, identify any errors or issues, and make the necessary corrections.

## Features

* Simple username and password login screen
* Username and password are saved using SharedPreferences
* Previously entered username and password are automatically filled when the application is reopened
* Username and password are stored in an SQLite database
* Every login creates a new record in the database
* Previous login records are not deleted
* Logout button available at the top-right corner
* Local database storage without requiring an internet connection
* Demonstrates Android data persistence concepts

## Technologies Used

* **Language:** Kotlin
* **Platform:** Android
* **IDE:** Android Studio
* **UI:** XML
* **Database:** SQLite
* **Data Persistence:** SharedPreferences

## Application Flow

```text
Open Application
       |
       v
Username and Password
       |
       v
     Login
       |
       +----------------------+
       |                      |
       v                      v
SharedPreferences          SQLite
       |                      |
       v                      v
Save latest              Add new login
credentials               record
       |                      |
       +----------+-----------+
                  |
                  v
          Login Successful
```

## SharedPreferences

SharedPreferences is used to store the latest username and password as key-value pairs.

Example:

```text
username = Erika
password = 12345
```

When the application is opened again, these values are retrieved from SharedPreferences and automatically displayed in the username and password fields.


## Project Structure

```text
DataPersistenceApp/
│
├── app/
│   └── src/
│       └── main/
│           ├── java/
│           │   └── package/
│           │       ├── MainActivity.kt
│           │       └── DatabaseHelper.kt
│           │
│           ├── res/
│           │   └── layout/
│           │       └── activity_main.xml
│           │
│           └── AndroidManifest.xml
│
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

## Main Components

### MainActivity.kt

`MainActivity` manages the login interface and handles:

* Username input
* Password input
* Login button
* Logout button
* SharedPreferences
* SQLite database insertion

### DatabaseHelper.kt

`DatabaseHelper` extends `SQLiteOpenHelper` and manages the SQLite database.

It is responsible for:

* Creating the database
* Creating the `users` table
* Inserting login records
* Managing database upgrades

### activity_main.xml

The XML layout provides:

* Username field
* Password field
* Login button
* Logout button
* Application title



## Screenshots
<img width="720" height="1600" alt="WhatsApp Image 2026-10-01 at 1 13 22 PM (2)" src="https://github.com/user-attachments/assets/538cc033-cf44-4207-8cc7-6cd22e051be9" />
<img width="720" height="1600" alt="WhatsApp Image 2026-10-01 at 1 13 22 PM" src="https://github.com/user-attachments/assets/80afadce-309f-4499-8b8c-997aea8622bc" />



