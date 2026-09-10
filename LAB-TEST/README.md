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

```
---

##Output

<img width="720" height="1600" alt="WhatsApp Image 2026-09-10 at 2 34 39 PM" src="https://github.com/user-attachments/assets/0b644fb3-a8df-40a4-934b-feba8dfac205" />


<img width="720" height="1600" alt="WhatsApp Image 2026-09-10 at 2 34 39 PM (1)" src="https://github.com/user-attachments/assets/f1ea18de-9e83-46bd-ab14-1a94b300a9cc" />


<img width="720" height="1600" alt="WhatsApp Image 2026-09-10 at 2 34 38 PM (1)" src="https://github.com/user-attachments/assets/46fbfb34-4059-46e6-afe1-0f1d876edccb" />

---


## MainActivity.kt

```kotlin
package com.example.techconnect2026

import android.Manifest
import android.content.Intent
import android.content.pm.PackageManager
import android.os.Build
import android.os.Bundle
import android.util.Log
import android.widget.Button
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    private val TAG = "ActivityLifecycle"

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        Log.d(TAG, "MainActivity - onCreate")

        setContentView(R.layout.activity_main)

        // Request notification permission on Android 13 and above
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {

            if (
                checkSelfPermission(
                    Manifest.permission.POST_NOTIFICATIONS
                ) != PackageManager.PERMISSION_GRANTED
            ) {

                requestPermissions(
                    arrayOf(Manifest.permission.POST_NOTIFICATIONS),
                    100
                )
            }
        }

        // Register Now button
        val btnRegister =
            findViewById<Button>(R.id.btnRegister)

        btnRegister.setOnClickListener {

            Log.d(
                TAG,
                "Register Now button clicked"
            )

            // Explicit Intent
            val intent = Intent(
                this,
                RegistrationActivity::class.java
            )

            startActivity(intent)
        }
    }

    override fun onStart() {
        super.onStart()

        Log.d(
            TAG,
            "MainActivity - onStart"
        )
    }

    override fun onResume() {
        super.onResume()

        Log.d(
            TAG,
            "MainActivity - onResume"
        )
    }

    override fun onPause() {
        super.onPause()

        Log.d(
            TAG,
            "MainActivity - onPause"
        )
    }

    override fun onStop() {
        super.onStop()

        Log.d(
            TAG,
            "MainActivity - onStop"
        )
    }

    override fun onDestroy() {
        super.onDestroy()

        Log.d(
            TAG,
            "MainActivity - onDestroy"
        )
    }

    override fun onRequestPermissionsResult(
        requestCode: Int,
        permissions: Array<out String>,
        grantResults: IntArray
    ) {
        super.onRequestPermissionsResult(
            requestCode,
            permissions,
            grantResults
        )

        if (requestCode == 100) {

            if (
                grantResults.isNotEmpty() &&
                grantResults[0] == PackageManager.PERMISSION_GRANTED
            ) {

                Log.d(
                    TAG,
                    "Notification permission granted"
                )

            } else {

                Log.d(
                    TAG,
                    "Notification permission denied"
                )
            }
        }
    }
}
```

---

# 📄 activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp">

    <!-- College Logo -->

    <ImageView
        android:id="@+id/imgCollegeLogo"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:src="@drawable/college_logo"
        android:contentDescription="College Logo"
        android:scaleType="fitCenter"
        android:layout_marginBottom="20dp" />

    <!-- Application Title -->

    <TextView
        android:id="@+id/txtTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="TechConnect 2026"
        android:textSize="28sp"
        android:textStyle="bold"
        android:gravity="center"
        android:layout_marginBottom="16dp" />

    <!-- Short Description -->

    <TextView
        android:id="@+id/txtDescription"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="TechConnect 2026 is a technical event that provides students an opportunity to explore technology, innovation and new ideas."
        android:textSize="16sp"
        android:gravity="center"
        android:layout_marginBottom="30dp" />

    <!-- Register Now Button -->

    <Button
        android:id="@+id/btnRegister"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Register Now" />

</LinearLayout>
```

---

