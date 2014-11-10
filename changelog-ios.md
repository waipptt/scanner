# Stable AppGyver iOS Native Runtime

This document contains the release notes for **stable** releases of the iOS Native Runtime. To see which version of the native runtime each AppGyver component is running, see the [native runtime versions](https://github.com/AppGyver/scanner/blob/master/runtime-versions.md) document. A non-patch version is always accompanied by a new App Store version of the [AppGyver Scanner for iOS](https://itunes.apple.com/us/app/appgyver-scanner/id575076515?mt=8).

**Patch** versions are available via the Build Service to give access to new bugfixes before a new stable version has been approved by Apple – read more in the [native runtime Patch Version guide](https://academy.appgyver.com/categories/2-tooling/contents/119-native-runtime-patch-versions).

For early access to new features and more complex bugfixes, **Edge** versions are available via the Build Service. Read the [native runtime Edge version guide](https://academy.appgyver.com/categories/2-tooling/contents/86-native-runtime-edge-versions) for more information, and see the [changelog](https://github.com/AppGyver/scanner/blob/master/changelog-ios-edge.md) for release notes.

## 4.0.2 (TODO)

Fixes an issue with noticing changes in filepaths for Steroids 2.

## 4.0.1 (2014-11-04): Support for iPhone 6 and iPhone 6+

**Breaking changes:**
- Native CSS is now read from `ios.css` instead of `default.css`. Closes [#558](https://github.com/AppGyver/steroids/issues/558)

Features:
- Support for iPhone6 and iPhone 6+
  - Requires new graphical assets being defined in the Build Service
- Tab Items use the `id` defined in `application.coffee` for Native CSS.
- Updated cordova-plugin-dialogs to 0.2.10.

Bugfixes:
- API calls for `setStyle` properly discard inline styles set previously with `setStyle`
- `steroids.screen.dismissAlert` now triggers Cordova success callbacks.
- Preloaded drawers were broken after dismissing Initial View for the second time (fixes [#536](https://github.com/AppGyver/steroids/issues/536)).
- External keyboard caused background of software keyboard being displayed (fixes [#447](https://github.com/AppGyver/steroids/issues/447)).
- Preloaded WebViews are now discarded when displaying the Initial View and loaded again when hiding the Initial View (fixes [#572](https://github.com/AppGyver/steroids/issues/572), [#585](https://github.com/AppGyver/steroids/issues/585)).
- Focusing on an input caused an input field being scrolled out of the visible view and it did not come back even when started typing.
- WebView was pushed too far up if an input was at the bottom of the screen and Tab Bar was visible (fixes [#567](https://github.com/AppGyver/steroids/issues/567)).
- iPad on landscape-only builds displayed a black splashscreen. Closes [#158](https://github.com/AppGyver/steroids/issues/158)
- In a landscape-only build on iPhone 6+, adding a style class to the navigation bar makes it invisible [#559](https://github.com/AppGyver/steroids/issues/559)

Known issues:
- Splashscreen on landscape-only builds is displayed wrong [#599](https://github.com/AppGyver/steroids/issues/599)
- Portrait splashscreen is rotated to landscape if device orientation changes while showing the splashscreen [#594](https://github.com/AppGyver/steroids/issues/594)
- `steroids.screen.rotate` fires false success callback after trying to rotate to an unallowed direction [#598](https://github.com/AppGyver/steroids/issues/598)
- `steroids.screen.dismissAlert` is broken after the update of cordova-plugin-dialogs to 0.2.10.
- In a landscape-only build in iOS8 opening the BarCode Scanner renders the screen half gray [#560](https://github.com/AppGyver/steroids/issues/560)
- Landscape-only builds crash when Cordova Camera is used [#455](https://github.com/AppGyver/steroids/issues/455)

## 4.0.0 (2014-10-10): Native CSS with Pixate

Native UI styling with CSS syntax (Pixate). Replaced the default Cordova keyboard plugin with Ionic's keyboard plugin. A lot of iOS8 + Cordova compatibility fixes.

**Breaking Changes:**
- Switched included Cordova Keyboard plugin to the
  [Ionic Keyboard plugin](https://github.com/driftyco/ionic-plugins-keyboard/)
  (fixes [#550](https://github.com/AppGyver/steroids/issues/550))
- Keyboard settings can no longer be configured app-wide in `config.ios.xml`.

Features:
- Native UI can be styled with CSS syntax (Pixate).
  - Styles can be provided from `dist/native-styles/default.css`
  - API calls for styling Native UI with CSS:
    - API methods `setStyle` and `setClass` for Tab Bar and Navigation Bar
    - API method `setTheme` to apply a set of styles at once
- `steroids.screen.dismissNextAlert` to dismiss the next appearing alert (intended for test automation)
- `steroids.view.navigationBar.tapButton` to tap a specified navigation bar button (intended for test automation)

Bugfixes:
- iOS8 + Cordova compatibility fixes that close [#534](https://github.com/AppGyver/steroids/issues/534):
  - Updated Cordova submodule to iOS8 compatibility commit
  - Updated hardcoded Cordova plugins for iOS 8 compatibility. See versions [here](https://academy.appgyver.com/categories/7-extending-with-plugins/contents/146-default-plugins).
- PreviewFileView didn't display pdf on iOS8 (fixes [#528](https://github.com/AppGyver/steroids/issues/528))
- If called from modal, navigator.camera.getPicture closed the modal after it's callbacks (fixes [#465](https://github.com/AppGyver/steroids/issues/465))
- Allow `steroids.layers.replace` to be used even when the target view is in the layer stack (fixes [#411](https://github.com/AppGyver/steroids/issues/411))
- iOS 8 location services caused a "legacy on-demand authorization" error
  (fixes [#544](https://github.com/AppGyver/steroids/issues/544))
- Opening the Photo Library caused a crash on iOS 8.
- Text area lost focus and had other erratic behaviour when orientation was changed
  while having the keyboard open. (fixes [#467](https://github.com/AppGyver/steroids/issues/467))
- Fixed typo in Drawer options (strechDrawer -> stretchDrawer)

Known issues:
- In a landscape-only build on iPhone 6+, adding a style class to the navigation bar makes it invisible [#559](https://github.com/AppGyver/steroids/issues/559)
- In a landscape-only build in iOS8 opening the BarCode Scanner renders the screen half gray [#560](https://github.com/AppGyver/steroids/issues/560)
- Landscape-only builds crash when Cordova Camera is used [#455](https://github.com/AppGyver/steroids/issues/455)

## 3.5.2 (2014-09-22)

Minor bugfixes and fixes to iOS8 compatibility.

Bugfixes:
- Tab alignment which was broken in iOS 7.0 has now been confirmed to be fixed. Closes [#84](https://github.com/AppGyver/steroids/issues/84).
- Changing navbar appearance more than once causes navbar to not update its appearance before the navbar is visible on screen on iOS7.1
- False success callback was invoked when trying to update a non-preloaded view to drawer. Closes [#438](https://github.com/AppGyver/steroids/issues/438).
- iOS8 SDK was used when building the Scanner. This fixes the bug with yellow drawers experienced with iOS8. (Build Service has also been updated to use the iOS8 SDK, so all 3.5.1 and 3.5.2 builds are iOS8 compatible)

Known issues:
- In iOS8, taking a screenshot and scrolling clears all webview content due to Apple's base64 bug
- In iOS8, the keyboard accessory bar can not (at least currently) be disabled because of the new predictive text feature in iOS8
- In iOS8, `previewFileView` does not work correctly. Issue [#528](https://github.com/AppGyver/steroids/issues/528).

## 3.5.1 (2014-08-22)

The Rotation API used by Steroids was completely rewritten, initial support for iOS8 and several bugfixes.

Features:
- Initial support for iOS8. Closes [#396](https://github.com/AppGyver/steroids/issues/396)
- Added `waitTransitionEnd: true` parameter to `steroids.modal.show` to make it possible to force modal to wait for `layers.push` or similar to complete before showing the modal.
- Rewrite of rotation API, new methods `steroids.screen.setAllowedRotations` (deprecates `steroids.view.setAllowedRotations`). Closes [#160](https://github.com/AppGyver/steroids/issues/160), [#250](https://github.com/AppGyver/steroids/issues/250), [#314](https://github.com/AppGyver/steroids/issues/314), [#317](https://github.com/AppGyver/steroids/issues/317), [#319](https://github.com/AppGyver/steroids/issues/319), [#320](https://github.com/AppGyver/steroids/issues/320), [#323](https://github.com/AppGyver/steroids/issues/323), [#341](https://github.com/AppGyver/steroids/issues/341), [#395](https://github.com/AppGyver/steroids/issues/395), [#405](https://github.com/AppGyver/steroids/issues/405) & [#455](https://github.com/AppGyver/steroids/issues/455).

Bugfixes:
- Fixed a bug where WebView height did not take navigationBar into account. Closes [#275](https://github.com/AppGyver/steroids/issues/275).
- Fixed a bug where dismissing InitialView with status bar would render the navigationBar wonky during the animation. Closes [#321](https://github.com/AppGyver/steroids/issues/321).
- Fixed a bug where using a malformed WebView in the WebView preloads array would cause all WebViews in the app to appear blank. Closes [#322](https://github.com/AppGyver/steroids/issues/322).
- Fixed a bug where `steroids.navigationBar.setAppearance` would not change the `buttonTintColor` of existing buttons. Closes [#397](https://github.com/AppGyver/steroids/issues/397).
- Fixed a bug where calling `steroids.initialView.dismiss` after layers have been pushed results in brief yellow screen. Closes [#427](https://github.com/AppGyver/steroids/issues/427).
- Fixed a bug where a modal could not be opened from the onSuccess callback of Cordova Camera. Closes [#444](https://github.com/AppGyver/steroids/issues/444).

## 3.5.0 (2014-07-14)

Updated Cordova version from v3.1 to v3.5, added new API's for hiding all modals and replacing drawers, tons of bugfixes.

Breaking changes:
- Removed SQLite plugin from project default plugins. To use the SQLite plugin now it must be manually included through Build Service.

Features:
- Updated Cordova to match 3.5.0 features. Closes [#197](https://github.com/AppGyver/steroids/issues/197).
- Updated all hardcoded plugins to latest versions
- Configurable initial view that can be shown before actual app starts
- API to replace tabs with totally new tabs with `steroids.tabs.replace`. Closes [#280](https://github.com/AppGyver/steroids/issues/280) and [#281](https://github.com/AppGyver/steroids/issues/281).
- API to hide all modals with `steroids.modal.hideAll`. Closes [#218](https://github.com/AppGyver/steroids/issues/218).
- Non-preloaded WebViews can now be used as drawers. Closes [#270](https://github.com/AppGyver/steroids/issues/270).
- `steroids.drawers.hide` now allows non-preloaded WebViews to be used as new centers. Closes  [#413](https://github.com/AppGyver/steroids/issues/413)
- More informative error message when QR code scanning was unsuccessful. Closes [#340](https://github.com/AppGyver/steroids/issues/340).

Bugfixes:
- Fixed a bug where the `KeyboardShrinksView` parameter wasn't working in the 3.5.0-edge runtime. Closes issue [#404](https://github.com/AppGyver/steroids/issues/404).
- Fixed a bug where the cancellation of the iOS7 native pop gesture would cause the app to break. Closes issue [#120](https://github.com/AppGyver/steroids/issues/120).
- Fixed a bug where calling `steroids.drawers.show` for the opposite edge when a drawer was open would cause the other drawer to open but for the drawer view not to update. Closes issue [#402](https://github.com/AppGyver/steroids/issues/402).
- Fixed a bug where drawer content would be overlapped by the status bar. Closes issue [#273](https://github.com/AppGyver/steroids/issues/273).
- Fixed a bug where `steroids.modal.show` could not be called from a drawer. Closes issue [#291](https://github.com/AppGyver/steroids/issues/291).
- Fixed a bug where modals would not respect orientations set with `steroids.view.setAllowedOrientations`. Closes issue [#313](https://github.com/AppGyver/steroids/issues/313).
- Fixed a bug where `steroids.modal.hide` would not work when called from anywhere else than the modal. Closes issue [#315](https://github.com/AppGyver/steroids/issues/315).
- Fixed a bug where iPad landscape-only builds would show the portrait splashscreen for a second during startup. Closes issue [#328](https://github.com/AppGyver/steroids/issues/328).
- Fixed a bug where the navigation bar border would be positioned incorrectly in landscape apps.
- Fixed a bug where in landscape-only iPad apps would show a half empty view on app reload. Closes issue [#389](https://github.com/AppGyver/steroids/issues/389).
- Fixed a bug where calling `steroids.layers.pop` in an landscape-only app would crash the app. Closes issue [#276](https://github.com/AppGyver/steroids/issues/276).
- Fixed a bug where alerts would crash if dismissed after the WebView that called the alert had been destroyed. Closes issue [#187](https://github.com/AppGyver/steroids/issues/187).
- Fixed a bug where using alerts would crash the iOS simulator
- Fixed a bug where the app would freeze after calling `steroids.view.setAllowedRotations`
- Fixed a bug where during a period of low memory warnings scanning another app would display yellow screen
- Fixed a bug where navigation bar settings would wrongly transfer when opening a new view with different navigation bar settings but pressing the back button quickly enough would cause the original view to receive the navigation bar settings of the view that was going to be pushed. Closes issue [#401](https://github.com/AppGyver/steroids/issues/401).
- Fixed a bug where preload array and drawers configurations in `application.coffee` would not persist when building Ad Hoc builds. Closes issue [#369](https://github.com/AppGyver/steroids/issues/369).
- Fixed a bug where popping a layer would cause layout issues when the body element was shorter than the screen
- Fixed a bug where `steroids.layers.replace` and `steroids.layers.push` would not work from a preloaded view not in the layer stack. Closes issue [#377](https://github.com/AppGyver/steroids/issues/377).
- Fixed a bug where using `steroids.layers.push` broke when trying to push a URL with a hash while using File Protocol. Closes issue [#206](https://github.com/AppGyver/steroids/issues/206).
- Fixed a faulty success callback when calling `steroids.layers.push` incorrectly from inside a drawer. Closes issue [#335](https://github.com/AppGyver/steroids/issues/335).
- Fixed a bug where calling `steroids.view.setBackgroundImage` would crash the app on restart or when closing a layer with `steroids.layers.pop`. Closes issue [#368](https://github.com/AppGyver/steroids/issues/368).
- Fixed a bug where the Personal Hotspot bar shows yellow background when status bar gets hidden from the app. Closes issue [#394](https://github.com/AppGyver/steroids/issues/394).
- Fixed a bug where the Personal Hotspot bar overlaps the navigation bar and displaced webview content. Closes issue [#393](https://github.com/AppGyver/steroids/issues/393).
- Fixed a bug where an Ad Hoc build with the status bar hidden would cause tabs to be offset upwards. Closes issue [#392](https://github.com/AppGyver/steroids/issues/392).
- Fixed a bug where in apps that had more than 5 tabs errant behavious was experienced when trying to choose tabs from under the More... tab. Closes issue [#116](https://github.com/AppGyver/steroids/issues/116).
- Fixed a bug where the app would crash when calling `steroids.screen.rotateTo` under certain conditions

### 3.1.6-p4 (2014-06-03)

- Fixed a bug where `steroids.layers.push` and `steroids.layers.replace` didn't work from a drawer or from a preloaded view that was not in the layer stack. Related issues [#335](https://github.com/AppGyver/steroids/issues/335) & [#377](https://github.com/AppGyver/steroids/issues/377).
- Fixed a bug where preloads or drawers defined in `application.coffee` were not applied to Ad Hoc builds. Related issue [#369](https://github.com/AppGyver/steroids/issues/369).
- Fixed a bug where `layers.push` called from drawer fired a success callback even though it did nothing. Related issue [#335](https://github.com/AppGyver/steroids/issues/335).
- Fixed a bug where setting a background image to a WebView crashed app on start. Related issue [#368](https://github.com/AppGyver/steroids/issues/368).
- Fixed a bug where modals wouldn't respect `steroids.view.setAllowedRotations()`. Related issue [#313](https://github.com/AppGyver/steroids/issues/313).
- Fixed a bug where calling `steroids.layers.pop()` in landscape orientation crashed the app. Related issue [#276](https://github.com/AppGyver/steroids/issues/276).
- Fixed a bug where calling `steroids.modal.hideAll()` caused the app to show the "yellow screen of death". Related issue [#218](https://github.com/AppGyver/steroids/issues/218)
- Fixed a bug where a modal could not be opened from the drawer. Related issue [#291](https://github.com/AppGyver/steroids/issues/291).

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
