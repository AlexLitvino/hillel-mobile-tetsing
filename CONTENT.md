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
