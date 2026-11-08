# Android

### Step 1: Add nSure SDK to your app

Add it in your root **build.gradle** at the end of `repositories`:

```gradle
allprojects {
  repositories {
    maven { url 'https://jitpack.io' }
  }
}
```

Add the dependencies:

```gradle
implementation 'com.github.nsure-ai:android-sdk:1.4.3'
implementation 'com.fingerprint.android:sdk:4.0.0'
```

---

### Step 2: Add screen-capture permission

In your **AndroidManifest.xml**, add:

```xml
<uses-permission android:name="android.permission.DETECT_SCREEN_CAPTURE" />
```

This permission is required for nSure to detect when the user takes a screenshot.

---

### Step 3: Initialize

Initialize nSure with your application context:

```java
// Basic initialization
NSure nSure = NSure.getInstance(this.getApplicationContext(), "SAMPLE_ANDROID_APP_ID", "PARTNER_ID");

// Optionally specify a custom configuration base URL
NSure nSure = NSure.getInstance(this.getApplicationContext(),
                                "SAMPLE_ANDROID_APP_ID",
                                "PARTNER_ID",
                                "https://custom-config-url.com");

// Optionally also specify a custom events reporting URL
NSure nSure = NSure.getInstance(this.getApplicationContext(),
                                "SAMPLE_ANDROID_APP_ID",
                                "PARTNER_ID",
                                "https://custom-config-url.com",
                                "https://custom-events-url.com");
```
#### Initialization Parameters:

* **appID**  
  The application identifier provided by nSure.ai.
* **partnerID**  
  The partner identifier provided by nSure.ai. If no partner ID is provided, set this value to `null`.
* **configBaseUrl**  
  An optional base URL used for DNS cloaking. This value will be provided by nSure.ai when applicable. If no value is provided, set this to `null`.
* **eventsReportUrl**  
  An optional base URL that overrides the default events reporting endpoint. This value will be provided by nSure.ai when applicable. If no value is provided, set this to `null`.

---

### Step 4: Retrieve device ID from the SDK

The merchant has to retrieve the device id from the sdk and pass it to the merchant's server.  
The merchant's server has to add this device id in every call to nSure servers.  
The request body should contain the device id under a property called `sessionInfo`. 

For example sessionInfo:
```json
{ "deviceId": "user-device-id" }
```

Java method access:
```java
NSure.getInstance().getDeviceId();
```
