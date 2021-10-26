# ADB Shell Commands

Some essential ADB shell commands


## Android Debugger

#### Wait for Debugger to Attach
```
adb shell am set-debug-app -w --persistent <my.package.id>
```

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
> This can be used as a workaround for some AVDs with internet connectivity issues




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

Learn more about `bundletool` here https://developer.android.com/studio/command-line/bundletool