# 📄 AndroidManifest.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<manifest
    xmlns:android="http://schemas.android.com/apk/res/android">

    <!-- Notification permission for Android 13+ -->

    <uses-permission
        android:name="android.permission.POST_NOTIFICATIONS" />

    <application
        android:allowBackup="true"
        android:label="TechConnect 2026"
        android:supportsRtl="true"
        android:theme="@style/Theme.TechConnect2026">

        <!-- Confirmation Activity -->

        <activity
            android:name=".ConfirmationActivity"
            android:exported="false" />

        <!-- Registration Activity -->

        <activity
            android:name=".RegistrationActivity"
            android:exported="false" />

        <!-- Home Activity -->

        <activity
            android:name=".MainActivity"
            android:exported="true">

            <intent-filter>

                <action
                    android:name="android.intent.action.MAIN" />

                <category
                    android:name="android.intent.category.LAUNCHER" />

            </intent-filter>

        </activity>

    </application>

</manifest>
```

## RegistrationActivity.kt

```kotlin
package com.example.techconnect2026

import android.content.Intent
import android.os.Bundle
import android.util.Log
import android.widget.Button
import android.widget.CheckBox
import android.widget.EditText
import android.widget.RadioButton
import android.widget.RadioGroup
import android.widget.Toast
import android.widget.ToggleButton
import androidx.appcompat.app.AppCompatActivity

class RegistrationActivity : AppCompatActivity() {

    private val TAG = "ActivityLifecycle"

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        Log.d(
            TAG,
            "RegistrationActivity - onCreate"
        )

        setContentView(R.layout.activity_registration)

        // Student Name
        val studentName =
            findViewById<EditText>(
                R.id.etStudentName
            )

        // USN
        val usn =
            findViewById<EditText>(
                R.id.etUSN
            )

        // Email
        val email =
            findViewById<EditText>(
                R.id.etEmail
            )

        // Gender RadioGroup
        val genderGroup =
            findViewById<RadioGroup>(
                R.id.rgGender
            )

        // Event Category RadioGroup
        val categoryGroup =
            findViewById<RadioGroup>(
                R.id.rgCategory
            )

        // Event Rules CheckBox
        val rules =
            findViewById<CheckBox>(
                R.id.cbRules
            )

        // Certificate ToggleButton
        val certificate =
            findViewById<ToggleButton>(
                R.id.toggleCertificate
            )

        // Submit Button
        val submit =
            findViewById<Button>(
                R.id.btnSubmit
            )

        submit.setOnClickListener {

            // Get input values
            val name =
                studentName.text.toString().trim()

            val usnText =
                usn.text.toString().trim()

            val emailText =
                email.text.toString().trim()

            // Validate Student Name
            if (name.isEmpty()) {

                studentName.error =
                    "Enter student name"

                return@setOnClickListener
            }

            // Validate USN
            if (usnText.isEmpty()) {

                usn.error =
                    "Enter USN"

                return@setOnClickListener
            }

            // Validate Email
            if (emailText.isEmpty()) {

                email.error =
                    "Enter email"

                return@setOnClickListener
            }

            // Validate Gender
            if (
                genderGroup.checkedRadioButtonId == -1
            ) {

                Toast.makeText(
                    this,
                    "Please select gender",
                    Toast.LENGTH_SHORT
                ).show()

                return@setOnClickListener
            }

            // Validate Event Category
            if (
                categoryGroup.checkedRadioButtonId == -1
            ) {

                Toast.makeText(
                    this,
                    "Please select event category",
                    Toast.LENGTH_SHORT
                ).show()

                return@setOnClickListener
            }

            // Validate Event Rules
            if (!rules.isChecked) {

                Toast.makeText(
                    this,
                    "Please agree to the event rules",
                    Toast.LENGTH_SHORT
                ).show()

                return@setOnClickListener
            }

            // Get selected event category
            val selectedCategory =
                findViewById<RadioButton>(
                    categoryGroup.checkedRadioButtonId
                ).text.toString()

            // Get certificate status
            val certificateRequired =
                certificate.isChecked

            Log.d(
                TAG,
                "Registration submitted"
            )

            Log.d(
                TAG,
                "Student Name: $name"
            )

            Log.d(
                TAG,
                "Event Category: $selectedCategory"
            )

            Log.d(
                TAG,
                "Certificate Required: $certificateRequired"
            )

            // Intent to ConfirmationActivity
            val intent =
                Intent(
                    this,
                    ConfirmationActivity::class.java
                )

            // Pass student name
            intent.putExtra(
                "studentName",
                name
            )

            // Pass selected event category
            intent.putExtra(
                "category",
                selectedCategory
            )

            // Open Confirmation Activity
            startActivity(intent)
        }
    }

    override fun onStart() {
        super.onStart()

        Log.d(
            TAG,
            "RegistrationActivity - onStart"
        )
    }

    override fun onResume() {
        super.onResume()

        Log.d(
            TAG,
            "RegistrationActivity - onResume"
        )
    }

    override fun onPause() {
        super.onPause()

        Log.d(
            TAG,
            "RegistrationActivity - onPause"
        )
    }

    override fun onStop() {
        super.onStop()

        Log.d(
            TAG,
            "RegistrationActivity - onStop"
        )
    }

    override fun onDestroy() {
        super.onDestroy()

        Log.d(
            TAG,
            "RegistrationActivity - onDestroy"
        )
    }
}
```

---
## ConfirmationActivity.kt

```kotlin
package com.example.techconnect2026

