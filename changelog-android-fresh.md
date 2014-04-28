# Changelog for AppGyver Scanner (Fresh Android)

## 0.2 (2014-04-28)

* Android 2.3 support (API levels 10-19)
	* Minimum SDK level can be configured in Build Service.
	* Maximum SDK level setting has no effect for Fresh Android.
	* See [Android Developer's guide](http://developer.android.com/guide/topics/manifest/uses-sdk-element.html) for details about selecting an SDK level.

## 0.1 (2014-04-15)

First beta release!

Supported Android versions:
Android 3.0.x (API level 11) to Android 4.4 (API level 19)

Supported features:

* Single-Page Applications from a File URL. File URLs start without a leading slash, eg. "index.html".
* Start application from a scanned QR code which points to Steroids CLI.
* Steroids CLI refresh will reload project.
* Buildable from AppGyver Build Service having adhoc, scanner and Google Play as build targets.
* Supported settings in Build Service:
	* Keystore
	* Prodution, Ad Hoc and Scanner Build settings EXCEPT min/max SDK level
	* Icons
