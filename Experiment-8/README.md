# Menus and WebView App

## Experiment 8: Implement Menus and WebView in an Android Application

## Aim

To implement **Options Menu, Popup Menu, GridView, Fragments, and WebView** in an Android application and demonstrate loading images and a webpage within the application.

---

## Objective

* To understand the use of **Options Menu** in Android.
* To implement a **Popup Menu**.
* To display images using **GridView**.
* To create and use **Fragments**.
* To understand the use of **WebView**.
* To load a local HTML file using WebView.
* To load images from drawable resources.
* To handle menu item click events.
* To navigate between different fragments.
* To understand basic webpage rendering inside an Android application.

---

## Technology Used

| Technology     | Purpose                                        |
| -------------- | ---------------------------------------------- |
| Kotlin         | Application programming                        |
| XML            | Designing user interfaces                      |
| Android Studio | Development environment                        |
| Android SDK    | Android application development                |
| Fragment       | Dividing the application into separate screens |
| GridView       | Displaying images in a grid                    |
| ImageView      | Displaying images                              |
| WebView        | Displaying webpage content                     |
| Options Menu   | Providing application-level actions            |
| Popup Menu     | Displaying contextual actions                  |
| HTML           | Creating the local webpage                     |

---

## Features

* Displays images in a **GridView**.
* Uses two fragments:

  * Image Grid Fragment
  * WebView Fragment
* Images are loaded from the `drawable` folder.
* Clicking an image displays a **Popup Menu**.
* Popup Menu contains:

  * Edit
  * Share
  * Delete
* Options Menu contains:

  * Select All
  * Edit
  * Share
* Displays a webpage using **WebView**.
* Uses a local HTML file so that the WebView can work without an internet connection.
* The WebView displays the student's **name and USN**.
* Provides a simple interface to switch between Images and WebView.

---

## Scenario

The application demonstrates an Android application containing two different sections. The first section displays a collection of images using a GridView. The second section displays a webpage using WebView.

The application also demonstrates the use of Options Menu and Popup Menu for performing different actions.

---

## Procedure

1. Create a new **Android Studio** project using **Kotlin** and **Empty Views Activity**.
2. Create two Fragments named `ImageGridFragment` and `WebViewFragment`.
3. Design the Image Grid Fragment using a **GridView**.
4. Add images to the `res/drawable` folder.
5. Create a custom image item layout for displaying images in the GridView.
6. Create an adapter to display the images.
7. Implement a **Popup Menu** containing Edit, Share, and Delete options.
8. Create an **Options Menu** containing Select All, Edit, and Share options.
9. Create a `raw` resource directory and add a `dummy.html` file.
10. Design the WebView Fragment using the **WebView** component.
11. Load the local HTML file into the WebView.
12. Add buttons in the main Activity to switch between the Image Grid Fragment and WebView Fragment.
13. Build and run the application on an Android emulator.
14. Test the GridView, Options Menu, Popup Menu, and WebView functionality.
15. Capture screenshots of the output and test cases for GitHub submission.

---

## Project Structure

```text
Experiment8/
│
├── app/
│   │
│   ├── src/
│   │   └── main/
│   │       │
│   │       ├── java/
│   │       │   └── com/
│   │       │       └── example/
│   │       │           └── experiment8/
│   │       │               ├── MainActivity.kt
│   │       │               ├── ImageGridFragment.kt
│   │       │               └── WebViewFragment.kt
│   │       │
│   │       ├── res/
│   │       │   │
│   │       │   ├── drawable/
│   │       │   │   ├── image1.jpg
│   │       │   │   ├── image2.jpg
│   │       │   │   ├── image3.jpg
│   │       │   │   └── image4.jpg
│   │       │   │
│   │       │   ├── layout/
│   │       │   │   ├── activity_main.xml
│   │       │   │   ├── fragment_image_grid.xml
│   │       │   │   ├── fragment_webview.xml
│   │       │   │   └── item_image.xml
│   │       │   │
│   │       │   ├── menu/
│   │       │   │   └── main_menu.xml
│   │       │   │
│   │       │   ├── raw/
│   │       │   │   └── dummy.html
│   │       │   │
│   │       │   └── values/
│   │       │       ├── colors.xml
│   │       │       ├── strings.xml
│   │       │       └── themes.xml
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

# Code

## 1. MainActivity.kt

```kotlin
package com.example.experiment8

import android.os.Bundle
import android.view.Menu
import android.view.MenuItem
import android.widget.Button
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContentView(R.layout.activity_main)

        val btnImages = findViewById<Button>(R.id.btnImages)
        val btnWeb = findViewById<Button>(R.id.btnWeb)

        if (savedInstanceState == null) {
            supportFragmentManager.beginTransaction()
                .replace(
                    R.id.fragmentContainer,
                    ImageGridFragment()
                )
                .commit()
        }

        btnImages.setOnClickListener {
            supportFragmentManager.beginTransaction()
                .replace(
                    R.id.fragmentContainer,
                    ImageGridFragment()
                )
                .commit()
        }

        btnWeb.setOnClickListener {
            supportFragmentManager.beginTransaction()
                .replace(
                    R.id.fragmentContainer,
                    WebViewFragment()
                )
                .commit()
        }
    }

    override fun onCreateOptionsMenu(menu: Menu): Boolean {
        menuInflater.inflate(R.menu.main_menu, menu)
        return true
    }

    override fun onOptionsItemSelected(item: MenuItem): Boolean {

        return when (item.itemId) {

            R.id.action_select_all -> {
                Toast.makeText(
                    this,
                    "Select All clicked",
                    Toast.LENGTH_SHORT
                ).show()
                true
            }

            R.id.action_edit -> {
                Toast.makeText(
                    this,
                    "Edit clicked",
                    Toast.LENGTH_SHORT
                ).show()
                true
            }

            R.id.action_share -> {
                Toast.makeText(
                    this,
                    "Share clicked",
                    Toast.LENGTH_SHORT
                ).show()
                true
            }

            else -> super.onOptionsItemSelected(item)
        }
    }
}
```

---

## 2. ImageGridFragment.kt

```kotlin
package com.example.experiment8

