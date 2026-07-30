https://github.com/user-attachments/assets/fe550364-3a8e-40c6-934a-962990baf98a

## Experiment 2: Implement Android Activity Lifecycle using lifecycle methods.														

## Aim

To understand the Android Activity Lifecycle by implementing different lifecycle methods in Kotlin and observing their execution using Toast messages.

---

## Objective

The objective of this experiment is to understand how Android manages the lifecycle of an Activity and how different lifecycle callback methods are executed during various user interactions.

---

## Technology Used

- Android Studio
- Kotlin
- Android SDK
- Android Emulator (Pixel 9)

---

## Activity Lifecycle Methods

### onCreate()
Called when the activity is created.

### onStart()
Called when the activity becomes visible.

### onResume()
Called when the activity comes to the foreground and becomes interactive.

### onPause()
Called when another activity partially covers the current activity.

### onStop()
Called when the activity is no longer visible.

### onRestart()
Called when the activity is restarted after being stopped.

### onDestroy()
Called before the activity is destroyed.

---

## CODE

package com.example.exp2

import android.os.Bundle
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        Toast.makeText(this, "onCreate Called", Toast.LENGTH_SHORT).show()
    }

    override fun onStart() {
        super.onStart()
        Toast.makeText(this, "onStart Called", Toast.LENGTH_SHORT).show()
    }

    override fun onResume() {
        super.onResume()
        Toast.makeText(this, "onResume Called", Toast.LENGTH_SHORT).show()
    }

    override fun onPause() {
        super.onPause()
        Toast.makeText(this, "onPause Called", Toast.LENGTH_SHORT).show()
    }

    override fun onStop() {
        super.onStop()
        Toast.makeText(this, "onStop Called", Toast.LENGTH_SHORT).show()
    }

    override fun onRestart() {
        super.onRestart()
        Toast.makeText(this, "onRestart Called", Toast.LENGTH_SHORT).show()
    }

    override fun onDestroy() {
        super.onDestroy()
        Toast.makeText(this, "onDestroy Called", Toast.LENGTH_SHORT).show()
    }
}

