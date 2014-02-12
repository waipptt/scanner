# Changelog for AppGyver Scanner for Android

##3.1.2.1 (2014-02-10)

Reverted support for Android 4.4 due to it causing issues in both Android 4.4 and older versions.

##3.1.2 (2014-02-05)

Premilinary Android 4.4 support, bugfixes for back button and fullscreen preference.

Features:
  - Preliminary Android 4.4 support with limited features.

Bugfixes:
  - Fixed the issue of native backbutton exiting the app.
  - Fixed fullscreen preference in config.android.xml (also fixing [issue #97](https://github.com/AppGyver/scanner/issues/97) where WebView does not scroll when focusing on input element).

Android 4.4 known issues:
  - Requests to `http://localhost/` fail randomly. Serving the app via File protocol (i.e. `steroids.config.location = "index.html"`) works.
  - Animations to and from new (not preloaded) WebViews are uglier.
  - If you load a faulty document to a WebView, it usually results in a black screen instead of something informative.
  - Orientation settings other than "only portrait allowed" are not supported.
  - No ChromeView or awesome debugging or any of that stuff.
  - Cordova events `pause`,`resume` and `destroy` work inconsistently/might crash.


##3.1.1 (2013-12-19)

Improved Cordova 3.1 stability, all the Cordova core plugins now included, SQLite plugin fix.

Features:

  - Previously missing Cordova core plugins, File-Transfer and Console, are now included by default.
  - Updated all plugins to latest versions.

Changes:
  - Cordova.js can now be downloaded only from http://localhost/cordova.js.
  - Shortened the application label from "AppGyver Scanner" to "Scanner" to prevent truncating on some Android devices.

Bugfixes:
  - Fixed SQLite plugin compatibility issue

##3.1.0 (2013-12-04)

Cordova 3.1.0 upgrade, visibilitychange event fixes.

Changes:
  - Cordova support upgraded to 3.1.0
  - Plugins included in App Store Scanner: Cordova core plugins (excluding File-Transfer and Console), BarcodeScanner, Google analytics, SQLite plugin
  - BREAKING: the following plugins are no longer included by default:
      - File-Transfer
      - Calendar Plugin
      - DatePicker Plugin
  - Removed longpress touch listener which would quit the application

Bugfixes:
  - Fixed missing visibilitychange events when switching tabs
  - Fixed visibilitychange event issues related to pushing layers

## 2.7.6, 2.7.7, 2.7.8 (2013-07-19)

Stability improvements and bugfixes.

Bugfixes:
  - Fixed rare crash issues.
  - Fixed rare freeze issues.

## 2.7.5 (2013-07-01)

User agent reports if running inside Scanner or as a standalone app, bugfixes.

Features:
  - User agent now includes string "Scanner" if running inside Scanner app, otherwise includes string "StandAlonePackage".

Bugfixes:
  - Fixed issues with Cordova `pause` and `resume` events.
  - Fixed memory leak related to `loading.png` usage.
  - Fixed custom header handling with redirecting URLs in Cordova FileTransfer download API.

## 2.7.4 (2013-06-24)

Rotation/orientation support, redirect support for Cordova's FileTransfer download method, bugfixes.

Features:
  - Cordova FileTransfer download method now follows redirects.
  - Rotation/orientation support.

Bugfixes:
  - Fixed a regularly occurring crash related to camera usage.
  - setSleepDisabled API call works properly now.
  - Fixed startup problems with Galaxy Tab 10.1 device.
  - Fixed crash related to using an input HTML element with type file.
  - Fixed issue with long layer stacks where topmost layer works and is on screen but does not render html content.

## 2.7.3 (2013-06-11)

Support for custom `loading.png` and loading screen color, platform-specific `config.xml` file, `.android.` file extension, bugfixes.

Features:
  - Use `loading.png` from project's `www/` folder if exists.
  - Use loading screen color from project's `config/application.coffee`.
  - Use `config.xml` from project's `www/config.android.xml` if it exists, or from `www/config.xml` if `config.android.xml` is not found.

Changes:
  - Android specific files are now loaded from files with `.android` _before_ their own extension. e.g. `index.android.html` instead of previous implementation of `index.html.android`.

Bugfixes:
  - Fixed a problem with native back button usage.
