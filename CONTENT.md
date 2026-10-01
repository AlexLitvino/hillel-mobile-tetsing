# Mobile Testing: Practical Guide

## 01 Introduction to testing mobile applications
Monetization of mobile apps:
- Freemium
- Ads
- Transaction
- Payment
- Corporative
- Subscription

Types of devices:
- Base mobile phones
- Functional phones
- Smartphones
- Tablets
- Devices-companions (wearable and IoT)

Types of tetsing for mobile apps:
- Functional testing
- Productivness testing
- Security testing
- Compatibility testing
- UI testing

## 02 Types of mobile applications
Types of mobile applications:
- Native
- Hybrid
- Browser

Components of Mobile application:
- UI
- Application logic
- Backend
- DataBase
- Interaction between components


## 03 Strategy and risks when testing mobile applications
Typical risks:
- Data absence about device usage in region
- Uncertain business model
- Cost of development support for different platforms
- Absence of test devices

Challenges:
- Devices and platforms fragmentation
- Difference in hardware
- Many tools of development
- Difference in UI design and UX
- Different types of network
- Limitation of device resources
- Different channels of distributions
- High quality of feedback
- Publications approve on stores

Introduction to test strategy
- Goals of testing
- Using emulators and simulators on early stages
- Testing on real devices on later stages
- Coverage strategies
- Test environment preparation
- Test automation
- Reports and analysis

Selecting test strategy  
Defining testing goals:
1. Business requirements and user expectations analysis
2. Defining quality key indicators
3. Defining application critical functionalities
4. Risk assessment
5. Market and technology conditions analysis
6. Resource and limitations defining

Examples of test strategy goals:
- Finding defects on early stages
- Checking compatibility with main platforms and devices
- Application productivity analysis under high load

Coverage strategy:
- Single platform (test only on Android or iOS)
- Multiplatform (both Android and iOS)
- Maximal coverage


## 04 Emulators and simulators for mobile testing
Emulator imitates HW, simulator imitates only SW.


## 05 Downloading and installation Android Studio


## 06 Obtaining developers rights and connecting device
To enable Developer options, click 7 times on:  
About phone -> Serial number  
OR  
Software information -> Build number  

Then Developer options option will appear:  
Settings -> Developer options -> USB debugging

Device could be connected via cable or Wi-Fi


## 07 Android Emulator
Android Studio -> Tools -> Device Manager (AVD Manager)


## 08 Possibilities of Android emulator
Possibilities:
- Turn off/on
- Volume on/off
- Rotate
- Back/Home/Menu
- Screenshot
- Record video
- Snapshots (to save device state)
- Add keyboard
- Displays
- Cellular
- Battery
- Camera
- Location
- Phone
- Directional pad (joystick)
- Microphone
- Fingerprint
- Virtual sensors
- Google Play
- Settings


## 09 Frequent problem when working with Android Studio
Add to environment variable PATH the following path:
```shell
...\Android\Sdk\platform-tools
```
Check if it is set correctly
```shell
adb --version
```


## 10 APK-file static testing using aapt2
aapt2 (Android Asset Packaging Tool)
It is located
```shell
Android\sdk\build-tools\<MAX_ANDROID_VERSION>\aapt2
```
Check
```shell
aapt2 version
```

Common information
```shell
aapt2 dump badging <APK_FILE>
```
Results:
- versionName
- compileSdkVersionName
- sdkVersion - minimum version
- targetSdkVersion - target version
- usesPermission - list of permissions
- launchable-activity - activity that starts application
- feature-group - list of permissions that will be requested
- supports-screens
- locales - supported locales
- native-code - supported processors
- supports-any-density, densities - supported screen resolutions 

Permissions
```shell
aapt2 dump permissions <APK_FILE>
```

Get packagename
```shell
aapt2 dump packagename <APK_FILE>
```

```shell
aapt2 dump configurations <APK_FILE>
```
Manifest structure
```shell
aapt2 dump xmltree app.apk AndroidManifest.xml
```

Application resources
```shell
aapt2 dump resources app.apk
```

https://developer.android.com/tools/aapt2    aapt2  
https://developer.android.com/guide/topics/manifest/uses-sdk-element    Android API Levels  


## 11 Installation, update and removing (Android)
Installation
```shell
adb install path_to_your_apk.apk    // Install apk to device
```

Update (rollout)
```shell
adb install -r path_to_your_NEW_apk.apk
```

```shell
adb uninstall <PACKAGE_NAME>
```

List of all installed packages
```shell
adb shell pm list packages
```

Edge cases:
- Installation when not enough memory
- Interrupted installation/removing
- Clearing data

