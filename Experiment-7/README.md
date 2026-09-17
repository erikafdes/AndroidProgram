# Adaptive ListView App

## Experiment 7: Develop an Adaptive Android Application with ListView and ImageView

## Aim

To develop an adaptive Android application using **ListView and ImageView** to display a list of famous places along with their images, names, countries, and descriptions. The application also displays detailed information about a selected place on a separate screen.

---

## Objective

- To understand the use of **ListView** in Android.
- To display images using **ImageView**.
- To create a custom ListView item layout.
- To use a custom adapter for displaying data.
- To handle item click events.
- To use **Intent** for navigation between activities.
- To pass data from one Activity to another using `putExtra()`.
- To retrieve data using `getStringExtra()` and `getIntExtra()`.

---

## Technology Used

| Technology | Purpose |
|---|---|
| Kotlin | Application programming |
| XML | Designing user interfaces |
| Android Studio | Development environment |
| Android SDK | Android application development |
| ListView | Displaying a list of places |
| ImageView | Displaying place images |
| Intent | Navigation between activities and data transfer |
| BaseAdapter | Creating a custom ListView adapter |

---

## Features

- Displays a list of famous places from around the world.
- Each list item contains:
  - Place image
  - Place name
  - Country
  - Short description
- Uses a custom ListView layout.
- Clicking a place opens a separate detail screen.
- Detail screen displays:
  - Large image
  - Place name
  - Country
  - Detailed description
- Uses Intent to transfer selected place information.
- Scrollable detail screen using `ScrollView`.
- Simple and user-friendly interface.

---

## Places Included

The application contains the following famous places:

1. Eiffel Tower - France
2. Statue of Liberty - USA
3. Tokyo Tower - Japan
4. Colosseum - Italy
5. Taj Mahal - India
6. Big Ben - United Kingdom
7. Great Wall of China - China
8. Christ the Redeemer - Brazil

---

## Procedure

1. Create a new **Android Studio** project using **Kotlin** and **Empty Views Activity**.
2. Add images of famous places to the `res/drawable` folder.
3. Design `activity_main.xml` using a **TextView** and **ListView**.
4. Create `item_place.xml` to define the layout of each ListView item with an **ImageView** and **TextViews**.
5. Create `Place.kt` to store place name, country, description, and image.
6. Create `PlaceAdapter.kt` using `BaseAdapter` to display the places in the ListView.
7. Create `PlaceDetailActivity` with `activity_place_detail.xml` to display the selected place's image and description.
8. Use **Intent** and `putExtra()` to send the selected place data to the detail Activity.
9. Retrieve the data using `getStringExtra()` and `getIntExtra()` and display it on the detail screen.
10. Build and run the application, then test the ListView and detail screen functionality.

---

## Project Structure

```text
AdaptiveListViewApp/
│
├── app/
│   │
│   ├── src/
│   │   └── main/
│   │       │
│   │       ├── java/
│   │       │   └── com/
│   │       │       └── example/
│   │       │           └── adaptivelistviewapp/
│   │       │               ├── MainActivity.kt
│   │       │               ├── Place.kt
│   │       │               ├── PlaceAdapter.kt
│   │       │               └── PlaceDetailActivity.kt
│   │       │
│   │       ├── res/
│   │       │   │
│   │       │   ├── drawable/
│   │       │   │   ├── eiffel_tower.jpg
│   │       │   │   ├── statue_of_liberty.jpg
│   │       │   │   ├── tokyo_tower.jpg
│   │       │   │   ├── colosseum.jpg
│   │       │   │   ├── taj_mahal.jpg
│   │       │   │   ├── big_ben.jpg
│   │       │   │   ├── great_wall.jpg
│   │       │   │   └── christ_redeemer.jpg
│   │       │   │
│   │       │   ├── layout/
│   │       │   │   ├── activity_main.xml
│   │       │   │   ├── item_place.xml
│   │       │   │   └── activity_place_detail.xml
│   │       │   │
│   │       │   ├── mipmap/
│   │       │   │   └── app launcher icons
│   │       │   │
│   │       │   ├── values/
│   │       │   │   ├── colors.xml
│   │       │   │   ├── strings.xml
│   │       │   │   └── themes.xml
│   │       │   │
│   │       │   └── xml/
│   │       │       ├── backup_rules.xml
│   │       │       └── data_extraction_rules.xml
│   │       │
│   │       └── AndroidManifest.xml
│   │
│   ├── build.gradle.kts
│   └── proguard-rules.pro
│
├── gradle/
│   └── wrapper/
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
│
├── .gitignore
├── build.gradle.kts
├── gradle.properties
├── gradlew
├── gradlew.bat
├── settings.gradle.kts
└── README.md
```
---

