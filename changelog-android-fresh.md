# Changelog for AppGyver Scanner (Android)

## 4.0.0: Major Feature Parity with iOS

For information about the new Crosswalk x86 and ARM build options, please see our [Android build types guide](https://academy.appgyver.com/categories/8-distribution/contents/147-android-build-types).

### Features:
- In place animations (flip and slide to four directions).
- Complete Layers API (closes [#553](https://github.com/AppGyver/steroids/issues/553))
  - `steroids.layers.replace`
  - `steroids.layers.popAll`
- Unload a WebView with `view.unload`.
- Update to Crosswalk 9 with Chromium 38.
- Implement view related events:
  - `visibilitychange` (requires Steroids.js 3.5.6)
  - `steroids.layers.on/off`
  - `steroids.modal.on/off`
  - `steroids.tabBar.on/off`
- Implement rest of Tab Bar API
  - `steroids.tabBar.replace`
  - `steroids.tabBar.currentTab.update`
- Drawer API methods
  - `steroids.drawers.update`
    - enable/disable gestures
    - change the drawer size
    - display shadow between the center view and drawer
  - `steroids.drawers.show`
  - `steroids.drawers.hide`
  - `steroids.drawers.on/off`

### Changes:
- Sped up layer transitions to be consistent with iOS (0.6s --> 0.3s).
- Upgrade build-tools to 21.1 and Android SDK to 21 (Android 5.0 Lollipop).
- Improve Pixate consistency between iOS and Android.

### Bugfixes:
- Back button events now work on Crosswalk builds too (fixes [#519](https://github.com/AppGyver/steroids/issues/519)).
- Fixed a crash when changing orientation too many times with Crosswalk (fixes [#575](https://github.com/AppGyver/steroids/issues/575))
- Fixed three WebView related memory leaks, which will help overall stability.
- Locked touch events and API calls during in-place animations (fixes [#539](https://github.com/AppGyver/steroids/issues/539)).
- Navigation Bar did not show title image.
- Replacing layers failed when doing the API call from a WebView which was not visible, ie. not added to any layer. (fixes [#581](https://github.com/AppGyver/steroids/issues/581)).
- Fixed a crash occurring when onPageLoaded callback was invoked for a WebView which had already been killed (affected especially slower devices).
- Fixed a crash occuring when enter was pressed in the Steroids console while `about:inspect` chrome debugging was open.
- Crosswalk Scanner crashed when Chrome Debugger was open while doing a
  project refresh.
- `steroids.getApplicationState()` returned list of preloads as a string
  instead of a proper JSON array.


### Known issues:
- Crosswalk Chromium WebViews appear as stretched for a moment after focusing out from a Native UI Control or after rotation [#574](https://github.com/AppGyver/steroids/issues/574).
- On Crosswalk Viewport size must be defined in the HTML or content will appear as zoomed out
  ([#297](https://github.com/AppGyver/steroids/issues/297)). In hybrid apps this causes in iOS the drawers to scroll. Suggested workaround for this is to create a different layout for the Steroids application's CONTENT and DRAWER.
- App crashes if only one drawer is defined [#606](https://github.com/AppGyver/steroids/issues/606).
- Replacing the center layer while hiding the drawer causes loss of the nav bar and tab bar of the WebView [#608](https://github.com/AppGyver/steroids/issues/608).
- After calling `modal.hide` the native back button won't work in Crosswalk [#610](https://github.com/AppGyver/steroids/issues/610).
- If a modal is open during rotation, the WebView below it flashes quickly on top [#609](https://github.com/AppGyver/steroids/issues/609).
- Nexus 5 with Android version 4.4.4 crashes on `layers.push` in Scanner. Standalone builds seem to do better.
- `visibilitychange` is not fired on document hide [#607](https://github.com/AppGyver/steroids/issues/607).
- `steroids.app.getMode` returns "scanner" in Standalone builds.
- `navigationBar.setStyleCSS` does not apply style [#586](https://github.com/AppGyver/steroids/issues/586).



## 3.5.4 (2014-10-23): Splash Screen, Initial View and Native CSS styling

### Features:
- Display Splashscreen on application start (closes [#159](https://github.com/AppGyver/steroids/issues/159)).
  - Splashscreen is displayed for three seconds by default and then hid automatically.
  - To gain control over when to hide splashscreen, use `steroids.splashscreen.hide()` and set `AutoHideSplashScreen` to false in `config.android.xml`.
- InitialView can be shown, dismissed and app can be resetted to it
- Drawer can be initialized from application.coffee.
- Implement API for `steroids.tabBar.update`.
- Navigation Bar modification methods available:
  - Back button text can be modified and replaced with an image
  - Back button can be overridden
  - Navigation Bar can have an image as the title
  - Navigation Bar can have multiple custom buttons
    - both image and text are supported
- Style Native UI elements with CSS (Pixate).
  - Define styles in `dist/native-styles/android.css`.
  - API for `setStyle`, `setClass` and `setId`.
  - Change the whole Native UI styling at once with `steroids.app.loadTheme()`.
  - Supported elements: Navigation Bar, Buttons, Tab Bar.
- Define a Native CSS `id` in application.coffee for Tabs, to allow convenient styling of individual Tab Items (eg. setting the icon individually for each Tab).
- Status bar onSuccess and onFailure callbacks on show and hide
- Loading.html is shown when WebView is pushing, tabs are loading or a modal is shown (closes [#483](https://github.com/AppGyver/steroids/issues/483)).
- Set WebView default background color to white.
- Return a list of all currently preloaded WebViews with `steroids.app.getApplicationState()`.
- Cordova assets are no longer copied to internal storage in Scanner to speed up the application start. Cordova can now only be loaded from `http://localhost/cordova.js`.
- Make Cordova's ScrollEvent class available to Cordova plugins.
- Output WebView console.log messages using INFO log level (ie. visible on production builds).
- When application is started with a custom schema, the value can be read from `window.AG_APP_STARTUP_URL` ([#141](https://github.com/AppGyver/steroids/issues/141)).
- Include hardcoded Open GL 2 version in default Android Manifest for Google Maps plugin support. This will be fixed properly by providing this is as a user configurable option.
- Remove permission `DOWNLOAD_WITHOUT_NOTIFICATION` which is no longer needed.
- Load Scanned Application in an emulator without requiring to scan the QR code.

### Bugfixes:
- Displaying a WebView no longer causes a nasty blink (fixes [#525](https://github.com/AppGyver/steroids/issues/525)).
- When using Tab Bar, sometimes a wrong WebView was visible with Chromium (fixes [#526](https://github.com/AppGyver/steroids/issues/526)).
- Opening two Steroids layers no longer result in two WebViews being created.
- Sending a post message caused a NPE when application was shutting down.
- CordovaWebView#reload() expected by plugins is now implemented.
- Showing the soft keyboard on top layer caused flickering.
- Status Bar hide/show and rotation from landscape->portrait caused flickering.
- Sending a Post Message caused the recipient view to flicker over the sender
  view (affected only Chromium runtimes).
- Tab Bar sometimes appeared as empty right after application start.
- API `navigation.bar.show()` is now consistent with iOS:
  - Success callback is invoked.
  - Change default to show navigation bar without animation.
- Cordova's `config.(android.).xml` was not properly applied. This caused problems with plugins depending on it (eg. FileTransfer, Urban Airship) (fixes [#564](https://github.com/AppGyver/steroids/issues/564), [#533](https://github.com/AppGyver/steroids/issues/533)).
- Certain null attribute values in application.coffee caused a crash.
- WebView touch events are now disabled when opening a new WebView. This previously allowed to eg. invoke several subsequent layers.push() method calls by repeatedly tapping a button (fixes [#539](https://github.com/AppGyver/steroids/issues/539)).

### Known issues:
- Chromium WebViews appear as stretched after focusing out from a Native UI Control [#574](https://github.com/AppGyver/steroids/issues/574).
- Chromium runtime crashes with out-of-memory error when changing the device
  orientation too many times in a short period of time ([#575](https://github.com/AppGyver/steroids/issues/575)).
- On Chromium Viewport size must be defined in the HTML or content will appear as zoomed out
  ([#297](https://github.com/AppGyver/steroids/issues/297)). In hybrid apps this causes in iOS the drawers to scroll. Suggested workaround for this is to create a different layout for the Steroids application's CONTENT and DRAWER.
- Chromium runtime doesn't handle device button events correctly and crashes sometimes on e.g. backbutton event
  ([#519](https://github.com/AppGyver/steroids/issues/519)).


## 3.5.3-p1 (2014-10-03): Cordova Security Update

Bug fixes:
- Apply security fix for Cordova issue
[CVE-2014-3502](http://cordova.apache.org/announcements/2014/08/04/android-351.html).
  Updates Cordova version to 3.5.1.


## 3.5.3 (2014-09-18): Fresh Android replaces Legacy Android

### Features:
- Support for multi-page applications:
  - Views can be pushed/popped in the layer stack.
  - Modal can be displayed and hid.
  - All modals can be closed at once.
  - Basic animation for layer transitions.
  - Preloaded views.
  	- Views can be preloaded in the preloads array in `application.coffee`.
  - Tab bar for selecting the current set of views on the screen.
  - Back button navigates back in the current view stack.
  - WebViews have unique identifiers (UUID) available API calls.
  - Tab bar is displayed on the bottom by default to allow better multiplatform
    consistency. Tab bar position can be changed in the future in `application.coffee`
    and with `steroids.tabBar.update`.
- Navigation Bar
  - Back button takes to the previous WebView
  - API calls
    - show / hide the navigation bar
    - set the navigation bar title
- Completely revamped Chromium internals
  - Chromium is now provided by the [Crosswalk Project](https://crosswalk-project.org/).
  - Crosswalk 8.37.189.7 with Chromium M37.0.2062.94
    (closes [#485](https://github.com/AppGyver/steroids/issues/485))
- Chromium runtime supports loading project assets from http://localhost.
- Required permissions can be configured in the Build Service
  (closes [#508](https://github.com/AppGyver/steroids/issues/508))
- Scanner shares similar outlook with the AppGyver iOS client.
- Communicate between WebViews using JavaScript post messages.


### Bugfixes:
- Return HTTP 404 Not Found when an asset from http://localhost does not
  exist. Previously "Connection Refused" was the result which caused problems.
  (fixes [#524](https://github.com/AppGyver/steroids/issues/524))
- URLs with a double slash no longer give an error message,
  eg. `http://localhost//index.html` (fixes [#514](https://github.com/AppGyver/steroids/issues/514))
- Scanned URL is correctly remembered when opening a previously scanned app
  (fixes [#513](https://github.com/AppGyver/steroids/issues/513))
- Scanner intelligently selects the correct IP address from the scanned
  QR code (fixes [#302](https://github.com/AppGyver/steroids/issues/302))
- Exiting the app no longer causes Illegal State Exception
  (fixes [#504](https://github.com/AppGyver/steroids/issues/504))
- Scanner no longer runs out of memory with a one second polling interval
  (fixes [#359](https://github.com/AppGyver/steroids/issues/359))
- Implement rest of Chromium WebView APIs required by Cordova

### Known issues:
- When pushing a layer or opening a modal the WebView blinks as black (white on Chromium) ([#525](https://github.com/AppGyver/steroids/issues/525)).
- When using Tab Bar, the app sometimes opens with empty tabs or shows the wrong content in the tabs ([#526](https://github.com/AppGyver/steroids/issues/526)). This corrects itself when the tabs are clicked on a few times.
- On Chromium Viewport size must be defined in the HTML or content will appear as zoomed out
  ([#297](https://github.com/AppGyver/steroids/issues/297)). In hybrid apps this causes in iOS the drawers to scroll. Suggested workaround for this is to create a different layout for the Steroids application's CONTENT and DRAWER.
- Chromium runtime doesn't handle device button events correctly and crashes sometimes on e.g. backbutton event
  ([#519](https://github.com/AppGyver/steroids/issues/519))
- Android 4.0 issues:
  - Cordova plugins for Steroids Addons do not initialize correctly ([#493](https://github.com/AppGyver/steroids/issues/493))
  - No animations
  - On some older devices on Chromium `layers.push` and `modal.show` do not work and crash the app
  - On some older devices opening modals on top of modals does not work
- Android 2.3 is no longer supported starting from 3.5.3
  - Release 3.5.2 will be stay available in Build Servier as a support release for Android 2.3.


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
- **Many Cordova plugins don't initialize correctly on Android 4.0 and cause the build to constantly crash.** Same plugins work with Android 4.0 on Fresh Android 3.5.1 and on Android >= 4.1 in Fresh Android 3.5.2. This will be fixed in a patch ASAP. Issue [#493](https://github.com/AppGyver/steroids/issues/493)
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