import android.os.Bundle
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.BaseAdapter
import android.widget.GridView
import android.widget.ImageView
import android.widget.PopupMenu
import android.widget.Toast
import androidx.fragment.app.Fragment

class ImageGridFragment : Fragment(R.layout.fragment_image_grid) {

    override fun onViewCreated(
        view: View,
        savedInstanceState: Bundle?
    ) {
        super.onViewCreated(view, savedInstanceState)

        val gridView = view.findViewById<GridView>(R.id.gridView)

        val images = listOf(
            R.drawable.image1,
            R.drawable.image2,
            R.drawable.image3,
            R.drawable.image4
        )

        val adapter = object : BaseAdapter() {

            override fun getCount(): Int {
                return images.size
            }

            override fun getItem(position: Int): Any {
                return images[position]
            }

            override fun getItemId(position: Int): Long {
                return position.toLong()
            }

            override fun getView(
                position: Int,
                convertView: View?,
                parent: ViewGroup?
            ): View {

                val imageView = if (convertView == null) {

                    LayoutInflater.from(requireContext())
                        .inflate(
                            R.layout.item_image,
                            parent,
                            false
                        ) as ImageView

                } else {
                    convertView as ImageView
                }

                imageView.setImageResource(images[position])

                return imageView
            }
        }

        gridView.adapter = adapter

        gridView.setOnItemClickListener { _, selectedView, _, _ ->

            val popup = PopupMenu(
                requireContext(),
                selectedView
            )

            popup.menu.add("Edit")
            popup.menu.add("Share")
            popup.menu.add("Delete")

            popup.setOnMenuItemClickListener { item ->

                Toast.makeText(
                    requireContext(),
                    "${item.title} clicked",
                    Toast.LENGTH_SHORT
                ).show()

                true
            }

            popup.show()
        }
    }
}
```

---

## 3. WebViewFragment.kt

```kotlin
package com.example.experiment8

import android.os.Bundle
import android.view.View
import android.webkit.WebView
import androidx.fragment.app.Fragment

class WebViewFragment : Fragment(R.layout.fragment_webview) {

    override fun onViewCreated(
        view: View,
        savedInstanceState: Bundle?
    ) {
        super.onViewCreated(view, savedInstanceState)

        val webView = view.findViewById<WebView>(R.id.webView)

        webView.settings.javaScriptEnabled = true

        webView.loadUrl(
            "file:///android_res/raw/dummy.html"
        )
    }
}
```

---

# 4. activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:padding="16dp"
        android:text="Experiment 8 - Menus and WebView"
        android:textSize="22sp"
        android:textStyle="bold" />

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btnImages"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="Images" />

        <Button
            android:id="@+id/btnWeb"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="WebView" />

    </LinearLayout>

    <FrameLayout
        android:id="@+id/fragmentContainer"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1" />

</LinearLayout>
```

---

# 5. fragment_image_grid.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<FrameLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <GridView
        android:id="@+id/gridView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:numColumns="2"
        android:horizontalSpacing="8dp"
        android:verticalSpacing="8dp"
        android:padding="8dp" />

</FrameLayout>
```

---

# 6. item_image.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<ImageView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/imageView"
    android:layout_width="match_parent"
    android:layout_height="180dp"
    android:scaleType="centerCrop"
    android:padding="4dp"
    android:contentDescription="Grid Image" />
```

---

# 7. fragment_webview.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<FrameLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <WebView
        android:id="@+id/webView"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

</FrameLayout>
```

---

# 8. main_menu.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<menu xmlns:android="http://schemas.android.com/apk/res/android">

    <item
        android:id="@+id/action_select_all"
        android:title="Select All" />

    <item
        android:id="@+id/action_edit"
        android:title="Edit" />

    <item
        android:id="@+id/action_share"
        android:title="Share" />

</menu>
```

---

# 9. dummy.html

```html
<!DOCTYPE html>
<html>

<head>
    <title>Experiment 8</title>
</head>

<body>

    <h1>Android WebView</h1>

    <h2>Experiment 8</h2>

    <p>This webpage is loaded using WebView.</p>

    <p><b>Name:</b> Erika Fernandes</p>

    <p><b>USN:</b> YOUR_USN</p>

    <h3>Menus and WebView</h3>

    <p>
        This page demonstrates loading a local HTML file
        inside an Android WebView.
    </p>

</body>

</html>
```

Replace `YOUR_USN` with your actual USN.

---

# OUTPUT

### GridView Output



```markdown

```

### Options Menu

```markdown

```

### Popup Menu

```markdown

```

### WebView

```markdown
```

---

## Result

The Android application was successfully developed using **GridView, Fragments, Options Menu, Popup Menu, and WebView**. The application displays images in a grid, provides menu-based actions, and loads a local HTML webpage using WebView.

---

## Conclusion

The application successfully demonstrates the use of **Fragments, GridView, ImageView, Options Menu, Popup Menu, and WebView** in Android. It provides practical understanding of menu handling, image display, fragment navigation, and webpage rendering within an Android application.

