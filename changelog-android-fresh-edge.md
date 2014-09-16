## 3.5.3-rc3 (2014-09-16): Return proper 404 errors in http://localhost

Bug fixes:
- Return HTTP 404 Not Found when an asset from http://localhost does not
  exist. Previously "Connection Refused" was the result which caused problems.
  (fixes [#524](https://github.com/AppGyver/steroids/issues/524))


## 3.5.3-rc2 (2014-09-10): Multipage apps with Chromium

Bug fixes:
- Applied a workaround to get multipage support on Chromium
  (closes [#495](https://github.com/AppGyver/steroids/issues/495))

Known issues:
- Viewport size must be defined in the HTML or content will appear as zoomed out
  ([#297](https://github.com/AppGyver/steroids/issues/297))
- Chromium runtime doesn't handle device button events correctly
  ([#519](https://github.com/AppGyver/steroids/issues/519))


## 3.5.3-rc1 (2014-09-09): Styled navigation bar

This is the first release candidate for 3.5.3-stable.

Features:
- Navigation bar looks more native by default.
- Required permissions can be configured in the Build Service
  (closes [#508](https://github.com/AppGyver/steroids/issues/508))

Bug fixes:
- URLs with a double slash no longer give an error message,
  eg. `http://localhost//index.html` (fixes [#514](https://github.com/AppGyver/steroids/issues/514))
- Scanned URL is correctly remembered when opening a previously scanned app
  (fixes [#513](https://github.com/AppGyver/steroids/issues/513))
- Back button no longer wraps into two lines on small screens
  (fixes [#512](https://github.com/AppGyver/steroids/issues/512))


## 3.5.3-edge4 (2014-09-04): Styled scanner

Features:
- Scanner shares similar outlook with the AppGyver iOS client.
- API for visibilityState returns values according to the WebView's visibility
- Tab bar is displayed on the bottom by default to allow better multiplatform
  consistency. Tab bar position can be changed in the future in `application.coffee`
  and with `steroids.tabBar.update`.
- WebViews have unique identifiers (UUID) available API calls.
- Crosswalk runtimes updated to 8.37.189.7 with Chromium M37.0.2062.94 (closes [#485](https://github.com/AppGyver/steroids/issues/485))

Bug fixes:
- Back button now closes all open modals before exiting the app (fixes [#505](https://github.com/AppGyver/steroids/issues/505)).
- WebView transitions now work with Android 4.0.
- Tab bar no longer gets misaligned on Android 4.0 after orientation change (fixes [#494](https://github.com/AppGyver/steroids/issues/494)).
- Preloaded views can be displayed multiple times (fixes [#510](https://github.com/AppGyver/steroids/issues/510)).
- Navigation bar's visible size stays the same although different devices have
  different pixel-densities.


## 3.5.3-edge3 (2014-09-01): Navigation bar

New naming convention for edge versions: the "p" is now dropped out because too many people
confused stable patch level releases (3.5.2-p2) with edges (3.5.2-edge-p2).
This caused wrong version numbers being reported in bug reports.

Features:
- Navigation bar
  - Back button returns to the previous WebView
  - API calls
    - show / hide the navigation bar
    - set the navigation bar title

Bug fixes:
- Scanner intelligently selects the correct IP address from the scanned
  QR code (fixes [#302](https://github.com/AppGyver/steroids/issues/302))
- Tab Bar position is remembered when switching the frontmost activity,
  for example: pause/resume the app, open the camera.
  (fixes [#503](https://github.com/AppGyver/steroids/issues/503))
- Exiting the app no longer causes Illegal State Exception
  (fixes [#504](https://github.com/AppGyver/steroids/issues/504))
- Scanner no longer runs out of memory with a one second polling interval
  (fixes [#359](https://github.com/AppGyver/steroids/issues/359))

## 3.5.3-edge-p2 (2014-08-26)

Bug fixes:
- Fix crash which occurred if Tab Bar wasn't defined in application.coffee ([#497](https://github.com/AppGyver/steroids/issues/497))
- Implement rest of Chromium WebView APIs required by Cordova

## 3.5.3-edge-p1 (2014-08-22): Initial MPA and Updated Chromium

Features:
- Initial support for multi-page applications:
  - Views can be pushed/popped in the layer stack.
  - Modal can be displayed and hid.
  - All modals can be closed at once.
  - Basic animation for layer transitions.
  - Preloaded views.
  - Tab bar for selecting the current set of views on the screen.
  - Back button navigates back in the current view stack.
- Completely revamped Chromium internals
  - Chromium is now provided by the [Crosswalk Project](https://crosswalk-project.org/).
  - Chromium updated to M37 using Crosswalk-8.
- Chromium runtime supports loading project assets from http://localhost.
- Communicate between WebViews using JavaScript post messages.

Known issues:
- Chromium runtime supports only Single-Page apps ([#495](https://github.com/AppGyver/steroids/issues/495))
  - Vote [issue XWALK-2012](https://crosswalk-project.org/jira/browse/XWALK-2012) on Crosswalk Jira to let them know You want multi-page apps.
- Android 4.0 issues:
  - Tab bar is not displayed correctly ([#494](https://github.com/AppGyver/steroids/issues/494))
  - Cordova plugins for Steroids Addons do not initialize correctly ([#493](https://github.com/AppGyver/steroids/issues/493))
- Android 2.3 is no longer supported starting from 3.5.3
  - Release 3.5.2 will be stay available in Build Servier as a support release for Android 2.3.


## 3.5.2-edge-p3 (2014-08-11)

Features:

- A Steroids app can now send logs to Steroids CLI via `steroids.logger.log`.
- Opening a link with the `appgyver://` schema will open the Fresh Android application.
- An AppGyver Cloud QR code can be used to load a Steroids app.
- An event (`steroids.keyboard.on` `actionButtonPressed`) is now dispatched when the Go button is pressed on the Android software keyboard.

Bug fixes:

- Most of Android permissions required by Scanner are marked as optional, which allows e.g. downloading the Scanner from Google Play even if the device doesn't have Camera.
- Fixed crash caused by the QR code reader timing out or returning corrupted data.
- Previously opened WebViews are properly closed when Scanned Steroids application is reloaded.
- Fixed compatibility with the [email composer Cordova plugin](https://github.com/AppGyver/email-composer/).


## 3.5.2-edge-p2 (2014-07-31)

Features:
- Facebook SDK is included by default (will be optional later), which allows the official
  Cordova Facebook plugin to compile.



## 3.5.2-edge-p1 (2014-07-31)

Features:
- Android keyboard's Go button triggers an event that can be used on Javascript side.
- WebKit runtime supports initial_eval_js_string.
- Updated media-capture plugin to 0.3.1
- Updated media plugin to 0.2.11
- Updated file-transfer plugin to 0.4.4
- Updated file plugin to 1.2.0
- Complete support for Cordova's onMessage (required for plugins).
- Steroids application can send logs to Steroids CLI (or any endpointUrl)


Bug fixes:
- navigator.app.exitApp() now quits the application.
- Previously opened WebViews are now closed after a scanned application is restarted.
