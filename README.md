# Sonar Android SDK

Syncs Health Connect and Samsung Health data to Sonar for your signed-in users. The SDK reads the
phone's health stores, uploads in the background, and keeps its place; your backend reads the
normalized data from the Sonar API.

- Android 8.0 (API level 26) or later
- Beta: the API can still change before 1.0
- Guide: https://docs.sonarhealth.co/android-sdk/
- Examples (a demo backend, iOS and React Native): https://github.com/Sonar-Health/sonar-sdk-examples

## Before you start

- An SDK app ID: add your package name in Atlas → Developers → Apps.
- A Sonar API key, kept on your backend. Sandbox or live follows the key; the app is built the same
  for both.
- A Sonar user for each of your users (`POST /v1/users`).

## Install

Add this repository to `settings.gradle.kts`, and the SDK to your app module:

```kotlin
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven("https://raw.githubusercontent.com/Sonar-Health/sonar-android-sdk/main/maven")
    }
}
```

```kotlin
dependencies {
    implementation("co.sonarhealth:sonar-sdk:0.1.7")
}
```

Samsung Health is read through Samsung's own SDK, which Samsung hands out as a file: to sync it, add
that file and the runtimes it needs to your app, as the guide shows. Without it the SDK reads Health
Connect only.
