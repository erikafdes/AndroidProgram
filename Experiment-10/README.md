# Data Sharing Android Application

## Experiment 10: Data Sharing Using Contacts Content Provider

This Android application demonstrates **data sharing using the Contacts Content Provider**. The application allows users to retrieve contact names and phone numbers stored on the device after granting runtime permission. It also provides an option to open the system contact-creation screen with the entered name and phone number.

## Objectives

- To understand the concept of Android Content Providers.
- To learn how to access contact information using `ContactsContract`.
- To understand the use of `ContentResolver` for retrieving data.
- To implement runtime permissions for accessing device contacts.
- To learn how to use implicit intents to open system applications.
- To display retrieved contact details in an Android application.

## Procedure

1. Create a new Android project in Android Studio using Kotlin.
2. Design the application interface using XML with fields for entering a contact name and phone number.
3. Add buttons to fetch existing contacts and initiate contact creation.
4. Declare the `READ_CONTACTS` permission in `AndroidManifest.xml`.
5. Implement runtime permission handling in `MainActivity.kt`.
6. Use `ContactsContract.CommonDataKinds.Phone.CONTENT_URI` to access phone contact information.
7. Retrieve contact names and phone numbers using `ContentResolver` and display the results.
8. Implement an implicit intent to open the system contact-creation screen.
9. Run the application on an Android device or emulator and test the contact retrieval and creation features.

## Features

* Displays student identification details.
* Retrieves contact names and phone numbers from the device.
* Requests permission before accessing contacts.
* Displays contacts in alphabetical order.
* Opens the system contact-creation screen with pre-filled information.
* Displays a message when the contact list is empty.
* Handles denied permissions and empty input fields.
* Uses the device's existing contacts database without requiring an internet connection.

## Technologies Used

* **Language:** Kotlin
* **Platform:** Android
* **IDE:** Android Studio
* **UI:** XML
* **Data Source:** Android Contacts Content Provider
* **Data Access:** `ContentResolver`
* **Permission:** `READ_CONTACTS`
* **Communication:** Implicit Intent

## Application Flow

```text
      Open Application
             |
             v
       Contact Interface
             |
       +-----+------+
       |            |
       v            v
 Fetch Contacts   Add Contact
       |            |
       v            v
 Check Permission  Enter Name
       |            |
       v            v
 Read Contacts    Enter Phone
       |            |
       v            v
 ContentResolver  Create Intent
       |            |
       v            v
 Display Results  Open Contacts App
```

## Contacts Content Provider

The Contacts Content Provider allows Android applications to access contact information through a standard interface.

The application uses `ContactsContract.CommonDataKinds.Phone.CONTENT_URI` to access phone-related contact records.

The following fields are retrieved:

* `DISPLAY_NAME` — The name associated with a contact.
* `NUMBER` — The phone number associated with a contact.

## ContentResolver

`ContentResolver` is used to execute a query against the Contacts Content Provider.

```kotlin
val uri = ContactsContract.CommonDataKinds.Phone.CONTENT_URI

val projection = arrayOf(
    ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME,
    ContactsContract.CommonDataKinds.Phone.NUMBER
)

val cursor = contentResolver.query(
    uri,
    projection,
    null,
    null,
    "${ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME} ASC"
)
```

The query retrieves the contact name and phone number columns and sorts the results alphabetically by display name.

## Runtime Permission

Android requires permission before an application can read the user's contacts.

Add the following permission above the `<application>` tag in `AndroidManifest.xml`.

```xml
<uses-permission android:name="android.permission.READ_CONTACTS" />
```

The application checks whether permission has already been granted. If permission has not been granted, it requests access from the user before retrieving contacts.

## Project Structure

```text
ContactsProviderApp/
│
├── app/
│   └── src/
│       └── main/
│           ├── java/
│           │   └── com/example/contactsproviderapp/
│           │       └── MainActivity.kt
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

`MainActivity.kt` manages the application's main interface and implements the following operations:

* Reads the contact name and phone number entered by the user.
* Checks and requests contact-reading permission.
* Retrieves contact details using `ContentResolver`.
* Displays the retrieved contacts using a `TextView`.
* Opens the contact-creation screen using an implicit intent.
* Displays toast messages for success, missing input, and permission denial.

### activity_main.xml

The XML layout defines the user interface, including:

* Student identification information.
* Contact name input field.
* Phone number input field.
* Add Contact button.
* Fetch Contacts button.
* Contact display area.

### AndroidManifest.xml

The manifest declares the application's contact-reading permission and contains the application configuration.

## Main Source Code

### MainActivity.kt

```kotlin
package com.example.contactsproviderapp

