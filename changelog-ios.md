# Changelog for AppGyver Scanner for iOS

##3.1.3 (2014-03-06)

Features:
 - Support for setting tab bar badges, see [`steroids.tabBar.update`](http://docs.appgyver.com/en/edge/steroids_Steroids%20Native%20UI_steroids.tabBar_tabBar.update.md.html#steroids.tabBar.update)
 - Support for programmatically selecting a tab, see [`steroids.tabBar.selectTab`](http://docs.appgyver.com/en/edge/steroids_Steroids%20Native%20UI_steroids.tabBar_tabBar.selectTab.md.html#steroids.tabBar.selectTab)
 - [`steroids.layers.replace`](http://docs.appgyver.com/en/edge/steroids_Steroids%20Native%20UI_Steroids.layers_layers.replace.md.html#steroids.layers.replace) now works for WebViews already in the layer stack. This allows developers to circumvent an issue with calling `steroids.layers.popAll()` in a non-visible tab – see the [GitHub issue](https://github.com/AppGyver/scanner/issues/155) for more details.
 - Support for hiding and showing a modal without an animation (see the [`steroids.modal`](http://docs.appgyver.com/en/edge/steroids_Steroids%20Native%20UI_Steroids.modal_index.md.html#steroids.modal) API docs).

Bugfixes:
 - Fixed compatibility issues with some plugins that include a static library (`.a` extension)

##3.1.2 (2014-02-10)

Support for updating navigation bar contents and hiding and showing splashscreen programmatically and several bugfixes.

Features:
  - Support for updating navigation bar contents (title, title image, buttons) per webview ([#108](https://github.com/AppGyver/scanner/issues/108), [#18](https://github.com/AppGyver/scanner/issues/18), [#37](https://github.com/AppGyver/scanner/issues/37))
  - Support for config.ios.xml option to disable iOS7 pop gesture ([#21](https://github.com/AppGyver/scanner/issues/21))
  - Support for config.ios.xml option to disable tint coloring for unselected tab bar icons
  - Support for config.ios.xml option to disable automatic hiding of splashscreen during application start
  - Support for showing and hiding splashscreen programmatically ([#41](https://github.com/AppGyver/scanner/issues/41))
  - Support for showing and hiding navigation bar with animation

Changes:
  - Tab bar selected icon tint color now also affects the selected icon title tint color ([#116](https://github.com/AppGyver/scanner/issues/116))
  - [OAuth.io plugin](https://oauth.io/) included in the App Store Scanner (but not Simulator or custom builds from the Build Service), causes a global `OAuth` object to be defined in every WebView.

Bugfixes:
  - Fixed [the Issue #101](https://github.com/AppGyver/scanner/issues/101) steroids.layers.replace breaks steroids.layer.push
  - Fixed [the Issue #105](https://github.com/AppGyver/scanner/issues/105) calling steroids.navigationBar.show() multiple times on preloaded views pushes WebView content downwards
  - Fixed [the Issue #9](https://github.com/AppGyver/scanner/issues/9) native keyboard toolbar being affected by navigation bar appearance attributes
  - Fixed [the Issue #107](https://github.com/AppGyver/scanner/issues/107) showing a preloaded modal multiple times when the status bar is active pushes the modal's content downwards


##3.1.1 (2013-12-19)

All the Cordova core plugins now included, support for updating tab titles and icons, several bugfixes.

Features:
  - Previously missing Cordova core plugins, File-Transfer and Console, are now included by default.
  - Support for updating tab titles and icons to new ones with steroids.tabBar.update.

Changes:
  - Adds failure callbacks to steroids.tabBar.show and steroids.tabBar.hide, if another transition is in progress at the same time.
  - Cordova.js can now be downloaded only from http://localhost/cordova.js.

Bugfixes:
  - Fixed camera core plugin.
  - Fixed modal webview html content starting from under the statusbar instead of below status bar.
  - Fixed steroids.layers.replace to replace layers correctly and to release old layers correctly.

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
