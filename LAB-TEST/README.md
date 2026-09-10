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

