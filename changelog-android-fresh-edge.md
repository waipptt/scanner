## 3.5.1-edge-p1

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