import android.Manifest
import android.app.NotificationChannel
import android.app.NotificationManager
import android.content.pm.PackageManager
import android.os.Build
import android.os.Bundle
import android.util.Log
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity
import androidx.core.app.NotificationCompat
import androidx.core.app.NotificationManagerCompat

class ConfirmationActivity : AppCompatActivity() {

    private val TAG = "ActivityLifecycle"

    private val CHANNEL_ID =
        "techconnect_registration"

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        Log.d(
            TAG,
            "ConfirmationActivity - onCreate"
        )

        setContentView(
            R.layout.activity_confirmation
        )

        // Receive data from RegistrationActivity
        val name =
            intent.getStringExtra(
                "studentName"
            )

        val category =
            intent.getStringExtra(
                "category"
            )

        // Display confirmation
        val confirmation =
            findViewById<TextView>(
                R.id.txtConfirmation
            )

        confirmation.text =
            "Dear $name,\n\n" +
                    "Your registration for TechConnect 2026 " +
                    "has been successfully completed.\n\n" +
                    "Event Category: $category"

        // Create notification channel
        createNotificationChannel()

        // Generate notification
        showNotification()
    }

    private fun createNotificationChannel() {

        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {

            val channel = NotificationChannel(
                CHANNEL_ID,
                "TechConnect Registration",
                NotificationManager.IMPORTANCE_HIGH
            )

            channel.description =
                "Notifications for TechConnect 2026 registration"

            channel.enableVibration(true)

            val manager =
                getSystemService(NotificationManager::class.java)

            manager.createNotificationChannel(channel)
        }
    }

    private fun showNotification() {

        val notification =
            NotificationCompat.Builder(this, CHANNEL_ID)
                .setSmallIcon(android.R.drawable.ic_dialog_info)
                .setContentTitle("TechConnect 2026")
                .setContentText("Registration was successful!")
                .setPriority(NotificationCompat.PRIORITY_HIGH)
                .setDefaults(NotificationCompat.DEFAULT_ALL)
                .setAutoCancel(true)
                .build()

        if (
            Build.VERSION.SDK_INT < Build.VERSION_CODES.TIRAMISU ||
            checkSelfPermission(Manifest.permission.POST_NOTIFICATIONS)
            == PackageManager.PERMISSION_GRANTED
        ) {

            NotificationManagerCompat
                .from(this)
                .notify(1, notification)

            Log.d(
                TAG,
                "Notification sent successfully"
            )
        }
    }
    override fun onStart() {
        super.onStart()

        Log.d(
            TAG,
            "ConfirmationActivity - onStart"
        )
    }

    override fun onResume() {
        super.onResume()

        Log.d(
            TAG,
            "ConfirmationActivity - onResume"
        )
    }

    override fun onPause() {
        super.onPause()

        Log.d(
            TAG,
            "ConfirmationActivity - onPause"
        )
    }

    override fun onStop() {
        super.onStop()

        Log.d(
            TAG,
            "ConfirmationActivity - onStop"
        )
    }

    override fun onDestroy() {
        super.onDestroy()

        Log.d(
            TAG,
            "ConfirmationActivity - onDestroy"
        )
    }
}

---



---

