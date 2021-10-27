# ADB Shell Commands

Some essential ADB shell commands
## ADB Server
```
adb start-server 
adb kill-server
adb devices 
```
## APK Install & Uninstall
```
adb install <app.apk>
adb install -r <app.apk> // Reinstall the apk and keep the existing data 
adb install -d <app.apk> // Install the apk allowing version downgrade
adb uninstall <my.package.id>
```
## Android Debugger
#### Wait for Debugger to Attach
```
adb shell am set-debug-app -w --persistent <my.package.id>
```
Adding debugger this way is helpful to debug the app right from the start-up. Another option is to use `WaitForDebugger`.
#### Clear Debugger to Attach
```
adb shell am clear-debug-app <my.package.id>
```
## Open Deep Links
```
adb shell am start -a android.intent.action.VIEW -d "scheme://my/app/page"
```
## Emulator
#### List all AVDs
```
emulator -list-avds
```

```
Nexus5_Nougat
Nexus_5X_API_23
Pixel2_Pie
Pixel3a_Android-10
```
#### Run a specific AVD
```
emulator @Pixel2_Pie
```
#### Run a specific AVD setting DNS 
```
emulator @Pixel2_Pie -dns-server 8.8.8.8
```
_This can be used as a workaround for some AVDs with internet connectivity issues._
## ADB Inputs
#### Input event - SWIPE
```
adb shell input touchscreen swipe x1 y1 x2 y2 t
```
x1 y1 - Starting coordinates;
x2 y2 - Ending coordinates;
t - Duration in ms

Sample:
```
adb shell input touchscreen swipe 0 1080 0 0 20 (Swipe Down)
adb shell input touchscreen swipe 0 0 0 1080 20 (Swipe Up)
```
## Firebase Debugging Events & GTM Loogging
#### Enable logging
```
adb shell setprop debug.firebase.analytics.app <my.package.id>
```
#### Disable logging
```
adb shell setprop debug.firebase.analytics.app .none.
```
#### Set GTM Log Level
```
adb shell setprop log.tag.GoogleTagManager VERBOSE
```
## App Bundles (bundletool)

#### Create APK set
```
bundletool build-apks --bundle=my_app.aab --output=my_app.apks
```
#### Create APK set with Signing info form Keystore
```
bundletool build-apks --bundle=my_app.aab --output=my_app.apks
--ks upload.keystore
--ks-pass ‘pass:yourPassword’
--ks-key-alias MyKeyAlias
--key-pass ‘pass:yourPassword’
```
#### Install APKs to the connected device
```
bundletool install-apks --apks=myapp.apks
```
## Systrace
```
python systrace.py -t N -a <app_name>
```
t - Run the trace for N seconds.
a - Enable tracing for a specific app.


## Links
Learn more about `Android Debug Bridge` here https://developer.android.com/studio/command-line/adb

Learn more about `Firebase Debugging Events` here https://firebase.google.com/docs/analytics/debugview

Learn more about `Bundletool` here https://developer.android.com/studio/command-line/bundletool

Learn more about `Systrace` here https://developer.android.com/topic/performance/tracing/command-line

List of other ADB commands https://gist.github.com/Pulimet/5013acf2cd5b28e55036c82c91bd56d8
