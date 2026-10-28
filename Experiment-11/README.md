# Google Maps Android Application

## Experiment 11: Integration of Google Maps in Android

This Android application demonstrates the integration of **Google Maps into an Android application using Kotlin**. It displays an interactive map with a custom marker at a specified location, camera positioning, zoom controls, and a compass. The application also supports edge-to-edge user interface handling for modern Android devices.

## Objectives

- To understand the integration of Google Maps in Android applications.
- To learn how to configure the Google Maps SDK for Android.
- To display an interactive map using `SupportMapFragment`.
- To add markers at specific geographical coordinates.
- To control map zoom and camera positioning.
- To enable map controls such as zoom buttons and compass.
- To understand the use of API keys and required permissions.

## Procedure

1. Create a new Android project in Android Studio using Kotlin.
2. Add the Google Play Services Maps dependency to the application-level Gradle file.
3. Create or select a project in the Google Cloud Console.
4. Enable the Maps SDK for Android and generate an API key.
5. Add the API key metadata to `AndroidManifest.xml`.
6. Configure the required permissions and application settings.
7. Design the user interface using `FragmentContainerView` to display the map.
8. Implement `OnMapReadyCallback` in `MainActivity.kt` to initialize the map.
9. Add a marker at the desired latitude and longitude.
10. Configure camera zoom, compass, and zoom controls.
11. Run the application on an Android emulator or physical device with Google Play Services.

## Features

* Displays an interactive Google Map.
* Uses `SupportMapFragment` to load the map.
* Places a custom marker at a predefined location, such as Sydney.
* Adjusts the camera position and zoom level.
* Enables built-in zoom controls and compass.
* Supports modern edge-to-edge window layout handling.
* Uses the Google Maps SDK for Android.
* Supports execution on compatible Android emulators and physical devices.

## Technologies Used

* **Language:** Kotlin
* **Platform:** Android
* **IDE:** Android Studio
* **UI:** XML
* **Maps SDK:** Google Maps SDK for Android
* **Google Services:** Google Play Services Maps
* **API Configuration:** Google Cloud Console
* **Version Control:** Git and GitHub

## Application Flow

```text
      Launch Application
             |
             v
       Load Main Activity
             |
             v
       Initialize Map
             |
             v
    Wait for Map to Be Ready
             |
             v
      Configure Google Map
             |
       +-----+------+
       |            |
       v            v
  Add Marker    Set Camera
       |            |
       v            v
  Show Location  Set Zoom Level
       |            |
       +-----+------+
             |
             v
    Display Interactive Map
```

## Google Maps Integration

The application uses `SupportMapFragment` to display Google Maps within the activity layout.

The `OnMapReadyCallback` interface is used to receive the Google Map instance after initialization. Once the map is ready, the application can add markers, change camera positioning, and enable map controls.

### MainActivity.kt — Core Implementation

The following example demonstrates the basic map initialization and marker configuration. Keep your existing edge-to-edge code if it is already implemented in your project.

```kotlin
package com.example.exp11

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import com.google.android.gms.maps.CameraUpdateFactory
import com.google.android.gms.maps.GoogleMap
import com.google.android.gms.maps.OnMapReadyCallback
import com.google.android.gms.maps.SupportMapFragment
import com.google.android.gms.maps.model.LatLng
import com.google.android.gms.maps.model.MarkerOptions

class MainActivity : AppCompatActivity(), OnMapReadyCallback {

    private lateinit var googleMap: GoogleMap

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val mapFragment = supportFragmentManager
            .findFragmentById(R.id.map) as SupportMapFragment

        mapFragment.getMapAsync(this)
    }

    override fun onMapReady(map: GoogleMap) {
        googleMap = map

        val sydney = LatLng(-33.8688, 151.2093)

        googleMap.addMarker(
            MarkerOptions()
                .position(sydney)
                .title("Sydney")
        )

        googleMap.moveCamera(
            CameraUpdateFactory.newLatLngZoom(sydney, 12f)
        )

        googleMap.uiSettings.isZoomControlsEnabled = true
        googleMap.uiSettings.isCompassEnabled = true
    }
}
```

**Note:** This is a basic example of the map functionality described above. Your actual package name, map fragment ID, and edge-to-edge implementation may differ.

## Project Structure

```text
EXP11-GoogleMaps-App/
│
├── app/
│   └── src/
│       └── main/
│           ├── java/
│           │   └── com/example/exp11/
│           │       └── MainActivity.kt
│           │
│           ├── res/
│           │   └── layout/
│           │       └── activity_main.xml
│           │
│           └── AndroidManifest.xml
│
├── images/
│   └── google-maps-screenshot.png
│
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

## Main Components

### MainActivity.kt

`MainActivity.kt` controls the map initialization and configuration.

It is responsible for:

* Initializing the map fragment.
* Implementing `OnMapReadyCallback`.
* Adding markers to geographical coordinates.
* Setting the camera position and zoom level.
* Enabling zoom controls and the compass.

### activity_main.xml

The XML layout contains the map fragment that displays Google Maps within the application.

### AndroidManifest.xml

The manifest configures the application and provides the API key metadata required to load Google Maps. It may also declare internet and location permissions, depending on the features implemented.

## Setup and Configuration

### 1. Configure the Google Maps API Key

1. Open the [Google Cloud Console](https://console.cloud.google.com/).
2. Create or select a Google Cloud project.
3. Enable **Maps SDK for Android**.
4. Navigate to **APIs & Services → Credentials**.
5. Create an API key.
6. Configure the key with appropriate restrictions, including Android application restrictions where applicable.

Add the following metadata inside the `<application>` element in `AndroidManifest.xml`:

```xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="YOUR_ACTUAL_API_KEY" />
```

Replace `YOUR_ACTUAL_API_KEY` with your own API key. Do not commit an unrestricted key or other secrets to a public repository.

### 2. Add the Maps Dependency

Add the Google Maps dependency to your app-level `build.gradle.kts` file. For example:

```kotlin
dependencies {
    implementation("com.google.android.gms:play-services-maps:19.2.0")
}
```

If your project already uses another compatible version, retain the version configured for your project.

### 3. Configure Permissions

The application generally requires internet access to load map tiles. Add this permission outside the `<application>` element in `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

Location permissions are only needed if the application accesses the device's current location. They are not required merely to display a map and a predefined marker.

## Building and Running

1. Open the project in Android Studio.
2. Synchronize the Gradle files.
3. Configure a valid Google Maps API key.
4. Verify that the Maps SDK for Android is enabled.
5. Run the application on a compatible emulator or Android device.
6. Confirm that the map loads and the marker appears at the specified location.
7. Test the zoom buttons, compass, and map interaction.

## Screenshots



## Result

The Google Maps Android application demonstrates the integration of the Google Maps SDK using Kotlin. The experiment covers map initialization, marker placement, camera positioning, built-in map controls, and API key configuration.
