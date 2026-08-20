# Notification App

> **Experiment 5 – Create an Android Application to Display Notifications**

---

## Aim

To develop an Android application that demonstrates how to **create and display notifications** using the Android Notification API. The application generates notifications for different college-related activities such as assignments, examinations, and college events.

---

## Objective

* Develop an Android application to display notifications.
* Create and configure a Notification Channel.
* Request notification permission for Android 13 and above.
* Display notifications using `NotificationCompat`.
* Demonstrate heads-up notification behavior.
* Display notifications in the Android notification panel.
* Handle button click events.
* Test different notification scenarios.

---

## Technology Used

* **Programming Language:** Kotlin
* **IDE:** Android Studio
* **UI Design:** XML
* **Android SDK:** API 37
* **Build Tool:** Gradle (Kotlin DSL)
* **Version Control:** Git & GitHub

---

## Concepts Used

* Android Notifications
* Notification Channel
* NotificationManager
* NotificationManagerCompat
* NotificationCompat
* `POST_NOTIFICATIONS` Permission
* Runtime Permission
* Notification Importance
* Notification Priority
* Button Click Events
* Event Handling
* XML Layout
* Kotlin
* Android Activity

---

# Project Structure

```text
NotificationApp
│
├── app
│   ├── manifests
│   │      └── AndroidManifest.xml
│   │
│   ├── java
│   │      └── com.example.notificationapp
│   │              └── MainActivity.kt
│   │
│   └── res
│       ├── drawable
│       │
│       ├── layout
│       │      └── activity_main.xml
│       │
│       ├── mipmap
│       │
│       ├── values
│       │
│       └── xml
│
├── gradle
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

---

# Working

1. Launch the application.
2. The **College Notification System** screen is displayed.
3. The application requests notification permission on Android 13 and above.
4. Allow notification permission.
5. The application creates a Notification Channel.
6. Three notification buttons are displayed.
7. Click **Assignment Notification** to generate an assignment notification.
8. Click **Exam Notification** to generate an examination reminder.
9. Click **Event Notification** to generate a college event notification.
10. The notification appears as a heads-up popup when supported by the device settings.
11. The notification also remains available in the Android notification panel.

---

# Notification Scenarios

## Assignment Notification

When the user clicks the **Assignment Notification** button, the application displays:

**New Assignment**

> Your Android assignment is due tomorrow.

---

## Exam Notification

When the user clicks the **Exam Notification** button, the application displays:

**Exam Reminder**

> Your Software Engineering exam is scheduled tomorrow.

---

## Event Notification

When the user clicks the **Event Notification** button, the application displays:

**College Event**

> College technical event starts at 10:00 AM.

---

# Notification Permission

Android 13 and above requires applications to request permission before displaying notifications.

The following permission is added to `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.POST_NOTIFICATIONS" />
```

The application requests this permission at runtime before displaying notifications.

---

# Notification Channel

Android 8.0 and above requires notifications to be associated with a notification channel.

The application creates a channel named:

**College Notifications**

The channel is created with high importance:

```kotlin
val channel = NotificationChannel(
    channelId,
    "College Notifications",
    NotificationManager.IMPORTANCE_HIGH
)
```

High importance allows the notification to appear as a heads-up notification when the device's notification settings permit it.

---

# Output


```


https://github.com/user-attachments/assets/afbbd8e4-98a7-4462-97e9-d74479a33d60



```

---


# 📄 MainActivity.kt

```kotlin
package com.example.notificationapp

import android.Manifest
import android.app.NotificationChannel
import android.app.NotificationManager
import android.content.pm.PackageManager
import android.os.Build
import android.os.Bundle
import android.widget.Button
import androidx.appcompat.app.AppCompatActivity
import androidx.core.app.ActivityCompat
import androidx.core.app.NotificationCompat
import androidx.core.app.NotificationManagerCompat

class MainActivity : AppCompatActivity() {

    private val channelId = "college_notifications_v2"

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContentView(R.layout.activity_main)

        createNotificationChannel()

        requestNotificationPermission()

        val assignmentButton =
            findViewById<Button>(R.id.btnAssignment)

