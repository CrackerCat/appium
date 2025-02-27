# Appium server arguments and environment variables

Since Appium 1.5, many server arguments have been deprecated in favor of the [--default-capabilities flag](/docs/en/writing-running-appium/default-capabilities-arg.md).

Usage: `node . [flags]`

## Server flags
All flags are optional, but some are required in conjunction with certain others.

<expand_table>

|Flag|Default|Description|Example|
|----|-------|-----------|-------|
|`--shell`|null|Enter REPL mode||
|`--allow-cors`|false|Turn on CORS compatibility mode, which will allow connections to the Appium server from within websites hosted on any domain. Be careful when enabling this feature, since there is a potential security risk if you visit a website that uses a cross-domain request to initiate or introspect sessions on your running Appium server.||
|`--ipa`|null|(IOS-only) abs path to compiled .ipa file|`--ipa /abs/path/to/my.ipa`|
|`-a`, `--address`|0.0.0.0|IP Address to listen on|`--address 0.0.0.0`|
|`-p`, `--port`|4723|port to listen on|`--port 4723`|
|`-pa`, `--base-path`|/wd/hub|Initial path segment where the Appium/WebDriver API will be hosted. Every endpoint will be behind this segment.|`--base-path /my/path/prefix`|
|`-ca`, `--callback-address`|null|callback IP Address (default: same as --address)|`--callback-address 127.0.0.1`|
|`-cp`, `--callback-port`|null|callback port (default: same as port)|`--callback-port 4723`|
|`-bp`, `--bootstrap-port`|4724|(Android-only) port to use on device to talk to Appium|`--bootstrap-port 4724`|
|`-r`, `--backend-retries`|3|(iOS-only) How many times to retry launching Instruments before saying it crashed or timed out|`--backend-retries 3`|
|`--session-override`|false|Enables session override (clobbering)||
|`-l`, `--pre-launch`|false|Pre-launch the application before allowing the first session (Requires --app and, for Android, --app-pkg and --app-activity)||
|`-g`, `--log`|null|Also send log output to this file|`--log /path/to/appium.log`|
|`--log-level`|debug|Set the server log level for console and logfile (specified as `console-level:logfile-level`, with both being the same if only one value is supplied). Possible values are `debug`, `info`, `warn`, `error`, which are progressively less verbose.|`--log-level error:debug`|
|`--log-timestamp`|false|Show timestamps in console output||
|`--local-timezone`|false|Use local timezone for timestamps||
|`--log-no-colors`|false|Do not use colors in console output||
|`-G`, `--webhook`|null|Also send log output to this HTTP listener|`--webhook localhost:9876`|
|`--safari`|false|(IOS-Only) Use the safari app||
|`--default-device`, `-dd`|false|(IOS-Simulator-only) use the default simulator that instruments launches on its own||
|`--force-iphone`|false|(IOS-only) Use the iPhone Simulator no matter what the app wants||
|`--force-ipad`|false|(IOS-only) Use the iPad Simulator no matter what the app wants||
|`--tracetemplate`|null|(IOS-only) .tracetemplate file to use with Instruments|`--tracetemplate /Users/me/Automation.tracetemplate`|
|`--instruments`|null|(IOS-only) path to instruments binary|`--instruments /path/to/instruments`|
|`--nodeconfig`|null|Configuration JSON file to register appium with selenium grid|`--nodeconfig /abs/path/to/nodeconfig.json`|
|`-ra`, `--robot-address`|0.0.0.0|IP Address of robot|`--robot-address 0.0.0.0`|
|`-rp`, `--robot-port`|-1|port for robot|`--robot-port 4242`|
|`--chromedriver-port`|9515|Port upon which ChromeDriver will run|`--chromedriver-port 9515`|
|`--chromedriver-executable`|null|ChromeDriver executable full path||
|`--show-config`|false|Show info about the appium server configuration and exit||
|`--no-perms-check`|false|Bypass Appium's checks to ensure we can read/write necessary files||
|`--strict-caps`|false|Cause sessions to fail if desired caps are sent in that Appium does not recognize as valid for the selected device||
|`--isolate-sim-device`|false|Xcode 6 has a bug on some platforms where a certain simulator can only be launched without error if all other simulator devices are first deleted. This option causes Appium to delete all devices other than the one being used by Appium. Note that this is a permanent deletion, and you are responsible for using simctl or xcode to manage the categories of devices used with Appium.||
|`--tmp`|null|Absolute path to directory Appium can use to manage temporary files, like built-in iOS apps it needs to move around. On *nix/Mac defaults to /tmp, on Windows defaults to C:\Windows\Temp||
|`--trace-dir`|null|Absolute path to directory Appium use to save ios instruments traces, defaults to <tmp dir>/appium-instruments||
|`--debug-log-spacing`|false|Add exaggerated spacing in logs to help with visual inspection||
|`--suppress-adb-kill-server`|false|(Android-only) If set, prevents Appium from killing the adb server instance||
|`--async-trace`|false|Add long stack traces to log entries. Recommended for debugging only.||
|`--webkit-debug-proxy-port`|27753|(IOS-only) Local port used for communication with ios-webkit-debug-proxy|`--webkit-debug-proxy-port 27753`|
|`-dc`, `--default-capabilities`|{}|Set the default desired capabilities, which will be set on each session unless overridden by received capabilities.|`--default-capabilities [ '{"app": "myapp.app", "deviceName": "iPhone Simulator"}' | /path/to/caps.json ]`|
|`--reboot`|false| - (Android-only) reboot emulator after each session and kill it at the end||
|`--command-timeout`|60|[DEPRECATED] No effect. This used to be the default command timeout for the server to use for all sessions (in seconds and should be less than 2147483). Use newCommandTimeout cap instead||
|`-k`, `--keep-artifacts`|false|[DEPRECATED] - no effect, trace is now in tmp dir by default and is cleared before each run. Please also refer to the --trace-dir flag.||
|`--platform-name`|null|[DEPRECATED] - Name of the mobile platform: iOS, Android, or FirefoxOS|`--platform-name iOS`|
|`--platform-version`|null|[DEPRECATED] - Version of the mobile platform|`--platform-version 7.1`|
|`--automation-name`|null|[DEPRECATED] - Name of the automation tool: Appium, XCUITest, etc.|`--automation-name Appium`|
|`--device-name`|null|[DEPRECATED] - Name of the mobile device to use|`--device-name iPhone Retina (4-inch), Android Emulator`|
|`--browser-name`|null|[DEPRECATED] - Name of the mobile browser: Safari or Chrome|`--browser-name Safari`|
|`--app`|null|[DEPRECATED] - IOS: abs path to simulator-compiled .app file or the bundle_id of the desired target on device; Android: abs path to .apk file|`--app /abs/path/to/my.app`|
|`-lt`, `--launch-timeout`|90000|[DEPRECATED] - (iOS-only) how long in ms to wait for Instruments to launch||
|`--language`|null|[DEPRECATED] - Language for the iOS simulator / Android Emulator|`--language en`|
|`--locale`|null|[DEPRECATED] - Locale for the iOS simulator / Android Emulator|`--locale en_US`|
|`-U`, `--udid`|null|[DEPRECATED] - Unique device identifier of the connected physical device|`--udid 1adsf-sdfas-asdf-123sdf`|
|`--orientation`|null|[DEPRECATED] - (IOS-only) use LANDSCAPE or PORTRAIT to initialize all requests to this orientation|`--orientation LANDSCAPE`|
|`--no-reset`|false|[DEPRECATED] - Do not reset app state between sessions (IOS: do not delete app plist files; Android: do not uninstall app before new session)||
|`--full-reset`|false|[DEPRECATED] - (iOS) Delete the entire simulator folder. (Android) Reset app state by uninstalling app instead of clearing app data. On Android, this will also remove the app after the session is complete.||
|`--app-pkg`|null|[DEPRECATED] - (Android-only) Java package of the Android app you want to run (e.g., com.example.android.myApp)|`--app-pkg com.example.android.myApp`|
|`--app-activity`|null|[DEPRECATED] - (Android-only) Activity name for the Android activity you want to launch from your package (e.g., MainActivity)|`--app-activity MainActivity`|
|`--app-wait-package`|false|[DEPRECATED] - (Android-only) Package name for the Android activity you want to wait for (e.g., com.example.android.myApp)|`--app-wait-package com.example.android.myApp`|
|`--app-wait-activity`|false|[DEPRECATED] - (Android-only) Activity name for the Android activity you want to wait for (e.g., SplashActivity)|`--app-wait-activity SplashActivity`|
|`--device-ready-timeout`|5|[DEPRECATED] - (Android-only) Timeout in seconds while waiting for device to become ready|`--device-ready-timeout 5`|
|`--android-coverage`|false|[DEPRECATED] - (Android-only) Fully qualified instrumentation class. Passed to -w in adb shell am instrument -e coverage true -w |`--android-coverage com.my.Pkg/com.my.Pkg.instrumentation.MyInstrumentation`|
|`--avd`|null|[DEPRECATED] - (Android-only) Name of the avd to launch|`--avd @default`|
|`--avd-args`|null|[DEPRECATED] - (Android-only) Additional emulator arguments to launch the avd|`--avd-args -no-snapshot-load`|
|`--use-keystore`|false|[DEPRECATED] - (Android-only) When set the keystore will be used to sign apks.||
|`--keystore-path`|&lt;user&gt;/.android/debug.keystore|[DEPRECATED] - (Android-only) Path to keystore||
|`--keystore-password`|android|[DEPRECATED] - (Android-only) Password to keystore||
|`--key-alias`|androiddebugkey|[DEPRECATED] - (Android-only) Key alias||
|`--key-password`|android|[DEPRECATED] - (Android-only) Key password||
|`--intent-action`|android.intent.action.MAIN|[DEPRECATED] - (Android-only) Intent action which will be used to start activity|`--intent-action android.intent.action.MAIN`|
|`--intent-category`|android.intent.category.LAUNCHER|[DEPRECATED] - (Android-only) Intent category which will be used to start activity|`--intent-category android.intent.category.APP_CONTACTS`|
|`--intent-flags`|0x10200000|[DEPRECATED] - (Android-only) Flags that will be used to start activity|`--intent-flags 0x10200000`|
|`--intent-args`|null|[DEPRECATED] - (Android-only) Additional intent arguments that will be used to start activity|`--intent-args 0x10200000`|
|`--dont-stop-app-on-reset`|false|[DEPRECATED] - (Android-only) When included, refrains from stopping the app before restart||
|`--calendar-format`|null|[DEPRECATED] - (IOS-only) calendar format for the iOS simulator|`--calendar-format gregorian`|
|`--native-instruments-lib`|false|[DEPRECATED] - (IOS-only) IOS has a weird built-in unavoidable delay. We patch this in appium. If you do not want it patched, pass in this flag.||
|`--keep-keychains`|false|[DEPRECATED] - (iOS-only) Whether to keep keychains (Library/Keychains) when reset app between sessions||
|`--localizable-strings-dir`|en.lproj|[DEPRECATED] - (IOS-only) the relative path of the dir where Localizable.strings file resides |`--localizable-strings-dir en.lproj`|
|`--show-ios-log`|false|[DEPRECATED] - (IOS-only) if set, the iOS system log will be written to the console||
|`--relaxed-security`|false|Disable additional security checks, so it is possible to use some advanced features, provided by drivers supporting this option. Only enable it if all the clients are in the trusted network and it is not the case if a client could potentially break out of the session sandbox. Can override enabling of specific features with --deny-insecure. See also the [security doc](/docs/en/writing-running-appium/security.md)||
|`--allow-insecure`|[]|Allow a list of features which are considered insecure and must be turned on explicitly by system administrators. Feature names are documented by the relevant server/driver. Should be a comma-separated list, or a path to a filename containing one feature name per line. Features listed in --deny-insecure will override anything listed here. Does not make sense to use in conjunction with --relaxed-security. See also the [security doc](/docs/en/writing-running-appium/security.md)|`--allow-insecure=foo,bar`|
|`--deny-insecure`|[]|Specify a list of features which will never be allowed to run, even if --relaxed-security is turned on, and even if feature names are listed with --allow-insecure. Should be a comma-separated list, or a path to a filename containing one feature name per line. See also the [security doc](/docs/en/writing-running-appium/security.md)|`--deny-insecure=foo,bar`|
|`--log-filters`|null|Specify a full path to a JSON file containing one or more log filtering rules. This feature is useful for cases when it is necessary to obfuscate sensitive information, which may be present in server log records, like passwords or access tokens. The format of each rule is described in https://github.com/appium/appium-support/blob/master/lib/log-internal.js. An exception will be thrown on server startup if any of the rules has issues.|`--log-filters=/home/config.json`|


## Environment variables

|Flag|Default|Description|Example|
|----|-------|-----------|-------|
|`APPIUM_PREFER_SYSTEM_UNZIP`|| Tell Appium to always prefer the built-in unzip implementation instead of trying to use the unzip executable bundled with the operationg system, whcih is usually more performance. Setting this environment variable to `0` or `false` could help to avoid issues similar to [appium#16050](https://github.com/appium/appium/issues/16050). This flag is available since Appium 1.22.1. | `0` `false` |