Clear data
```shell
adb shell pm clear <PACKAGE_NAME>
```


## 12 Installation, update and removing (iOS)
Installation via:
- App Store
- TestFlight
- Enterprise Distribution
- XCode
- QR-code (OTA Distribution)

Add device UID to Developers Profile


## 13 Interruption testing
Interruption:
- System
- Network
- Device state change
- External

System interruptions:
- Incoming calls
- SMS
- Push notifications
- System notifications (low battery, OS update)

Network interruptions:
- Connection lost
- Change from Wi-Fi to Cellular and back
- Airplane mode
- Roaming
- VPN

Device state change interruption
- Blocking/Unblocking
- Rotation
- Connecting/disconnecting charger
- Connecting/disconnecting earphones/other Bluetooth devices
- Turn on / off
- Sending app to background
- Opening notifications bar
- Automatic blocking

External interruptions:
- Notifications from other apps
- Emails
- Picture in picture
- Distributed screen


## 14 Permissions testing
In project permissions are kept in app.config (Android) or info.plist (iOS) files.  

Permissions types (Android)
- Normal Permissions (no request) (INTERNET, ACCESS_WIFI_STATE, VIBRATE)
- Dangerous Permissions (require explicit allowance) (CAMERA, READ/WRITE_EXTERNAL_STORAGE, READ_CONTACTS, ACCESS_FINE_LOCATION, READ_SMS)
- Signature Permissions (for apps developed by the same developer) (BIND_ACCESSIBILITY_SERVICE)
- Special Permissions (permissions provided only via System Settings) (SYSTEM_ALERT_WINDOW, WRITE_SETTINGS)

Permissions types (iOS)
- App Permissions (main functions and device data) (Location, Contacts, Camera, Microphone)
- Sensitive Data Permissions (access to confidential data) (Health, HomeKit, Siri)
- Hardware Permissions (access to device hardware components) (Bluetooth, NFC)
- System Permissions (access to system functions or services) (Background App Refresh, Notification)

Scenarios:
- Correctly asking permissions
- Adequate working when deny permission
- Sequential permission request
- Removing permissions
- If app asks for extra redundant permissions?
- Data security and confidentiality (data processed in correct way)
- Permissions on different OS versions

Additional scenarios:
- Permissions in different access modes (background, limited access)
- Permissions changes during app work
- Permission requests localization
- Integration with other applications
- Check permissions in extremal situation
- Different platforms and devices
- Compatibility to standards (GDPR, CCPA)


## 15 Checking network interaction during testing mobile applications
Scenarios:
- No Internet connection
- Changing to Cellular from Wi-Fi and back
- Slow internet
- Proxy and VPN
- Sending and obtaining data to/from server
- Error handling
- Correct caching


## 16 Push-notifications testing
Principles of push-notifications work:
1. Install app on device
2. OS request permission to send notifications. OS get token (device ID) from push-notifications service
3. OS sends token to server
4. Server sends notifications during events

Types of mobile notifications:
- Information notification
- Geolocation notification
- Re-engagement
- Ads notification
- Periodical notification
- Notification about survey

Types of mobile notifications:
- Text notifications
- Rich Notifications
- Actionable Notifications
- Local Notifications
- Push-to-Local Notifications

Technology:
- Firebase Cloud Messaging (FCM) (Android)
- Apple Push Notification Service (APNs) (iOS)

### Scenarios
Checks in different app state:
- Notification when app is not started
- Notification when app is started
- Notification when app in background
- Notification during app start
- Notification during game
- Notification when another app is active

Checks for interaction with notification:
- Click on notification
- Appropriate part app is open
- No repeatative notification
- Start app from background

Checks of display and behavior:
- Notification in different time zones
- Sound, vibration and blinking
- Notification in app
- Notification in bar
- Notification title
- Notification language
- Notification disappears from bar when it was opened

Checks of icons and counters:
- Counter update when new notification
- Counter update when notification was read


## 17 Logs
On Android, Android Studio -> Logcat  (View > Tool Windows > Logcat)
On iOS, using Console app  
```shell
adb logcat > logs.txt
adb logcat *:E > error_logs.txt
adb logcat -s MyApp > myapp_logs.txt
adb logcat -v time > logs_with_time.txt
adb logcat -G 16M
```

Log levels:
- Verbose
- Debug
- Information
- Warning
- Error
- Crash (Assert?)

Search in logs:
- Ctrl+F
- Filters (level:info & package:com.HillelAuto) (&|-() - logical operators)
- Custom tags (tag: <TAG_VALUE>)
