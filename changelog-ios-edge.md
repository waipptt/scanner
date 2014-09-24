## Edge versions for AppGyver iOS Native Runtime

This changelog documents features and bugfixes available in **Edge** versions of the AppGyver iOS Native Runtime. They are available to give users access to new features and bugfixes without having to wait for the next **stable** version to pass the Apple App Store approval process. Edge versions can be unstable, so use them with caution – building with Edge versions for production is not adviced.

Read more in the [patch and Edge versions guide](http://academy.appgyver.com/guides/86)!

The changelog for **stable** releases is available [here](https://github.com/AppGyver/scanner/blob/master/changelog-ios.md).

The runtime versions currently in use by each AppGyver component can be found [here](https://github.com/AppGyver/scanner/blob/master/runtime-versions.md)

### 3.5.3-edge1 (2014-09-24)

iOS8 fixes for [#534](https://github.com/AppGyver/steroids/issues/534):
- Updated Cordova submodule to iOS 8 compatibility commit
- Updated hardcoded Cordova plugins for iOS 8 compatibility. See versions [here](https://academy.appgyver.com/categories/7-extending-with-plugins/contents/146-default-plugins).

### 3.5.2-edge1 (2014-09-12)

Bugfixes:
- False success callback was invoked when trying to update a non-preloaded view to drawer (fixes [#438](https://github.com/AppGyver/steroids/issues/438))
- iOS8 fixes:
  - Full drawer support
  - Full modal support

### 3.5.0-edge-p3 (2014-07-01)

Bugfixes:
- Reloading the app while rotated to landscape mode no longer causes the app view to be "squished". Related issue [#389](https://github.com/AppGyver/steroids/issues/389).
- You can now open a modal view directly from Camera's success callback. Related issue [#444](https://github.com/AppGyver/steroids/issues/444).
- Improved error message when the QR code scan is not successful. Related issue [AppGyver/composer/#7](https://github.com/AppGyver/composer/issues/7)
- Fixed bug where the Personal Hotspot bar overlapped status bar and displaced WebView content. Related issue [#393](https://github.com/AppGyver/steroids/issues/393).
- Fixed bug where hiding an initially visible status bar showed yellow backround if Personal Hotspot bar is visible. Related issue [#394](https://github.com/AppGyver/steroids/issues/394).
- Fixed bug where Ad Hoc builds with a hidden status bar caused tabs to be offset upwards. Related issue [#392](https://github.com/AppGyver/steroids/issues/392).

### 3.5.0-edge-p2 (2014-06-17)

Bugfixes:
- Fixed a bug where having more than 5 tabs caused inconsistent behavior. Related issue [#116](https://github.com/AppGyver/steroids/issues/116).
- Fixed a rare crash with the Facebook Cordova plugin.

### 3.5.0-edge-p1 (2014-06-11)

Features:
- The `center` parameter of `steroids.drawers.hide()` now supports non-preloaded WebViews. Related issue [#413](https://github.com/AppGyver/steroids/issues/413).
- [Cordova keyboard plugin](https://github.com/AppGyver/cordova-plugin-keyboard) included.

Bugfixes:
- Fixed a bug where the `KeyboardShrinksView` parameter wasn't working in 3.5.0-edge runtime. Related issue [#404](https://github.com/AppGyver/steroids/issues/404).
- Fixed a bug where the `HideKeyboardFormAccessory` parameter wasn't working in 3.5.0-edge runtime. Related issue [#412](https://github.com/AppGyver/steroids/issues/412).

### 3.5.0-edge (2014-06-05)

Breaking changes:
- SQLite plugin is no longer included by default and must instead be installed via the Build Service as a custom plugin. You can find the plugin we used [here](https://github.com/AppGyver/Cordova-SQLitePlugin).

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

### 3.1.6-edge-p3 (2014-05-20)

- Fixed a bug where modals wouldn't respect `steroids.view.setAllowedRotations()`. Related issue [#313](https://github.com/AppGyver/steroids/issues/313).

### 3.1.6-edge-p2 (2014-05-19)

Bugfixes:
- Fixed a bug where calling `steroids.layers.pop()` in landscape orientation crashed the app. Related issue [#276](https://github.com/AppGyver/steroids/issues/276).
- Fixed a bug where calling `steroids.modal.hideAll()` caused the app to show the "yellow screen of death". Related issue [#218](https://github.com/AppGyver/steroids/issues/218)

### 3.1.6-edge-p1 (2014-05-13)

Fixed a bug where a modal could not be opened from the drawer. Related issue [#291](https://github.com/AppGyver/steroids/issues/291).

### 3.1.6-edge (2014-05-13)

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

