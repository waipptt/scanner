# Stable AppGyver iOS Native Runtime

This document is for **stable** releases of the iOS Native Runtime, updated when the [AppGyver Scanner app](https://itunes.apple.com/us/app/appgyver-scanner/id575076515?mt=8) running the given runtime version is available for download from the App Store.

In addition, **patch** and **Edge** versions are available via the Build Service to give access to new features and bugfixes before a new stable version has been approved by Apple. Changelog and more information can be found [here](https://github.com/AppGyver/scanner/blob/master/changelog-ios-patch-edge.md).

### 3.1.6-p4 (2014-06-03)

- Fixed a bug where `steroids.layers.push` and `steroids.layers.replace` didn't work from a drawer or from a preloaded view that was not in the layer stack. Related issues [#335](https://github.com/AppGyver/steroids/issues/335) & [#377](https://github.com/AppGyver/steroids/issues/377).
- Fixed a bug where preloads or drawers defined in `application.coffee` were not applied to Ad Hoc builds. Related issue [#369](https://github.com/AppGyver/steroids/issues/369).
- Fixed a bug where `layers.push` called from drawer fired a success callback even though it did nothing. Related issue [#335](https://github.com/AppGyver/steroids/issues/335).
- Fixed a bug where setting a background image to a WebView crashed app on start. Related issue [#368](https://github.com/AppGyver/steroids/issues/368).

## 3.1.6 (2014-05-20)

Several bugfixes, better callbacks for `steroids.layers.popAll`.

Features:
  - No longer display native error message if `steroids.view.setAllowedOrientations` doesn't match allowed orientations set via the Build Service.
  - More and better callbacks to `steroids.layers.popAll`, available in Steroids.js v3.1.10.

Bugfixes:
  - Keyboard that is opened from a drawer WebView no longer stays open after the drawer is closed. Closes [#262](https://github.com/AppGyver/steroids/issues/262).
  - Closing a drawer with the keyboard no longer destroys the target WebView. Closes [#267](https://github.com/AppGyver/steroids/issues/267)
  - Fixed a bug where `steroids.drawer.hide` only work when both left and right drawers were defined. Closes [#268](https://github.com/AppGyver/steroids/issues/268).
  - Steroids.js API calls now function correctly when called via the Cordova `resume` event. Closes [#90](https://github.com/AppGyver/steroids/issues/90).
  - `steroids.layers.popAll()` now remembers root WebView's navigation bar visibility state correctly. Closes [#295](https://github.com/AppGyver/steroids/issues/295).
  - Setting a custom back button immediately after a page is pushed no longer causes overlapping buttons. Closes [#145](https://github.com/AppGyver/steroids/issues/145).
  - Fixed issue where WebView top inset was offset by status bar height after presenting the Cordova Camera. Closes [#296](https://github.com/AppGyver/steroids/issues/296)

### 3.1.5-p4 (2014-05-20)

- Fixed a bug where calling `steroids.layers.pop()` in landscape orientation crashed the app. Related issue [#276](https://github.com/AppGyver/steroids/issues/276).

### 3.1.5-p3 (2014-05-13)

Fixed a bug where a modal could not be opened from the drawer. Related issue [#291](https://github.com/AppGyver/steroids/issues/291).

### 3.1.5-p2 (2014-05-08)

Fixed a bug where hiding the drawer with the keyboard open would destroy the drawer view. Related issue [#267](https://github.com/AppGyver/steroids/issues/267).

### 3.1.5-p1 (2014-05-07)

Fixed a bug where `steroids.drawer.hide` only work when both left and right drawers were defined. Related issue [#268](https://github.com/AppGyver/steroids/issues/268).

## 3.1.5 (2014-05-06)

New drawer, multiple other new features and bugfixes. Please see the [Steroids.js changelog](https://github.com/AppGyver/steroids-js/blob/master/CHANGELOG.md) for the relevant API calls.

Breaking changes:

- Drawer implementation completely redone using the [Mutual Mobile Drawer Controller](https://github.com/mutualmobile/MMDrawerController), new drawers require Steroids.js v3.1.9. Please see the [Drawer API docs]( http://docs.appgyver.com/en/edge/steroids_Steroids%20Native%20UI_steroids.drawers_index.md.html#steroids.drawers) for more information. Closes [#126](https://github.com/AppGyver/steroids/issues/126), [#123](https://github.com/AppGyver/steroids/issues/123) and [#118](https://github.com/AppGyver/steroids/issues/118).

Features:

- All locales are listed by default in app settings. This makes Steroids apps use the OS language instead of only English. Closes [#198](https://github.com/AppGyver/steroids/issues/198).
- Modal can be opened with navigation bar already open. Available with Steroids.js 3.1.9. Closes [#220](https://github.com/AppGyver/steroids/issues/220).
- All open modals can now be closed with a single API call (available as a secret feature `steroids.modal.closeAll` in Steroids.js 3.1.9). Closes [#218](https://github.com/AppGyver/steroids/issues/218).
- Application state (preloaded WebViews, tabs, modals) etc. can now be fetched (available as a secret feature, `steroids.getApplicationState()` in Steroids.js 3.1.9). Closes [#205](https://github.com/AppGyver/steroids/issues/205).
- Initial native UI events implemented (available as a secret feature in Steroids.js 3.1.9). Closes [#148](https://github.com/AppGyver/steroids/issues/148) and [#117](https://github.com/AppGyver/steroids/issues/117).
- Allow an untouched image to be used for navigation bar buttons. Available with Steroids.js 3.1.9. Closes [#130](https://github.com/AppGyver/steroids/issues/130).

Bugfixes:

- Fixed bug where setting `steroids.statusBar.onTap` event listener messed up status bar appearance. Closes [#260](https://github.com/AppGyver/steroids/issues/260).
- `steroids.screen.freeze` no longer makes tab bar background go black.
- Calling `modal.show()` and `navigationBar.show()` at the same time now displays navigation bar correctly. Closes [#261](https://github.com/AppGyver/steroids/issues/261).
- Calling `layers.pop()` after calling `layers.push({navigationBar:false})` now reshows navigation bar correctly. Closes [#221](https://github.com/AppGyver/steroids/issues/221) and [#109](https://github.com/AppGyver/steroids/issues/109).
- Setting `KeyboardShrinksView=true` in `config.ios.xml` no longer shows yellow behind the keyboard. Closes [#219](https://github.com/AppGyver/steroids/issues/219).
- Ongoing call or personal hotspot banner no longer offsets the WebView. Closes [#217](https://github.com/AppGyver/steroids/issues/217).
- Fixed bug where apps with no tab bar enabled rendered the navigation bar under the status bar. Closes [#212](https://github.com/AppGyver/steroids/issues/212).
- Fixed bug where showing a modal from landscape caused underlying WebView to go back to portrait orientation. Closes [#199](https://github.com/AppGyver/steroids/issues/199).
- Fixed a bug where pushing a WebView on app load and going back caused a grey banner to show. Closes [#144](https://github.com/AppGyver/steroids/issues/144).
- Fixed a bug where `steroids.layers.replace` didn't resize a short WebView correctly. Closes [#115](https://github.com/AppGyver/steroids/issues/115).
- Fixed a crash when rotating app from landscape to portrait. Closes [#86](https://github.com/AppGyver/steroids/issues/86).

##3.1.4 (2014-04-03)

Multiple new features and bugfixes to native UI.

Breaking changes:

- Hardcoded Google Analytics plugin removed. If including the plugin manually, please use the AppGyver fork at https://github.com/AppGyver/GAPlugin which has been fixed to work for multiple WebViews.
- Hardcoded CouchDB support removed.
- Increased minimum iOS version requirement from 6.0 to 7.0.

Features (see [Steroids.js v3.1.8 changelog](https://github.com/AppGyver/steroids-js/blob/master/CHANGELOG.md#318-2014-04-03) for the relevant API calls):

- Support for updating the currently active tab bar tab. Closes [#196](https://github.com/AppGyver/scanner/issues/196)
- Support for adding tap event listener to the status bar. Closes [#47](https://github.com/AppGyver/scanner/issues/47)
- Support for showing/hiding the keyboard input accessory bar. Closes [#200](https://github.com/AppGyver/scanner/issues/200).
- Support for a fully custom back button in navigation bar. Closes [#124](https://github.com/AppGyver/scanner/issues/124).
- Support for using the navigation bar in a modal window. Closes [#49](https://github.com/AppGyver/scanner/issues/49).
- Support for showing multiple modals on top of each other. Closes [#7](https://github.com/AppGyver/scanner/issues/7).
- Proper callbacks for animation start/end. Closes [#195](https://github.com/AppGyver/scanner/issues/195).
- Support for using a navigation bar in modal windows.
- Support for programmatically showing `loading.html`. Closes [#149](https://github.com/AppGyver/scanner/issues/149).
- Support for showing multiple modals on top of each other. Closes [#7](https://github.com/AppGyver/scanner/issues/7)
- New `DisableDoubleTapToFocus` preference in `config.ios.xml` disables the default WebView behavior where double-tapping on the screen scrolls the content. Closes [#144](https://github.com/AppGyver/scanner/issues/144).
- New `ViewIgnoresStatusBar` preference in `config.ios.xml` will make the WebView start under the status bar instead of below it. Closes [#62](https://github.com/AppGyver/scanner/issues/62).
- Sliding animations now work in landscape orientation.

Bugfixes:

- Fixed several UI alignment issues introduced with iOS 7 UI updates. Closes [#194](https://github.com/AppGyver/scanner/issues/194), [#90](https://github.com/AppGyver/scanner/issues/90), [#98](https://github.com/AppGyver/scanner/issues/98), [#133](https://github.com/AppGyver/scanner/issues/133) and [#194](https://github.com/AppGyver/scanner/issues/194).
- Fixed a crash when updating the tab bar with fewer tabs that exist on the screen. Closes [#193](https://github.com/AppGyver/scanner/issues/193).
- Fixed a bug where updating the tab bar wouldn't update the "selected image" of the tab. Closes [#192](https://github.com/AppGyver/scanner/issues/192).
- Animations will now correctly use the WebView background color. Closes [#12](https://github.com/AppGyver/scanner/issues/12).
- Fixed duplicate symbols when using the CouchBase plugin. Closes [#197](https://github.com/AppGyver/scanner/issues/197).
- Fixed crash when using tabs without titles in build service Ad Hoc builds
- When using the `HideKeyboardFormAccessoryBar` preference in `config.ios.xml`, the keyboard background is no longer transparent on iOS 7.1. Closes [#176](https://github.com/AppGyver/scanner/issues/176).

Changes:

- Disabled Crittercism crash reporting in Ad Hoc and App Store builds.

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
