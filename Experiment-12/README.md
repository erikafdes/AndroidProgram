 Android Application to Access Web Services Using HTTP Request

An Android application developed using **Kotlin** that demonstrates how to access web services using HTTP requests. The application sends a GET request to a web API, receives a JSON response, and displays the retrieved data on the screen.

---

## Aim

To develop an Android application using Kotlin to access web services by sending HTTP requests and displaying the response received from a server.

---

## Objectives

- To understand the concept of web services in Android.
- To learn how HTTP requests work.
- To implement GET requests using `HttpURLConnection`.
- To retrieve JSON data from a web API.
- To display server responses in an Android application.
- To handle network errors and responses.

---

## Features

- Sends HTTP GET requests to a web service.
- Retrieves JSON data from an online API.
- Displays the server response in the application.
- Uses background threads for network operations.
- Handles network errors and exceptions.
- Supports internet connectivity.

---

## Technologies Used

- **Language:** Kotlin
- **Platform:** Android
- **IDE:** Android Studio
- **UI:** XML
- **Networking:** HttpURLConnection
- **Data Format:** JSON
- **API:** JSONPlaceholder

---

## API Used

**JSONPlaceholder**

Test API endpoint:

`https://jsonplaceholder.typicode.com/posts/1`

The API returns sample post information in JSON format.

---

## Procedure

1. Create a new Android project in Android Studio using Kotlin.
2. Design the user interface using XML with a button to send an HTTP request and a TextView to display the response.
3. Add internet permission in `AndroidManifest.xml`.
4. Select a web service API endpoint that returns data in JSON format.
5. Implement the HTTP request using `HttpURLConnection`.
6. Execute the network request in a background thread to avoid blocking the main UI thread.
7. Read the server response and display the retrieved data in the application.
8. Handle network errors and unsuccessful HTTP responses.
9. Run the application on an emulator or physical Android device with internet access and verify the output.

---

## Internet Permission

Add the following permission in `AndroidManifest.xml`, outside the `<application>` tag:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

---

## Main Source Code

### MainActivity.kt

```kotlin
Thread {
    val url = java.net.URL(
        "https://jsonplaceholder.typicode.com/posts/1"
    )

    val connection = url.openConnection()
        as java.net.HttpURLConnection

    try {
        connection.requestMethod = "GET"

        val response = connection.inputStream
            .bufferedReader().use { it.readText() }

        runOnUiThread {
            textView.text = response
        }

    } catch (e: Exception) {
        runOnUiThread {
            textView.text = "Error: ${e.message}"
        }

    } finally {
        connection.disconnect()
    }
}.start()
```

---

## Application Flow

```text
    Launch Application
           |
           v
     Display Interface
           |
           v
     Click Request Button
           |
           v
      Send HTTP GET
           |
           v
       Web Server
           |
           v
    Receive JSON Response
           |
           v
     Display Response
           |
           v
       End Process
```

---

## Expected Output

The application sends a GET request to the JSONPlaceholder API and receives a JSON response similar to:

```json
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati",
  "body": "quia et suscipit..."
}
```

---
## Screenshot

<img width="529" height="1120" alt="pic1" src="https://github.com/user-attachments/assets/7e88b947-2c89-4f6e-970d-8814f9fcf876" />
<img width="526" height="1134" alt="pic2" src="https://github.com/user-attachments/assets/7bd5c6db-3b8f-4bbc-9f58-a9702d70c35a" />


## Result

The Android application successfully accesses a web service through an HTTP GET request, receives a JSON response from the server, and displays the retrieved data on the screen.

---