        assignmentButton.setOnClickListener {

            showNotification(
                "New Assignment",
                "Your Android assignment is due tomorrow."
            )
        }

        val examButton =
            findViewById<Button>(R.id.btnExam)

        examButton.setOnClickListener {

            showNotification(
                "Exam Reminder",
                "Your Software Engineering exam is scheduled tomorrow."
            )
        }

        val eventButton =
            findViewById<Button>(R.id.btnEvent)

        eventButton.setOnClickListener {

            showNotification(
                "College Event",
                "College technical event starts at 10:00 AM."
            )
        }
    }

    private fun requestNotificationPermission() {

        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {

            if (checkSelfPermission(
                    Manifest.permission.POST_NOTIFICATIONS
                ) != PackageManager.PERMISSION_GRANTED
            ) {

                ActivityCompat.requestPermissions(
                    this,
                    arrayOf(
                        Manifest.permission.POST_NOTIFICATIONS
                    ),
                    100
                )
            }
        }
    }

    private fun createNotificationChannel() {

        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {

            val channel = NotificationChannel(
                channelId,
                "College Notifications",
                NotificationManager.IMPORTANCE_HIGH
            )

            channel.description =
                "Notifications related to college activities"

            channel.enableVibration(true)

            val notificationManager =
                getSystemService(NotificationManager::class.java)

            notificationManager.createNotificationChannel(channel)
        }
    }

    private fun showNotification(
        title: String,
        message: String
    ) {

        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {

            if (checkSelfPermission(
                    Manifest.permission.POST_NOTIFICATIONS
                ) != PackageManager.PERMISSION_GRANTED
            ) {
                return
            }
        }

        val notification =
            NotificationCompat.Builder(
                this,
                channelId
            )
                .setSmallIcon(
                    android.R.drawable.ic_dialog_info
                )
                .setContentTitle(title)
                .setContentText(message)
                .setPriority(
                    NotificationCompat.PRIORITY_HIGH
                )
                .setAutoCancel(true)
                .setVibrate(
                    longArrayOf(0, 500, 200, 500)
                )
                .build()

        NotificationManagerCompat
            .from(this)
            .notify(
                System.currentTimeMillis().toInt(),
                notification
            )
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

    <TextView
        android:id="@+id/titleText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="College Notification System"
        android:textSize="24sp"
        android:textStyle="bold"
        android:gravity="center"
        android:layout_marginBottom="20dp" />

    <TextView
        android:id="@+id/studentInfo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Name: Erika Fernandes&#10;USN: 25MCAR0092"
        android:textSize="17sp"
        android:gravity="center"
        android:layout_marginBottom="30dp" />

    <Button
        android:id="@+id/btnAssignment"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Assignment Notification"
        android:layout_marginBottom="15dp" />

    <Button
        android:id="@+id/btnExam"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Exam Notification"
        android:layout_marginBottom="15dp" />

    <Button
        android:id="@+id/btnEvent"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Event Notification" />

</LinearLayout>
```

---

# 📄 AndroidManifest.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<manifest
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission
        android:name="android.permission.POST_NOTIFICATIONS" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.NotificationApp">

        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:windowSoftInputMode="adjustResize">

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

---

# Features

* Simple and user-friendly interface
* Assignment notification
* Examination reminder notification
* College event notification
* Notification permission handling
* Notification Channel implementation
* High-importance notifications
* Heads-up notification support
* Notification panel support
* Kotlin-based Android implementation
* XML-based user interface

---

# Result

The Android application was successfully developed to demonstrate **displaying notifications using the Android Notification API**.

The application successfully creates a notification channel, requests notification permission, and displays notifications for assignments, examinations, and college events. The notifications can be displayed as heads-up notifications and can also be viewed from the Android notification panel.

---

# Conclusion

This experiment demonstrates the implementation of Android notifications using **Kotlin and Android Notification APIs**. It provides a practical understanding of notification channels, notification permissions, notification priority, and notification management.

The **College Notification System** scenario demonstrates how Android notifications can be used in real-world applications to inform students about assignments, examinations, and college events.

---



