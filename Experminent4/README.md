#  Login Intent App

> **Experiment 4 – Implement an Android Application to Demonstrate Linking Activities Using Intents**

---

##  Aim

To develop an Android application that demonstrates **linking activities using Explicit Intents** by implementing a Login screen and a Dashboard screen. The application validates user credentials and navigates to the dashboard after successful authentication.

---

## Objective

- Develop a Login interface using XML.
- Implement Explicit Intents for navigation.
- Validate user credentials.
- Pass data between Activities using Intent Extras.
- Create a simple and attractive user interface.
- Understand Activity lifecycle and Intent communication.

---

##  Technology Used

- **Programming Language:** Kotlin
- **IDE:** Android Studio
- **UI Design:** XML
- **Android SDK:** API 37
- **Build Tool:** Gradle (Kotlin DSL)
- **Version Control:** Git & GitHub

---

##  Concepts Used

- Android Activities
- Explicit Intent
- Intent Extras
- EditText
- Button
- TextView
- ImageView
- RelativeLayout
- LinearLayout
- Drawable Resources
- Gradient Background
- Event Handling
- User Input Validation
- Toast Messages
- Material Design

---

#  Project Structure

```
LoginIntentApp
│
├── app
│   ├── manifests
│   │      └── AndroidManifest.xml
│   │
│   ├── java
│   │      ├── MainActivity.kt
│   │      └── DashboardActivity.kt
│   │
│   └── res
│       ├── drawable
│       │      ├── background_gradient.xml
│       │      ├── button_background.xml
│       │      ├── edittext_background.xml
│       │      ├── wave_bottom.xml
│       │      ├── ic_person.xml
│       │      └── ic_lock.xml
│       │
│       ├── layout
│       │      ├── activity_main.xml
│       │      └── activity_dashboard.xml
│       │
│       └── values
│
├── gradle
├── build.gradle.kts
└── README.md
```

---

#  Working

1. Launch the application.
2. Login screen is displayed.
3. Enter the username and password.
4. Click the **Login** button.
5. Credentials are validated.
6. If valid, the Dashboard Activity opens using an Explicit Intent.
7. Username is passed through Intent Extras.
8. Dashboard displays the welcome message.
9. Click **Logout** to return to the Login screen.

---

#  Login Credentials

| Username | Password |
|----------|----------|
| **admin** | **1234** |

---

# 📹 Output Video

Upload your screen recording inside the repository as:

```
output_demo.mp4
```

or inside a folder:

```
screen-recording/
    output_demo.mp4
```

---

# 📸 Screenshots Folder

Create a folder named:

```
screenshots
```

Add these files:

```
screenshots
│
├── login_screen.png
├── dashboard_screen.png
└── invalid_login.png
```

---

#  Source Code

### Main Files

- MainActivity.kt
- DashboardActivity.kt
- activity_main.xml
- activity_dashboard.xml
- AndroidManifest.xml

---

#  Features

- Beautiful Login UI
- Dashboard Screen
- Explicit Intent Navigation
- User Authentication
- Logout Functionality
- Modern Gradient Design
- Rounded UI Components

---

#  Result

The Android application was successfully developed to demonstrate **Activity Navigation using Explicit Intents**. The application authenticates user credentials, navigates from the Login screen to the Dashboard screen, and passes data between Activities using Intent Extras.

---

