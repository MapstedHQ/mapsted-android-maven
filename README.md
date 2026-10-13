# Mapsted Android SDK — Maven distribution

Public Maven repository hosting the **Mapsted Android SDK `26.10.2`** client artifacts
(`com.mapsted:android-sdk-*`). Served as static files via GitHub Pages — no authentication required.

**Full integration guide:** https://developer.mapsted.com/mobile-sdk/

## Repository URL

```
https://mapstedhq.github.io/mapsted-android-maven
```

## Usage (Gradle)

**`settings.gradle`** (or `allprojects { repositories { … } }`):

```groovy
repositories {
    google()
    mavenCentral()
    maven { url 'https://mapstedhq.github.io/mapsted-android-maven' }
}
```

**`app/build.gradle`:**

```groovy
android {
    defaultConfig {
        minSdkVersion 26                                   // SDK 26.10.2 requires minSdk 26
        manifestPlaceholders = [versionCode: "1", dateString: "2026-07-09"]  // required by the SDK
    }
}

dependencies {
    // BOM aligns all module versions
    implementation platform('com.mapsted:android-sdk-bom:26.10.2')

    implementation 'com.mapsted:android-sdk-core'
    implementation 'com.mapsted:android-sdk-map'
    implementation 'com.mapsted:android-sdk-ui'
    implementation 'com.mapsted:android-sdk-ui-components'
    implementation 'com.mapsted:android-sdk-geofence'
    implementation 'com.mapsted:android-sdk-geofence-offline'
    implementation 'com.mapsted:android-sdk-loc-marketing'
    implementation 'com.mapsted:android-sdk-inapp-notification'
    implementation 'com.mapsted:android-sdk-topbar-notifications'
    implementation 'com.mapsted:android-sdk-loc-share'
    // App template (optional starter): android-app-template, android-app-template-core
}
```

**ProGuard / R8** (`proguard-rules.pro`), if you enable minification:

```proguard
-dontwarn org.joda.convert.**
```

## Modules (`26.10.2`)

| Artifact | Purpose |
|---|---|
| `android-sdk-bom` | Bill of Materials (version alignment) |
| `android-sdk-core` | Positioning core + engine |
| `android-sdk-map` | Map rendering (Carto) |
| `android-sdk-ui` | Map UI |
| `android-sdk-ui-components` | Reusable UI components |
| `android-sdk-geofence` / `android-sdk-geofence-offline` | Geofencing |
| `android-sdk-loc-marketing` | Location marketing |
| `android-sdk-inapp-notification` / `android-sdk-topbar-notifications` | Notifications |
| `android-sdk-loc-share` | Location sharing |
| `android-app-template` / `android-app-template-core` | Optional app template |

---
© Mapsted. See https://developer.mapsted.com/mobile-sdk/ for licensing and full documentation.