import android.Manifest
import android.content.Intent
import android.content.pm.PackageManager
import android.database.Cursor
import android.os.Bundle
import android.provider.ContactsContract
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.app.ActivityCompat
import androidx.core.content.ContextCompat

class MainActivity : AppCompatActivity() {

    private val permissionReqCode = 101

    private lateinit var tvContactList: TextView
    private lateinit var etContactName: EditText
    private lateinit var etContactPhone: EditText

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val tvStudentUSN = findViewById<TextView>(R.id.tvStudentUSN)
        tvStudentUSN.text = "USN: 25MCAR0121"

        etContactName = findViewById(R.id.etContactName)
        etContactPhone = findViewById(R.id.etContactPhone)
        tvContactList = findViewById(R.id.tvContactList)

        val btnAddContact = findViewById<Button>(R.id.btnAddContact)
        val btnFetchContacts = findViewById<Button>(R.id.btnFetchContacts)

        btnAddContact.setOnClickListener {
            val name = etContactName.text.toString().trim()
            val phone = etContactPhone.text.toString().trim()

            if (name.isNotEmpty() && phone.isNotEmpty()) {
                val intent =
                    Intent(ContactsContract.Intents.Insert.ACTION).apply {
                        type = ContactsContract.RawContacts.CONTENT_TYPE
                        putExtra(
                            ContactsContract.Intents.Insert.NAME,
                            name
                        )
                        putExtra(
                            ContactsContract.Intents.Insert.PHONE,
                            phone
                        )
                    }

                startActivity(intent)
            } else {
                Toast.makeText(
                    this,
                    "Enter both name and phone number",
                    Toast.LENGTH_SHORT
                ).show()
            }
        }

        btnFetchContacts.setOnClickListener {
            if (checkPermission()) {
                fetchContacts()
            } else {
                requestPermission()
            }
        }
    }

    private fun checkPermission(): Boolean {
        return ContextCompat.checkSelfPermission(
            this,
            Manifest.permission.READ_CONTACTS
        ) == PackageManager.PERMISSION_GRANTED
    }

    private fun requestPermission() {
        ActivityCompat.requestPermissions(
            this,
            arrayOf(Manifest.permission.READ_CONTACTS),
            permissionReqCode
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

        if (requestCode == permissionReqCode) {
            if (
                grantResults.isNotEmpty() &&
                grantResults[0] == PackageManager.PERMISSION_GRANTED
            ) {
                Toast.makeText(
                    this,
                    "Permission Granted",
                    Toast.LENGTH_SHORT
                ).show()

                fetchContacts()
            } else {
                Toast.makeText(
                    this,
                    "Permission denied to read contacts",
                    Toast.LENGTH_SHORT
                ).show()
            }
        }
    }

    private fun fetchContacts() {
        val uri = ContactsContract.CommonDataKinds.Phone.CONTENT_URI

        val projection = arrayOf(
            ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME,
            ContactsContract.CommonDataKinds.Phone.NUMBER
        )

        val cursor: Cursor? = contentResolver.query(
            uri,
            projection,
            null,
            null,
            "${ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME} ASC"
        )

        if (cursor != null && cursor.count > 0) {
            val builder = StringBuilder()

            val nameIndex = cursor.getColumnIndexOrThrow(
                ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME
            )

            val numberIndex = cursor.getColumnIndexOrThrow(
                ContactsContract.CommonDataKinds.Phone.NUMBER
            )

            var count = 1

            while (cursor.moveToNext()) {
                val name = cursor.getString(nameIndex)
                val number = cursor.getString(numberIndex)

                builder.append(
                    "$count. $name\nPhone: $number\n\n"
                )

                count++
            }

            cursor.close()
            tvContactList.text = builder.toString()

            Toast.makeText(
                this,
                "Fetched ${count - 1} contacts successfully",
                Toast.LENGTH_SHORT
            ).show()
        } else {
            cursor?.close()
            tvContactList.text =
                "No contacts found in device phonebook."

            Toast.makeText(
                this,
                "Contacts list is empty",
                Toast.LENGTH_SHORT
            ).show()
        }
    }
}
```

## Screenshots
<img width="394" height="728" alt="image" src="https://github.com/user-attachments/assets/f75bbb0e-7543-4a9b-b7d7-b92af444763e" />

<img width="410" height="740" alt="image" src="https://github.com/user-attachments/assets/bda8956f-6206-40c4-83d5-d797b1de5a3d" />


## Result

The Android application demonstrates data sharing through the Contacts Content Provider. Contact information is retrieved using `ContentResolver` after runtime permission is granted, and new contact details are passed to the system Contacts application through an implicit intent.

