## Edge versions for AppGyver iOS Native Runtime

This changelog documents features and bugfixes available in **Edge** versions of the AppGyver iOS Native Runtime. They are available to give users access to new features and bugfixes without having to wait for the next **stable** version to pass the Apple App Store approval process. Edge versions can be unstable, so use them with caution – building with Edge versions for production is not adviced.

Read more in the [patch and Edge versions guide](http://academy.appgyver.com/guides/86)!

The changelog for **stable** releases is available [here](https://github.com/AppGyver/scanner/blob/master/changelog-ios.md).

The runtime versions currently in use by each AppGyver component can be found [here](https://github.com/AppGyver/scanner/blob/master/runtime-versions.md)

### 4.0.2-edge2 (2014-12-05):

Bugfix:
- MAJOR fix to our JSCore, events are now queued to prevent crashes. Fixes the constant Scanner crashing.

### 4.0.2-edge1 (2014-12-03):

Changes:
- Speed up Cordova `deviceready` on all iOS devices by changing the way Cordova's plugins are loaded. 

Features:
- Pixate `navigation-bar back-button` has been implemented

Bugfixes:
- Livereload did not look for changed files in user files
- Blank page was sometimes shown after splashscreen on Livereload

### 4.0.1-rc1 (2014-11-04): iPhone6 and iPhone6+

Features:
- Support for iPhone6 and iPhone 6+
  - Requires new graphical assets being defined in the Build Service
- API calls for `setStyle` properly discard inline styles set previously
  with `setStyle`
- `steroids.screen.dismissAlert` now triggers Cordova success callbacks.
- Preloaded drawers were broken after dismissing Initial View for the second
  time (fixes [#536](https://github.com/AppGyver/steroids/issues/536)).


### 4.0.1-edge1:

Breaking change:
- Native CSS is now read from `ios.css` instead of `default.css`.

Features:
- Tab Items use the `id` defined in `application.coffee` for Native CSS.

Bugfixes:
- `steroids.screen.dismissAlert` now triggers Cordova success callbacks.
- Preloaded drawers were broken after dismissing Initial View for the second
  time (fixes [#536](https://github.com/AppGyver/steroids/issues/536)).
- External keyboard caused background of software keyboard being displayed
  (fixes [#447](https://github.com/AppGyver/steroids/issues/447)).
- Preloaded WebViews are now discarded when displaying the Initial View
  (fixes [#572](https://github.com/AppGyver/steroids/issues/572)).
- Focusing on an input caused an input field being scrolled out of the visible
  view and it did not come back even when started typing.
- WebView was pushed too far up if an input was at the bottom of the screen
  and Tab Bar was visible
  (fixes [#567](https://github.com/AppGyver/steroids/issues/567)).
- iPad on landscape-only builds displayed a black splashscreen.
- Updated cordova-plugin-dialogs to 0.2.10.



### 3.5.3-rc3 (== 4.0.0 stable):

3.5.3-rc3 was released as 4.0.0 (we decided to bump the major version number after all.)

Bugfixes:
- Text area lost focus and had other erratic behaviour when orientation was changed
  while having the keyboard open.
  (fixes [#467](https://github.com/AppGyver/steroids/issues/467))


### 3.5.3-rc2:

Changes:
- Switched included Cordova Keyboard plugin to the
  [Ionic Keyboard plugin](https://github.com/driftyco/ionic-plugins-keyboard/)
  (fixes [#550](https://github.com/AppGyver/steroids/issues/550))
- Keyboard settings can no longer be configured app-wide in `config.ios.xml`.

Bug fixes:
- Opening the Photo Library caused a crash on iOS 8.


### 3.5.3-edge4: Fix edge3

Features:
- Add window.AG_WEBVIEW_UUID which gives out same value as window.AG_WEBVIEW_UDID.
  The latter will be deprecated.

Bug fixes:
- Fixed http://localhost which was broken in 3.5.3-edge3
- iOS 8 location services caused a "legacy on-demand authorization" error
  (fixes [#544](https://github.com/AppGyver/steroids/issues/544))
- Fixed typo in Drawer options (strechDrawer -> stretchDrawer)


### 3.5.3-edge3: APIs for Native UI styling

Features:
- API calls for styling Native UI with CSS:
  - API methods setStyle and setClass for Tab Bar and Navigation Bar
  - API method setTheme to apply a set of styles at once
- steroids.screen.dismissNextAlert mainly for test automation
- steroids.view.navigationBar.tapButton mainly for test automation

Bug fixes:
- Cordova Plugins which included a native framework couldn't be compiled
  (affected only 3.5.3-edge1 and 3.5.3-edge2).
- PreviewFileView didn't display pdf on iOS8
  (fixes [#528](https://github.com/AppGyver/steroids/issues/528))
- If called from modal, navigator.camera.getPicture closed the modal after it's callbacks
  (fixes [#465](https://github.com/AppGyver/steroids/issues/465))
- Allow `steroids.layers.replace` to be used even when the target view is in the layer stack
  (fixes [#411](https://github.com/AppGyver/steroids/issues/411))

### 3.5.3-edge2: Styling Native UI with CSS

Features:
- Native UI can be styled with CSS syntax (Pixate).
  - Styles can be provided from `dist/native-styles/default.css`

Bug fixes:
- Backported Cordova fixes for iOS8:
  - https://github.com/apache/cordova-ios/commit/b06ca8db4288f47e99f32294080106884e236d47
  - https://github.com/apache/cordova-ios/commit/6329027c4a35d18d85dcc5bcd0ee3a6d34fe2421

### 3.5.3-edge1 (2014-09-24)

iOS8 fixes for [#534](https://github.com/AppGyver/steroids/issues/534):
- Updated Cordova submodule to iOS 8 compatibility commit
- Updated hardcoded Cordova plugins for iOS 8 compatibility.
  See versions [here](https://academy.appgyver.com/categories/7-extending-with-plugins/contents/146-default-plugins).

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
