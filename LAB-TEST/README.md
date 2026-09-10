# Campus Event Registration – TechConnect 2026

## Experiment Title

**Campus Event Registration – TechConnect 2026**

---

## Aim

To develop an Android application for **Campus Event Registration** that allows students to register for the technical event **TechConnect 2026** using basic Android Views, Kotlin, XML, Intents, Notifications, and Activity Lifecycle methods.

---

## Objective

The objectives of this experiment are:

- To design a Home Activity for the TechConnect 2026 event.
- To display the college logo, application title, and event description.
- To navigate from the Home Activity to the Registration Activity using an Explicit Intent.
- To collect student details using different Android Views.
- To implement EditText, RadioButton, RadioGroup, CheckBox, ToggleButton, and Button.
- To validate the registration form.
- To navigate to a Confirmation Activity after successful registration.
- To pass the student's name and selected event category between Activities.
- To generate an Android notification after successful registration.
- To implement suitable Activity Lifecycle methods.
- To display Activity Lifecycle messages in Logcat.

---

## Scenario

A college is organizing a technical event called **TechConnect 2026**.

An Android application is developed to allow students to register for the event.

The application consists of three Activities:

### 1. Home Activity

The Home Activity displays:

- College Logo
- Application Title – **TechConnect 2026**
- Short description of the event
- **Register Now** button

### 2. Registration Activity

The Registration Activity allows students to enter:

- Student Name
- USN
- Email
- Gender
- Event Category
- Agreement to Event Rules
- Participation Certificate requirement

### 3. Confirmation Activity

After successful submission, the Confirmation Activity displays:

- Student Name
- Selected Event Category
- Successful registration message

An Android notification is also generated indicating that the registration was successful.

---

## Technology Used

| Technology | Description |
|---|---|
| **Android Studio** | Integrated Development Environment |
| **Kotlin** | Programming language |
| **XML** | User Interface design |
| **Android SDK** | Android application development framework |
| **Gradle** | Build and dependency management |
| **Android Views** | Used to create the application interface |
| **Intent** | Used for navigation between Activities |
| **Notification API** | Used to generate registration notification |
| **Logcat** | Used to display Activity Lifecycle messages |
| **GitHub** | Used for project submission and version control |

---

## Android Views Used

| Android View | Purpose |
|---|---|
| **ImageView** | Displays the college logo |
| **TextView** | Displays the application title, description, labels, and confirmation message |
| **EditText** | Accepts Student Name, USN, and Email |
| **RadioButton** | Allows selection of Gender and Event Category |
| **RadioGroup** | Groups the Gender and Event Category RadioButtons |
| **CheckBox** | Allows the student to agree to the event rules |
| **ToggleButton** | Allows selection of Participation Certificate requirement |
| **Button** | Used for Register Now and Submit Registration |
| **Toast** | Displays validation messages |
| **ScrollView** | Allows the registration form to be scrolled |

---
## Concepts Used

The following Android development concepts are used in this application:

1. **Android Activities**
   - The application uses three Activities:
     - `MainActivity`
     - `RegistrationActivity`
     - `ConfirmationActivity`

2. **XML Layout Design**
   - XML is used to design the user interface of all Activities.

3. **Android Views**
   - `TextView`
   - `ImageView`
   - `EditText`
   - `Button`
   - `RadioButton`
   - `RadioGroup`
   - `CheckBox`
   - `ToggleButton`
   - `ScrollView`

4. **Explicit Intent**
   - Used to navigate from one Activity to another within the application.

5. **Intent Data Passing**
   - `putExtra()` is used to pass the student's name and event category.
   - `getStringExtra()` is used to retrieve the passed data.

6. **Event Handling**
   - `setOnClickListener()` is used to handle button click events.

7. **User Input Validation**
   - The application checks whether required fields are entered and whether required options are selected.

8. **RadioGroup and RadioButton**
   - Used to allow the user to select Gender and Event Category.

9. **CheckBox**
   - Used to confirm that the student agrees to the event rules.

10. **ToggleButton**
    - Used to select whether the student requires a participation certificate.

11. **Toast Messages**
    - Used to display validation and error messages to the user.

12. **Android Notifications**
    - A notification is generated after successful registration.

13. **Notification Channel**
    - A notification channel is created for Android 8.0 and above.

14. **Runtime Permission**
    - `POST_NOTIFICATIONS` permission is requested for Android 13 and above.

15. **Activity Lifecycle**
    - Lifecycle methods such as `onCreate()`, `onStart()`, `onResume()`, `onPause()`, `onStop()`,
   

## Project Structure

```text
TechConnect2026/
│
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/
│   │   │   │       └── example/
│   │   │   │           └── techconnect2026/
│   │   │   │               ├── MainActivity.kt
│   │   │   │               ├── RegistrationActivity.kt
│   │   │   │               └── ConfirmationActivity.kt
│   │   │   │
│   │   │   ├── res/
│   │   │   │   ├── drawable/
│   │   │   │   │   └── college_logo.png
│   │   │   │   │
│   │   │   │   ├── layout/
│   │   │   │   │   ├── activity_main.xml
│   │   │   │   │   ├── activity_registration.xml
│   │   │   │   │   └── activity_confirmation.xml
│   │   │   │   │
│   │   │   │   └── values/
│   │   │   │
│   │   │   └── AndroidManifest.xml
│   │   │
│   │   └── test/
│   │
│   └── build.gradle.kts
│
├── screenshots/
│   ├── home-screen.png
│   ├── registration-form.png
│   ├── confirmation.png
│   ├── notification.png
│   └── lifecycle-logcat.png
│
├── build.gradle.kts
├── settings.gradle.kts
├── gradle.properties
├── gradlew
├── gradlew.bat
├── .gitignore
└── README.md



## Project Structure
