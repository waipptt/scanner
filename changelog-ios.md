# Changelog for AppGyver Scanner for iOS

##3.1.0 (2013-12-04)

Cordova 3.1.0 upgrade, bugfixes for status bar and steroids.layers methods.

Features:
  - Cordova support upgraded to 3.1.0
  - Plugins included in App Store Scanner: Cordova core plugins (excluding File-Transfer and Console), BarcodeScanner, Google Analytics, SQLite plugin
  - Support for hiding navigation bar when replacing layers
  - Initial webviews of the application have a preload identifier based on their 'location' attribute
  - Support for removing a preloaded layer from memory with steroids.views.WebView.prototype.unload
  - Support for hiding and showing the tab bar for tabbed applications
  - Support for hiding and showing the status bar. Includes changing the status bar style dynamically
  - Support for new status bar style 'light' 

Changes:
  - BREAKING: the following plugins are no longer included by default:
      - File-Transfer
      - Calendar Plugin
      - FacebookConnect Plugin
      - PushNotification Plugin
      - MapKitView
      - Flurry Plugin
  - To have working cordova plugins javascript loading, cordova.js must be loaded from src="http://localhost/cordova.js" or "/cordova.js" if window.location is already localhost
  - config*.xml files need to be updated to a new format and contents
  - Cordova plugins are expected to be written in an ARC compatible manner. Some old plugins will not work without having -objc-no-arc in their plugin.xml
  - Plugins are no longer configured through project config*.xml files. They are automatical now.
  - Plugin js files for plugins without the new element in their plugin.xml can have their js library loaded manually through the localhost path configured in their element target attribute
  - Support for overriding back button without adding any actual buttons

Bugfixes:
  - Fix status bar being always on in Appstore and Adhoc builds
  - Fix steroids.layers.replace moving the webview to be off by one(1) status bar on screen.
  - Fix steroids.layers.popAll disabling all native transitions if called while a modal is open
  - Fix tab bar selected tab tint color being always blue
  - Fix status bar being always on during modal views.
  - Fix status bar style not having any effect.
  - Fix crashing when pushing and popping layers really fast in sequence

## 2.7.9 (2013-10-12)

iOS7 stabilization and Native UI improvements.

Features (requires [Steroids.js](https://github.com/appgyver/steroids-js) v2.7.10):
  - Custom images as navigation bar and tab bar background 
  - Support for multiple buttons in multiple locations inside the navigation bar.
  - Support for images as navigaton bar buttons.

Changes:
  - Removed hardcoded GenericPush plugin in favor of build service plugin integration.

Bugfixes:
  - Fixed SVG/CSS mimetypes in localhost.
  - Fixed navigation bar back button arrow tint color not being affected by `steroids.config.navigationBar.buttonTintColor`.
  - Fixed status bar rendering with drawer.
  - Fixed crashes introduced by v2.7.8.
  - Fixed most of the memory leaks introduced by iOS7.

## 2.7.8 (2013-09-28)

Full iOS7 support.

Updates:
  - Updated integrated Facebook plugin to https://github.com/phonegap/phonegap-facebook-plugin.
  - Updated integrated SQLite plugin to https://github.com/pgsqlite/PG-SQLitePlugin-iOS.

## 2.7.7 (2013-09-10)

Fixed problems when running Steroids apps built with the iOS6 SDK on iOS7 devices.

## 2.7.6 (2013-07-22)

Bugfixes for User Agent and drawers.

Bugfixes:
  - Fixed an issue with User Agent not updating after the app is updated from the App Store.
  - Fixed a rare issue with drawers where drawer would be rendered black until user touches screen.

## 2.7.5 (2013-07-17)

Bugfixes for `window.postMessage`

Bugfixes:
  - Fixed an issue with `window.postMessage` related to preloaded WebViews.

## 2.7.4 (2013-07-08)

User agent differentiates between Scanner and stand-alone apps.

Features:
  - User agent now includes string "Scanner" if running inside Scanner app, otherwise includes string "StandAlonePackage"

## 2.7.3 (2013-07-01)

Context menu is now styled with Topcoat, bugfixes.

Features:
  - New context menu with Topcoat styles

Bugfixes:
  - Fixed drawer showing up on the background of certain animations.
  - Fixes the iOS Simulator build not supporting the iPhone5 Simulator device properly.

## 2.7.2 (2013-06-19)

Turned autoloading feature into a setting.

Features:
  - New option inside Settings.app to turn on autoloading of previous app when Scanner is opened.

Changes:
  - Autoloading of previous app is now disabled by default.
