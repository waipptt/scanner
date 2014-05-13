## Build Service Patch/Edge Changelog for AppGyver iOS Native Runtime

This changelog documents features and bugfixes available in **patch** and **edge** versions of the AppGyver iOS Native Runtime. They are available to give users access to new features and bugfixes without having to wait for the Apple App Store approval process. The runtime versions currently in use by each AppGyver component can be found [here](https://github.com/AppGyver/scanner/blob/master/runtime-versions.md)

The changelog for stable releases (i.e. `3.1.5`) is available [here](https://github.com/AppGyver/scanner/blob/master/changelog-ios.md).

Patch versions (`-pX`) are always non-breaking and generally include bugfixes. The fixes introduced in patch versions will always be included in the next stable, non-patch version of the runtime (and documented accordingly in the stable version changelog).

Edge versions include features that are upcoming in the next stable release. They work with the [Steroids.js `next` branch](https://github.com/AppGyver/steroids-js/tree/next), and if documentation is available, it can be found in the [Edge API docs](docs.appgyver.com/en/edge/index.html).

### 3.1.6-p1 (EDGE, 2014-05-13)

Fixed a bug where a modal could not be opened from the drawer. Related issue [#291](https://github.com/AppGyver/steroids/issues/291).

### 3.1.5-p3 (2014-05-13)

Fixed a bug where a modal could not be opened from the drawer. Related issue [#291](https://github.com/AppGyver/steroids/issues/291).

### 3.1.6 (EDGE, 2014-05-13)

Breaking changes:
  - All Steroids API calls are transferred to the new JSCoreBridge, available in Steroids.js v3.1.10 (`next` branch). Old Steroids.js versions no longer work with v3.1.6.

Features:
  - No longer display native error message if `steroids.view.setAllowedOrientations` doesn't match allowed orientations set via the Build Service.
  - More and better callbacks to `steroids.layers.popAll`.

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
