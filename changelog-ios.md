# Changelog for AppGyver Scanner for iOS

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