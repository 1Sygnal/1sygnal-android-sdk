# 1Sygnal Android SDK

Native Android SDK for 1Sygnal in-product surveys.

## Installation

Add the 1Sygnal Maven repository:

```kotlin
repositories {
    maven { url = uri("https://repo.1sygnal.app") }
}
```

Add the dependency:

```kotlin
dependencies {
    implementation("app.onesygnal:onesygnal-sdk:VERSION")
}
```

## Setup

Add your API key to `AndroidManifest.xml`:

```xml
<meta-data
    android:name="app.onesygnal.API_KEY"
    android:value="YOUR_API_KEY" />
```

## Initialization

```kotlin
import io.onesygnal.sdk.api.OneSygnal

OneSygnal.initialize(context) { success ->
    // SDK is ready to evaluate triggers
}
```

## Docs

See https://1sygnal.com/docs for the full integration guide.
