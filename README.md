# react-native-facetec-zoom

unofficial react-native bridge for Facetec's [Zoom SDK](https://dev.zoomlogin.com/).

## Functions

- liveness detection
- ...TODO

## Install

### Common

```sh
npm i -S tradle/react-native-facetec-zoom
react-native link react-native-facetec-zoom
```

### iOS

This library has been tested with version 7.0.15 of the SDK

First, download `ZoomAuthenticationHybrid.framework` from one of these sources:

- [Zoom SDK](https://dev.zoomlogin.com/zoomsdk/#/downloads)
- [app.tradle.io](https://s3.amazonaws.com/app.tradle.io/sdk/ZoomAuthentication-ios-7.0.15.zip)

Unzip the file, locate `ZoomAuthenticationHybrid.framework`, copy it to your `ios/` directory, and drag it to your project in XCode (Check the `Copy items if needed` option when asked)

Add a Copy File phase to your Xcode project and have `ZoomAuthenticationHybrid.framework` copied to Destination `Frameworks`

Add a Run Script phase to your Xcode project with the following contents:
```sh
bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/ZoomAuthenticationHybrid.framework/strip-unused-architectures-from-target.sh"
```

If you have an Objective-C project, add a blank Swift file to your project (File -> New -> Swift File), with a bridging header (it will prompt you to auto-create one).

add `NSCameraUsageDescription` to your Info.plist, e.g.:
```xml
<key>NSCameraUsageDescription</key>
<string>verify liveness with Zoom</string>
```

### Android

In your project's build.gradle (android/build.gradle), add the maven block below:

```gradle
allprojects {
  repositories {
    //  ...
    maven {
        url 'http://maven.facetec.com'
    }
}

If you want to override the default version of the Zoom SDK, add:

```gradle
ext {
  // ...
  zoomSdkVersion = '7.0.11' // <--- whichever version you want to use
  // ...
}
```

```

This module depends on [react-native-image-store](https://github.com/tradle/react-native-image-store), so you'll need to npm install and react-native link that one too.

## Usage

See example app at https://github.com/tradle/rnzoomexample
