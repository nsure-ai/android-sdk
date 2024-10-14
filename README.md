### Step 1: Add nSure SDK to your app

Add it in your root build.gradle at the end of repositories:

```gradle
allprojects {
  repositories {
    maven { url 'https://jitpack.io' }
  }
}
```

Add the dependency

```gradle
implementation 'com.github.nsure-ai:android-sdk:1.3.3'
```
### Step 2: Initialize
Initialize nSure with app context:

```java
NSure nSure = NSure.getInstance(this.getApplicationContext(), "SAMPLE_ANDROID_APP_ID", "PARTNER_ID");
```

### Step 3: Retrieve device id from the sdk
The sdk exposes a method "getDeviceId" on NSure.getInstance and one can use this method to retrieve the device id.

The merchant has to retrieve the device id from the sdk and pass it to the merchant's server. The merchant's server has to add this device id in every call to nSure servers. The request body should contain the device id under a property called sessionInfo. 
For example sessionInfo:
```json
{ "deviceId": "user-device-id" }
```
Java method access:
```java
NSure.getInstance().getDeviceId()
```