## Code

### 1. MainActivity.kt

```kotlin
package com.example.adaptivelistviewapp

import android.content.Intent
import android.os.Bundle
import android.widget.ListView
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val listView = findViewById<ListView>(R.id.placeListView)

        val places = listOf(
            Place(
                "Eiffel Tower",
                "France",
                "The Eiffel Tower is one of the most recognizable landmarks in the world.",
                R.drawable.eiffel_tower
            ),
            Place(
                "Statue of Liberty",
                "USA",
                "The Statue of Liberty is a famous monument located in New York Harbor.",
                R.drawable.statue_of_liberty
            ),
            Place(
                "Tokyo Tower",
                "Japan",
                "Tokyo Tower is a famous communications and observation tower in Tokyo.",
                R.drawable.tokyo_tower
            ),
            Place(
                "Colosseum",
                "Italy",
                "The Colosseum is an ancient Roman amphitheatre located in Rome.",
                R.drawable.colosseum
            ),
            Place(
                "Taj Mahal",
                "India",
                "The Taj Mahal is a famous white marble monument located in Agra.",
                R.drawable.taj_mahal
            ),
            Place(
                "Big Ben",
                "United Kingdom",
                "Big Ben is a famous landmark located in London.",
                R.drawable.big_ben
            ),
            Place(
                "Great Wall of China",
                "China",
                "The Great Wall of China is a historic series of fortifications.",
                R.drawable.great_wall
            ),
            Place(
                "Christ the Redeemer",
                "Brazil",
                "Christ the Redeemer is a famous statue overlooking Rio de Janeiro.",
                R.drawable.christ_redeemer
            )
        )

        val adapter = PlaceAdapter(this, places)
        listView.adapter = adapter

        listView.setOnItemClickListener { _, _, position, _ ->

            val selectedPlace = places[position]

            val intent = Intent(
                this,
                PlaceDetailActivity::class.java
            )

            intent.putExtra("place_name", selectedPlace.name)
            intent.putExtra("place_country", selectedPlace.country)
            intent.putExtra("place_description", selectedPlace.description)
            intent.putExtra("place_image", selectedPlace.image)

            startActivity(intent)
        }
    }
}
```
### 2.Place.kt
```
package com.example.adaptivelistviewapp

data class Place(
    val name: String,
    val country: String,
    val description: String,
    val image: Int
)
```
### 3. PlaceAdapter.kt
```text
package com.example.adaptivelistviewapp

import android.content.Context
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.BaseAdapter
import android.widget.ImageView
import android.widget.TextView

class PlaceAdapter(
    private val context: Context,
    private val places: List<Place>
) : BaseAdapter() {

    override fun getCount(): Int {
        return places.size
    }

    override fun getItem(position: Int): Any {
        return places[position]
    }

    override fun getItemId(position: Int): Long {
        return position.toLong()
    }

    override fun getView(
        position: Int,
        convertView: View?,
        parent: ViewGroup?
    ): View {

        val view = convertView ?: LayoutInflater.from(context)
            .inflate(R.layout.item_place, parent, false)

        val imageView = view.findViewById<ImageView>(R.id.placeImage)
        val nameTextView = view.findViewById<TextView>(R.id.placeName)
        val descriptionTextView =
            view.findViewById<TextView>(R.id.placeDescription)

        val place = places[position]

        imageView.setImageResource(place.image)
        nameTextView.text = "${place.name} - ${place.country}"
        descriptionTextView.text = place.description

        return view
    }
}
```
### 4. PlaceDetailActivity.kt
```text
package com.example.adaptivelistviewapp

import android.os.Bundle
import android.widget.ImageView
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity

class PlaceDetailActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContentView(R.layout.activity_place_detail)

        val imageView = findViewById<ImageView>(R.id.detailImage)
        val nameTextView = findViewById<TextView>(R.id.detailName)
        val countryTextView = findViewById<TextView>(R.id.detailCountry)
        val descriptionTextView =
            findViewById<TextView>(R.id.detailDescription)

        val name = intent.getStringExtra("place_name")
        val country = intent.getStringExtra("place_country")
        val description = intent.getStringExtra("place_description")

        val image = intent.getIntExtra("place_image", 0)

        nameTextView.text = name
        countryTextView.text = country
        descriptionTextView.text = description

        if (image != 0) {
            imageView.setImageResource(image)
        }
    }
}
```
### 5. activity_main.xml
```text
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:padding="16dp"
        android:text="Famous Places Around the World"
        android:textSize="24sp"
        android:textStyle="bold" />

    <ListView
        android:id="@+id/placeListView"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"
        android:dividerHeight="1dp" />

</LinearLayout>
```

