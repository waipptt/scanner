# Changelog for AppGyver Scanner (Fresh Android)

## 3.5.2 (2014-08-22): Stabilizing the SPA runtimes and Cloud QR codes

###Features:
- AppGyver Cloud QR code can be used to load the Steroids Application. Closes [#459](https://github.com/AppGyver/steroids/issues/459).
- Android keyboard's Go button triggers an event that can be used on Javascript side. Closes [#455](https://github.com/AppGyver/steroids/issues/445).
- Opening appgyver:// schema will open the Fresh Android application.
- Updated media-capture plugin to 0.3.1
- Updated media plugin to 0.2.11
- Updated file-transfer plugin to 0.4.4
- Updated file plugin to 1.2.0
- Updated camera plugin to 0.3.0
- Facebook SDK is included by default (will be optional later), which allows the official
	Cordova Facebook plugin to compile.
- Complete support for Cordova's onMessage (required for plugins).
- Steroids application can send logs to Steroids CLI (or any endpointUrl)

###Bug fixes:
- navigator.app.exitApp() now quits the application. Closes [#461](https://github.com/AppGyver/steroids/issues/461).
- Previously opened WebViews are now closed after a scanned application is restarted. Closes [#301](https://github.com/AppGyver/steroids/issues/301).
- Most of Android permissions required by Scanner are marked as optional, so that Fresh Scanner can be downloaded from Google Play to a wider range of devices.
- Fixed crash caused by the QR code reader timing out or returning corrupted data.
- Fixed compatibility with the email composer Cordova plugin.
- Refresh Client no longer stops polling for updates if it encounters an error.

###Known issues:
- Cordova's Capture video crashes on Android 4.4 devices after giving success callback. Issue [#491](https://github.com/AppGyver/steroids/issues/491).
- Cordova's Geolocation's callbacks do not always work on all Android 4.0 devices. We haven't been able to pinpoint this yet, but are looking into the issue.
- Cordova's Notification.beep does not work on all Android 4.0 and 4.1 devices.

## 3.5.1 (2014-07-24): Cordova support, localhost and device orientations

###Features

* Implemented full Cordova support
	* Support for Geolocation.
	* Support for Cordova core events. Closes [#363](https://github.com/AppGyver/steroids/issues/363).
	* Cordova plugin result is correctly available to the Steroids application.
	* Complete Cordova support with full application life-cycle.
	* Back button goes back in web history.
* Improved Scanner's user interface:
	* re-open and re-download buttons
	* display human readable error messages
	* display a loading indicator
	* improved handling of different error situations
	* display more exact error messages in device log on failures
* Support different Android device orientations and building landscape-only apps. Closes [#358](https://github.com/AppGyver/steroids/issues/358)
* Support for serving files from `http://localhost` (WebKit runtimes, i.e. not Chromium Fresh Android). Closes [#162](https://github.com/AppGyver/steroids/issues/162).
	* Steroids project files
	* UserFiles
	* Support for the ".android." naming convention for Android specific files
* Files defined in application.json's copy_to_user_files will be copied from project assets to UserFiles for write-access. Closes [#428](https://github.com/AppGyver/steroids/issues/428).
* Support for AdMob Cordova plugin
* Support for more Steroids APIs:
	* `steroids.statusBar.show` and `steroids.statusBar.hide`
	* `steroids.screen.rotate`
	* `steroids.app.host.getUrl`
* JavaScript alert() dialog is now displayed.
* Updated Contacts Cordova plugin to 0.2.11

###Bugfixes

* Cordova Media APIs trigger success/error callbacks. Closes [#458](https://github.com/AppGyver/steroids/issues/458).
* FileTransfer Cordova plugin failure
* Tapping "Go" in the keyboard did not dismiss the keyboard with Ionic tab bar
* Steroids APIs that depend on SteroidsApplication were not functioning perfectly.
* Fixed Cordova activity leak
* Standalone reported wrong applicationFullPath

###Known Issues

* Cordova barcodeScanner is not included in core plugins
* Cordova compass returns an initial heading of 0, subsequent calls work
* `navigator.notification.beep` freezes the screen for duration of beep on Android 4.4

## 3.5.0-p1 (2014-06-12): Fresh Android Scanner in Google Play

###Features:
* Fresh Android logo and Beta warning text added to the Scanner scanning screen

Also Build Service was fixed so that it does not break with the default splash screens, currently Fresh Android builds ignore splash screens because they are not yet used in the builds.

## 3.5.0 (2014-06-06): First Steroids and Cordova APIs
First release of Fresh Android that includes some Steroids and Cordova API calls!

###Features:

* Steroids API Bridge for all runtimes.
* Implemented the first batch of Steroids API calls:
	* ping
	* alert
	* log
	* getEdgeMode
	* getIPAddress
	* getApplicationPath
	* openURL
	* getCurrentVisibility
	* setSleepDisabled
	* getUserLocale
	* cancelAllDownloads
* Support for adding Cordova plugins to the project
* Included some Cordova core plugins:
	* org.apache.cordova.device-motion
	* org.apache.cordova.media-capture
	* org.apache.cordova.device-orientation
	* org.apache.cordova.network-information
	* org.apache.cordova.contacts
	* org.apache.cordova.device
	* org.apache.cordova.battery-status
	* org.apache.cordova.globalization
	* org.apache.cordova.media
	* org.apache.cordova.dialogs
	* org.apache.cordova.camera
	* org.apache.cordova.inappbrowser
	* org.apache.cordova.console
	* org.apache.cordova.file-transfer
* Added initial support for http://localhost for Cordova assets in WebKit runtimes.
* Local Storage support for WebKit runtimes.

###Bugfixes:

* Chromium runtime now supports folders which have a dot "." in their name

###Known issues:

* The Cordova Media APIs do open the Camera/Recorder but do not return the image/video/sound.
* Android 2.3 does not support localhost so Cordova will have to be loaded from "../../www/cordova.js"

__Chromium is still quite experimental and has quite many issues:__
* On some devices the screen glitches with noise sometimes, especially behind modals
* Cordova API's are unstable and requires screen reload or another Cordova API call to show the previous call on the screen.
* Sometimes the Chromium app opens but does not respond or load Cordova. Restarting the app usually solves this issue.
* In ChromeWebView sometimes touch events are misaligned
* Some devices crash or do not show up on Chrome Web Inspector


## 0.4 (2014-05-14): Chromium on Android 4.x

* Remote debugging with Chrome works with Android 4.x devices (open `about:inspect` in Chrome).
* Steroids apps are more consistent between different devices because the browser engine doesn't depend on Android's version.
* You can use newest HTML5 features on all Android 4.x devices.
* On our Canvas rendering tests, Fresh Android is 2-3 times faster using Chromium than the Android 4.4 default WebView.
* Fresh Android with platform WebView supports API levels 10-19 (Android 2.3.3 - 4.4).
* Fresh Android Chromium supports API levels 14-19 (Android 4.x).
* Chromium will add 22 MB to the APK file size. Therefore Fresh Android Chromium is its own build target in the Build Service. The APK size using the platform WebView (without Chromium) is around 1 MB.

## 0.3 (2014-05-02): Remote Debugging on Android 4.4

* Remote debugging with Chrome on Android 4.4
	* Connect your 4.4 device with a cable and open `about:inspect` in Chrome.


## 0.2 (2014-04-28): Android 2.3 Support

* Android 2.3 support (API levels 10-19)
	* Minimum SDK level can be configured in Build Service.
	* Maximum SDK level setting has no effect for Fresh Android.
	* See [Android Developer guide](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html) for details about selecting an SDK level.

## 0.1 (2014-04-15): Launch!

First beta release!

Supported Android versions:
Android 3.0.x (API level 11) to Android 4.4 (API level 19)

Supported features:

* Single-Page Applications from a File URL. File URLs start without a leading slash, eg. "index.html".
* Start application from a scanned QR code which points to Steroids CLI.
* Steroids CLI refresh will reload project.
* Buildable from AppGyver Build Service having adhoc, scanner and Google Play as build targets.
* Supported settings in Build Service:
	* Keystore
	* Prodution, Ad Hoc and Scanner Build settings EXCEPT min/max SDK level
	* Icons
