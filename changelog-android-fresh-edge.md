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
