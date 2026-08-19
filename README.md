# 1Sygnal Android SDK

Native Android SDK for 1Sygnal in-product surveys.

## Requirements

- Android `minSdk` 21+

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

ProGuard/R8 rules are bundled with the SDK — no manual keep rules are needed.

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

## Usage

### Tracking events

```kotlin
OneSygnal.track("checkout_completed", mapOf("plan" to "pro"))
```

### Identifying users

```kotlin
OneSygnal.identify("user-123", mapOf("plan" to "pro")) { success ->
    // identity synced
}
```

### Listening for survey events

```kotlin
val registration = OneSygnal.on("survey:completed") { event ->
    // handle completion
}

// Later, when no longer needed:
registration.cancel()
```

Other available events: `"ready"`, `"survey:shown"`, `"survey:dismissed"`, `"survey:question_answered"`.

Also available: `OneSygnal.logout()` and `OneSygnal.reset()` to clear session/user state,
`OneSygnal.setSurveysEnabled(enabled)` to toggle surveys at runtime, and `OneSygnal.shutdown()`
to tear the SDK down. See the docs for full details.

## Docs

Full integration guide: https://docs.1sygnal.app

## Other SDKs

- [iOS SDK](https://github.com/1Sygnal/1sygnal-ios-sdk)
- [Web SDK](https://github.com/1Sygnal/1sygnal-web)
