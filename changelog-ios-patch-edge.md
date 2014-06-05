## Patch/Edge versions for AppGyver iOS Native Runtime

This changelog documents features and bugfixes available in **patch** and **Edge** versions of the AppGyver iOS Native Runtime. They are available to give users access to new features and bugfixes without having to wait for the next **stable** version to pass the Apple App Store approval process. Read more in the [patch and Edge versions guide](http://academy.appgyver.com/guides/86)!

The changelog for **stable** releases is available [here](https://github.com/AppGyver/scanner/blob/master/changelog-ios.md).

The runtime versions currently in use by each AppGyver component can be found [here](https://github.com/AppGyver/scanner/blob/master/runtime-versions.md)

### 3.5.0 (EDGE, 2014-06-05)

Breaking changes:
- SQLite plugin is no longer included by default and must instead be installed via the Build Service.

Changes:
- Cordova version updated to 3.5.0. Related issue [#197](https://github.com/AppGyver/steroids/issues/197).

Bugfixes:
- Fixed a bug where modals could not be opened from drawers. Related issue [#291](https://github.com/AppGyver/steroids/issues/291).
- Fixed a bug where `steroids.modal.hideAll` showed a yellow screen. Related issue [#218](https://github.com/AppGyver/steroids/issues/218).
- Fixed a bug where `steroids.layers.pop()` crashed the app when called in Landscape mode. Related issue [#276](https://github.com/AppGyver/steroids/issues/276).
- Fixed a bug where modal views didn't respect `steroids.view.setAllowedOrientations`. Related issue [#313](https://github.com/AppGyver/steroids/issues/313).
- Fixed a bug where an URL with a hash character broke `steroids.layers.push` when using the File protocol. Related issue [#206](https://github.com/AppGyver/steroids/issues/206).
- Fixed a bug where `steroids.modal.hide` only worked when called from the modal WebView itself. Related issue [#315](https://github.com/AppGyver/steroids/issues/315).
- Fixed a bug where drawer contents overlapped status bar. Related issue [#273](https://github.com/AppGyver/steroids/issues/273).
- Fixed a bug where setting a background image crashed app on restart. Related issue [#368](https://github.com/AppGyver/steroids/issues/368).
- Fixed a bug where `steroids.layers.push` and `steroids.layers.replace` didn't work from a drawer or from a preloaded view that was not in the layer stack. Related issues [#335](https://github.com/AppGyver/steroids/issues/335) & [#377](https://github.com/AppGyver/steroids/issues/377).
- Fixed a bug where preloads or drawers defined in `application.coffee` were not applied to Ad Hoc builds. Related issue [#369](https://github.com/AppGyver/steroids/issues/369).
- Fixed a bug where `layers.push` called from drawer fired a success callback even though it did nothing. Related issue [#335](https://github.com/AppGyver/steroids/issues/335).
- Fixed a bug where if the back button is tapped while a new view is still loading, the navigation bar title and button change into the the title and button of the new layer. Related issue [#401](https://github.com/AppGyver/steroids/issues/401).
- Fixed a crash when opening navigator.notification.alert and then popping the current layer. Related issue [#187](https://github.com/AppGyver/steroids/issues/187).
- Fixed a bug where calling `steroids.drawers.show` for the opposite edge caused the other drawer to open but drawer view not update. Related issue [#402](https://github.com/AppGyver/steroids/issues/402).
- Fixed a bug where stopping the swipe-to-go-back gesture before it is finished broke native navigation bar. Related issue [#120](https://github.com/AppGyver/steroids/issues/120).

### 3.1.6-p4 (2014-06-03)

- Fixed a bug where `steroids.layers.push` and `steroids.layers.replace` didn't work from a drawer or from a preloaded view that was not in the layer stack. Related issues [#335](https://github.com/AppGyver/steroids/issues/335) & [#377](https://github.com/AppGyver/steroids/issues/377).
- Fixed a bug where preloads or drawers defined in `application.coffee` were not applied to Ad Hoc builds. Related issue [#369](https://github.com/AppGyver/steroids/issues/369).
- Fixed a bug where `layers.push` called from drawer fired a success callback even though it did nothing. Related issue [#335](https://github.com/AppGyver/steroids/issues/335).
- Fixed a bug where setting a background image to a WebView crashed app on start. Related issue [#368](https://github.com/AppGyver/steroids/issues/368).

### 3.1.6-p3 (EDGE, 2014-05-20)

- Fixed a bug where modals wouldn't respect `steroids.view.setAllowedRotations()`. Related issue [#313](https://github.com/AppGyver/steroids/issues/313).

### 3.1.5-p4 (2014-05-20)

- Fixed a bug where calling `steroids.layers.pop()` in landscape orientation crashed the app. Related issue [#276](https://github.com/AppGyver/steroids/issues/276).

### 3.1.6-p2 (EDGE, 2014-05-19)

Bugfixes:
- Fixed a bug where calling `steroids.layers.pop()` in landscape orientation crashed the app. Related issue [#276](https://github.com/AppGyver/steroids/issues/276).
- Fixed a bug where calling `steroids.modal.hideAll()` caused the app to show the "yellow screen of death". Related issue [#218](https://github.com/AppGyver/steroids/issues/218)

### 3.1.6-p1 (EDGE, 2014-05-13)

Fixed a bug where a modal could not be opened from the drawer. Related issue [#291](https://github.com/AppGyver/steroids/issues/291).

### 3.1.5-p3 (2014-05-13)

Fixed a bug where a modal could not be opened from the drawer. Related issue [#291](https://github.com/AppGyver/steroids/issues/291).

### 3.1.6 (EDGE, 2014-05-13)

Features:
  - No longer display native error message if `steroids.view.setAllowedOrientations` doesn't match allowed orientations set via the Build Service.
  - More and better callbacks to `steroids.layers.popAll`, available in Steroids.js v3.1.10.
  - Support for the new JSCoreBridge, used by default in Steroids.js v3.1.10.

Bugfixes:
  - Keyboard that is opened from a drawer WebView no longer stays open after the drawer is closed. Will close [#262](https://github.com/AppGyver/steroids/issues/262).
  - Closing a drawer with the keyboard no longer destroys the target WebView. Will close [#267](https://github.com/AppGyver/steroids/issues/267)
  - Fixed a bug where `steroids.drawer.hide` only work when both left and right drawers were defined. Will close [#268](https://github.com/AppGyver/steroids/issues/268).
  - Steroids.js API calls now function correctly when called via the Cordova `resume` event. Will close [#90](https://github.com/AppGyver/steroids/issues/90).
  - `steroids.layers.popAll()` now remembers root WebView's navigation bar visibility state correctly. Will close [#295](https://github.com/AppGyver/steroids/issues/295).
  - Setting a custom back button immediately after a page is pushed no longer causes overlapping buttons. Will close [#145](https://github.com/AppGyver/steroids/issues/145).
  - Fixed issue where WebView top inset was offset by status bar height after presenting the Cordova Camera. Will close [#296](https://github.com/AppGyver/steroids/issues/296)

### 3.1.5-p2 (2014-05-08)

Fixed a bug where hiding the drawer with the keyboard open would destroy the drawer view. Related issue [#267](https://github.com/AppGyver/steroids/issues/267).

### 3.1.5-p1 (2014-05-07)

Fixed a bug where `steroids.drawer.hide` only work when both left and right drawers were defined. Related issue [#268](https://github.com/AppGyver/steroids/issues/268).