### 6. item_place.xml
```text
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:padding="12dp">

    <ImageView
        android:id="@+id/placeImage"
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:scaleType="centerCrop"
        android:contentDescription="Place Image" />

    <LinearLayout
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:orientation="vertical"
        android:layout_gravity="center_vertical"
        android:paddingStart="12dp">

        <TextView
            android:id="@+id/placeName"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Place Name"
            android:textSize="19sp"
            android:textStyle="bold" />

        <TextView
            android:id="@+id/placeDescription"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="6dp"
            android:text="Place Description"
            android:textSize="14sp" />

    </LinearLayout>

</LinearLayout>
```

### 7.activity_place_detail.xml
```text
<?xml version="1.0" encoding="utf-8"?>

<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="16dp">

        <ImageView
            android:id="@+id/detailImage"
            android:layout_width="match_parent"
            android:layout_height="250dp"
            android:scaleType="centerCrop"
            android:contentDescription="Place Image" />

        <TextView
            android:id="@+id/detailName"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="16dp"
            android:text="Place Name"
            android:textSize="28sp"
            android:textStyle="bold" />

        <TextView
            android:id="@+id/detailCountry"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="6dp"
            android:text="Country"
            android:textSize="18sp" />

        <TextView
            android:id="@+id/detailDescription"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="16dp"
            android:text="Description"
            android:textSize="17sp"
            android:lineSpacingExtra="6dp" />

    </LinearLayout>

</ScrollView>
```
---


## OUTPUT 
<img width="959" height="473" alt="Screenshot 2026-09-17 110132" src="https://github.com/user-attachments/assets/38e64110-cee6-4026-8016-f4f0904a1c37" />

<img width="959" height="473" alt="Screenshot 2026-09-17 110140" src="https://github.com/user-attachments/assets/dc01cabc-dd9a-4f66-86f8-23e8365699c4" />

## Result

The Android application was successfully developed using **ListView and ImageView**. It displays a list of famous places with their images, names, countries, and descriptions. On clicking a place, its detailed image and information are displayed on a separate screen.

## Conclusion

The application successfully demonstrates the use of **ListView, ImageView, BaseAdapter, Data Class, and Intent** in Android. It provides a simple and interactive way to display and view detailed information about different places.
