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

## Application Flow

```text
                    ┌──────────────────────┐
                    │     Home Activity    │
                    │                      │
                    │ College Logo         │
                    │ TechConnect 2026     │
                    │ Event Description    │
                    │ Register Now         │
                    └──────────┬───────────┘
                               │
                        Explicit Intent
                               ↓
                    ┌──────────────────────┐
                    │ Registration Activity│
                    │                      │
                    │ Student Name         │
                    │ USN                  │
                    │ Email                │
                    │ Gender               │
                    │ Event Category       │
                    │ Event Rules          │
                    │ Certificate          │
                    │ Submit Registration  │
                    └──────────┬───────────┘
                               │
                        Explicit Intent
                        + putExtra()
                               ↓
                    ┌──────────────────────┐
                    │ Confirmation Activity│
                    │                      │
                    │ Registration         │
                    │ Successful           │
                    │                      │
                    │ Student Name         │
                    │ Event Category       │
                    └──────────┬───────────┘
                               │
                               ↓
                    ┌──────────────────────┐
                    │ Android Notification │
                    │                      │
                    │ Registration was     │
                    │ successful!          │
                    └──────────────────────┘

##Working of the Application
Step 1 – Launch Application

When the application is launched, the Home Activity is displayed.

It contains:

College Logo
TechConnect 2026 title
Short description of the technical event
Register Now button
Step 2 – Navigate to Registration Activity

When the user clicks the Register Now button, an Explicit Intent is used to open the Registration Activity.

val intent = Intent(
    this,
    RegistrationActivity::class.java
)

startActivity(intent)
Step 3 – Enter Student Details

The student enters the following details:

Student Name
USN
Email

These details are collected using EditText.

Step 4 – Select Gender

The student selects one option from the Gender RadioGroup.

The Gender options are implemented using RadioButton.

Only one gender can be selected at a time.

Step 5 – Select Event Category

The student selects one Event Category from the Event Category RadioGroup.

The category is selected using RadioButton.

Only one event category can be selected at a time.

Step 6 – Agree to Event Rules

The student selects:

"I agree to the event rules"

using the CheckBox.

The application checks whether the checkbox is selected before allowing the registration to continue.

if (!rules.isChecked) {

    Toast.makeText(
        this,
        "Please agree to the event rules",
        Toast.LENGTH_SHORT
    ).show()

    return@setOnClickListener
}
Step 7 – Participation Certificate

The student uses the ToggleButton to specify whether a participation certificate is required.

The ToggleButton has two states:

ON – Participation Certificate Required
OFF – Participation Certificate Not Required

The selected state is obtained using:

val certificateRequired =
    certificate.isChecked
Step 8 – Submit Registration

The student clicks the Submit Registration button.

The application validates the entered information.

The following details are validated:

Student Name
USN
Email
Gender
Event Category
Event Rules

If the Student Name, USN, or Email is empty, the application displays an appropriate error message.

If Gender or Event Category is not selected, a Toast message is displayed.

If the event rules are not accepted, the registration is not completed.

Step 9 – Navigate to Confirmation Activity

After successful validation, an Explicit Intent is used to open the ConfirmationActivity.

The student's name and selected event category are passed from the Registration Activity using putExtra().

intent.putExtra(
    "studentName",
    name
)

intent.putExtra(
    "category",
    selectedCategory
)
Step 10 – Retrieve Registration Details

The Confirmation Activity retrieves the information using getStringExtra().

val name =
    intent.getStringExtra(
        "studentName"
    )

val category =
    intent.getStringExtra(
        "category"
    )

The retrieved information is displayed in the Confirmation Activity.

Example:

Dear Rashmi Kumari,

Your registration for TechConnect 2026
has been successfully completed.

Event Category: Technical
Step 11 – Generate Notification

After successful registration, the application creates an Android notification.

The notification displays:

TechConnect 2026

Registration was successful!

A Notification Channel named TechConnect Registration is created for Android 8.0 and above.

The channel uses high importance for the registration notification.

Activity Lifecycle

The application implements suitable Activity Lifecycle methods in all three Activities.

The following lifecycle methods are implemented:

onCreate()
onStart()
onResume()
onPause()
onStop()
onDestroy()

Lifecycle messages are displayed in Android Studio Logcat using the tag:

ActivityLifecycle
MainActivity Lifecycle

When the application starts, the following messages are generated:

MainActivity - onCreate
MainActivity - onStart
MainActivity - onResume

When the Register Now button is clicked:

MainActivity - onPause
MainActivity - onStop
RegistrationActivity Lifecycle

When Registration Activity is opened:

RegistrationActivity - onCreate
RegistrationActivity - onStart
RegistrationActivity - onResume

When Submit Registration is clicked:

RegistrationActivity - onPause
RegistrationActivity - onStop
ConfirmationActivity Lifecycle

When Confirmation Activity is opened:

ConfirmationActivity - onCreate
ConfirmationActivity - onStart
ConfirmationActivity - onResume

These messages demonstrate the Activity Lifecycle during navigation between the three Activities.

Application Features
College logo display
TechConnect 2026 application title
Short event description
Register Now button
Student Name input
USN input
Email input
Gender selection
Event Category selection
Event Rules agreement
Participation Certificate selection
Input validation
Explicit Intent navigation
Data passing between Activities
Confirmation Activity
Successful registration message
Android notification
Activity Lifecycle implementation
Logcat lifecycle messages
Project Structure
TechConnect2026/
│
├── app/
│   ├── src/
│   │   ├── androidTest/
│   │   │
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
Important Kotlin Concepts Used
1. findViewById()

The findViewById() method is used to access the Views defined in the XML layout.

Example:

val studentName =
    findViewById<EditText>(
        R.id.etStudentName
    )
2. setOnClickListener()

The setOnClickListener() method is used to perform an action when a Button is clicked.

Example:

submit.setOnClickListener {
    // Registration logic
}
3. Explicit Intent

An Explicit Intent is used to navigate from one Activity to another Activity within the same application.

Example:

val intent = Intent(
    this,
    RegistrationActivity::class.java
)

startActivity(intent)
4. Passing Data Using putExtra()

The student's name and selected event category are passed to the Confirmation Activity using putExtra().

intent.putExtra(
    "studentName",
    name
)

intent.putExtra(
    "category",
    selectedCategory
)
5. Retrieving Data Using getStringExtra()

The Confirmation Activity retrieves the data passed through the Intent using getStringExtra().

val name =
    intent.getStringExtra(
        "studentName"
    )

val category =
    intent.getStringExtra(
        "category"
    )
6. RadioButton and RadioGroup

RadioGroup is used to group related RadioButtons.

For example, the Gender RadioGroup allows the user to select only one gender.

The Event Category RadioGroup allows the user to select only one event category.

The selected RadioButton is identified using:

categoryGroup.checkedRadioButtonId
7. CheckBox

The CheckBox is used for the event rules agreement.

if (!rules.isChecked) {

    Toast.makeText(
        this,
        "Please agree to the event rules",
        Toast.LENGTH_SHORT
    ).show()

    return@setOnClickListener
}
8. ToggleButton

The ToggleButton is used to determine whether the student requires a participation certificate.

val certificateRequired =
    certificate.isChecked
9. Notification Channel

A Notification Channel is created for Android 8.0 and above.

val channel = NotificationChannel(
    CHANNEL_ID,
    "TechConnect Registration",
    NotificationManager.IMPORTANCE_HIGH
)

The notification is displayed after successful registration.

10. Logcat

Logcat is used to display Activity Lifecycle messages.

The application uses the following tag:

ActivityLifecycle

Example:

MainActivity - onCreate
MainActivity - onStart
MainActivity - onResume
Test Cases
Test Case 1 – Successful Registration
Input
Student Name: Rashmi Kumari
USN: 25MCAR0092
Email: rashmi@example.com
Gender: Female
Event Category: Technical
Event Rules: Agreed
Participation Certificate: ON
Expected Output

The Confirmation Activity displays:

Dear Rashmi Kumari,

Your registration for TechConnect 2026
has been successfully completed.

Event Category: Technical

The application also generates the notification:

TechConnect 2026

Registration was successful!
Result

Test Case Passed

Test Case 2 – Empty Student Name
Input
Student Name: Empty
USN: 25MCAR0092
Email: rashmi@example.com
Expected Output

The application displays an error message:

Enter student name

The registration does not proceed to the Confirmation Activity.

Result

Test Case Passed

Test Case 3 – Event Rules Not Accepted
Input
Student Name: Rashmi Kumari
USN: 25MCAR0092
Email: rashmi@example.com
Gender: Female
Event Category: Technical
Event Rules: Not Selected
Expected Output

The application displays:

Please agree to the event rules

The registration is not completed.

Result

Test Case Passed

Screenshots
1. Home Activity

The Home Activity displays:

College Logo
TechConnect 2026 title
Short description of the event
Register Now button

2. Registration Activity

The Registration Activity displays the registration form containing:

Student Name
USN
Email
Gender
Event Category
Event Rules
Participation Certificate
Submit Registration button

3. Confirmation Activity

The Confirmation Activity displays the successful registration message along with the student's name and selected event category.

4. Android Notification

The application generates a notification after successful registration.

5. Activity Lifecycle – Logcat

The Activity Lifecycle messages can be viewed in Android Studio Logcat using the tag:

ActivityLifecycle

Result

The Campus Event Registration – TechConnect 2026 Android application was successfully developed according to the given requirements.

The application successfully implements:

College logo
Application title – TechConnect 2026
Event description
Register Now button
Student registration form
EditText
RadioButton and RadioGroup
CheckBox
ToggleButton
Submit Registration button
Explicit Intent navigation
Data passing between Activities
Confirmation Activity
Android notification
Activity Lifecycle methods
Logcat lifecycle messages
Conclusion

The experiment successfully demonstrates the development of a complete Campus Event Registration Android application using Kotlin and XML.

The application provides practical understanding of:

Designing Android user interfaces using XML
Using basic Android Views
Collecting and validating user input
Handling Button click events
Using RadioButton and RadioGroup
Using CheckBox
Using ToggleButton
Navigating between Activities using Explicit Intent
Passing data using putExtra()
Retrieving data using getStringExtra()
Creating Android notifications
Implementing Activity Lifecycle methods
Monitoring Activity Lifecycle using Logcat

The developed TechConnect 2026 Campus Event Registration application successfully satisfies all the requirements specified in the given problem statement.
