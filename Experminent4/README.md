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


https://github.com/user-attachments/assets/a261c54e-c0c4-466d-a3ad-4bb201ce7075



#  Source Code

---

##  MainActivity.kt

```kotlin
package com.example.loginintentapp

import android.content.Intent
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val username = findViewById<EditText>(R.id.etUsername)
        val password = findViewById<EditText>(R.id.etPassword)
        val login = findViewById<Button>(R.id.btnLogin)

        login.setOnClickListener {

            val user = username.text.toString()
            val pass = password.text.toString()

            if (user == "admin" && pass == "1234") {

                val intent = Intent(this, DashboardActivity::class.java)
                intent.putExtra("username", user)
                startActivity(intent)

            } else {

                Toast.makeText(
                    this,
                    "Invalid Username or Password",
                    Toast.LENGTH_SHORT
                ).show()
            }
        }
    }
}
```

---

## 📄 DashboardActivity.kt

```kotlin
package com.example.loginintentapp

import android.content.Intent
import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity

class DashboardActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_dashboard)

        val username = intent.getStringExtra("username")

        val tv = findViewById<TextView>(R.id.tvWelcome)
        tv.text = "Welcome, $username!"

        val logout = findViewById<Button>(R.id.btnLogout)

        logout.setOnClickListener {
            startActivity(Intent(this, MainActivity::class.java))
            finish()
        }
    }
}
```

---

## 📄 activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/background_gradient">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:gravity="center_horizontal"
        android:orientation="vertical"
        android:padding="30dp">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Login"
            android:textColor="#FFFFFF"
            android:textStyle="bold"
            android:textSize="34sp"/>

        <Space
            android:layout_width="match_parent"
            android:layout_height="40dp"/>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="55dp"
            android:background="@drawable/edittext_background"
            android:gravity="center_vertical"
            android:orientation="horizontal"
            android:paddingHorizontal="15dp">

            <ImageView
                android:layout_width="22dp"
                android:layout_height="22dp"
                android:src="@drawable/ic_person"
                android:tint="#A0A0A0"/>

            <EditText
                android:id="@+id/etUsername"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:background="@android:color/transparent"
                android:hint="Username"
                android:paddingStart="10dp"/>
        </LinearLayout>

        <Space
            android:layout_width="match_parent"
            android:layout_height="18dp"/>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="55dp"
            android:background="@drawable/edittext_background"
            android:gravity="center_vertical"
            android:orientation="horizontal"
            android:paddingHorizontal="15dp">

            <ImageView
                android:layout_width="22dp"
                android:layout_height="22dp"
                android:src="@drawable/ic_lock"
                android:tint="#A0A0A0"/>

            <EditText
                android:id="@+id/etPassword"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:background="@android:color/transparent"
                android:hint="Password"
                android:inputType="textPassword"
                android:paddingStart="10dp"/>
        </LinearLayout>

        <Space
            android:layout_width="match_parent"
            android:layout_height="30dp"/>

        <Button
            android:id="@+id/btnLogin"
            android:layout_width="match_parent"
            android:layout_height="55dp"
            android:background="@drawable/button_background"
            android:text="Login"
            android:textAllCaps="false"
            android:textColor="#FFFFFF"
            android:textSize="16sp"
            android:textStyle="bold"/>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="20dp"
            android:text="Forgot your password?"
            android:textColor="#FFFFFF"
            android:textSize="14sp"/>

    </LinearLayout>

</RelativeLayout>
```

---

## 📄 activity_dashboard.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/background_gradient">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:gravity="center_horizontal"
        android:orientation="vertical"
        android:padding="30dp">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Dashboard"
            android:textColor="#FFFFFF"
            android:textStyle="bold"
            android:textSize="34sp"/>

        <ImageView
            android:layout_width="95dp"
            android:layout_height="95dp"
            android:layout_marginTop="30dp"
            android:src="@drawable/ic_person"
            android:tint="#FFFFFF"/>

        <TextView
            android:id="@+id/tvWelcome"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="20dp"
            android:text="Welcome"
            android:textColor="#FFFFFF"
            android:textStyle="bold"
            android:textSize="24sp"/>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Glad to see you again"
            android:textColor="#F5F5F5"
            android:textSize="15sp"
            android:layout_marginBottom="30dp"/>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="70dp"
            android:background="@drawable/edittext_background"
            android:gravity="center"
            android:orientation="vertical">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Login Successful ✔"
                android:textColor="#5A66F0"
                android:textStyle="bold"
                android:textSize="18sp"/>

        </LinearLayout>

        <Button
            android:id="@+id/btnLogout"
            android:layout_width="match_parent"
            android:layout_height="55dp"
            android:layout_marginTop="35dp"
            android:background="@drawable/button_background"
            android:text="Logout"
            android:textAllCaps="false"
            android:textColor="#FFFFFF"
            android:textSize="16sp"
            android:textStyle="bold"/>

    </LinearLayout>

</RelativeLayout>
```

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

