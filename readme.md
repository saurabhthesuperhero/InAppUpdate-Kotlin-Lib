![Build Status](https://img.shields.io/badge/build-passing-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue) ![Release Version](https://img.shields.io/badge/release-v8.0.2-blue)
---

# In-App Update Library for Android

## Introduction

The In-App Update Library simplifies the integration of in-app updates in Android applications. It provides a straightforward way to check for updates and prompt users to update your app using Google Play's core app update features. This library is ideal for ensuring that your users always have the latest version of your app with minimal hassle.

## Features

- Easy integration of in-app updates.
- Supports immediate update flows.
- Simplified API for checking and starting updates.

## Demo

<img src="https://github.com/saurabhthesuperhero/InAppUpdate-Kotlin-Lib/assets/40573988/e1f96543-5e01-45bb-9c69-de66f78d63a7" width="200"/>
<img src="https://github.com/saurabhthesuperhero/InAppUpdate-Kotlin-Lib/assets/40573988/7ea12053-75af-4cf9-9d7c-9908a7055c24" width="200"/>
<img src="https://github.com/saurabhthesuperhero/InAppUpdate-Kotlin-Lib/assets/40573988/a5059a86-0f30-47c7-a746-563899f13260" width="200"/>

## Getting Started

### Prerequisites

- Android Studio
- An Android project with minimum SDK version 23.

## Installation

To use the In-App Update Library in your project, follow these steps:

### Step 1: Add the JitPack repository to your build file

Add JitPack to your project's build file. Open your root `build.gradle` file and add the following to the `repositories` section:

```gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

### Step 2: Add the dependency

Next, add the dependency for the In-App Update Library in your module's `build.gradle` file:

```gradle
dependencies {
    implementation 'com.github.saurabhthesuperhero:InAppUpdate-Kotlin-Lib:8.0.2'
}
```

After these steps, sync your project with the Gradle files to ensure that the library is properly imported into your project.

### Usage

1. **Initialization**:

   In your `MainActivity` or any other `Activity` from which you want to start the update process, initialize the `InAppUpdateManager`:

   ```kotlin
   import com.simplifymindfulness.inappupdate_library.InAppUpdateManager
   import androidx.activity.result.ActivityResultLauncher
   import androidx.activity.result.contract.ActivityResultContracts
   import android.os.Bundle
   import androidx.activity.ComponentActivity
   import androidx.activity.compose.setContent
   import com.google.android.material.composetheme.adapter.InAppUpdateKotlinLibTheme
   import androidx.compose.material3.MaterialTheme
   import androidx.compose.material3.Surface
   import androidx.compose.ui.Modifier
   import androidx.compose.ui.layout.fillMaxSize

   class MainActivity : ComponentActivity() {
       private lateinit var activityResultLauncher: ActivityResultLauncher<IntentSenderRequest>

       override fun onCreate(savedInstanceState: Bundle?) {
           super.onCreate(savedInstanceState)
           activityResultLauncher = registerForActivityResult(ActivityResultContracts.StartIntentSenderForResult()) { result ->
               // Handle the result of the update flow here
           }
           InAppUpdateManager.init(this, activityResultLauncher)
           setContent {
               InAppUpdateKotlinLibTheme {
                   Surface(modifier = Modifier.fillMaxSize(), color = MaterialTheme.colorScheme.background) {
                       HelloOpenSource()
                   }
               }
           }
       }
   }
   ```

2. **Handling Update Results**:

   Implement the logic to handle the result of the update flow in the `registerForActivityResult` callback.

### Contributing

Contributions are welcome! If you have a bug to report or a feature to suggest, please open an issue or submit a pull request.

