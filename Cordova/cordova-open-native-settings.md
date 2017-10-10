# Cordova-open-native-settings

`Cordova-open-native-settings`这个插件允许你在iOS 8+和Android上打开操作系统设置，例如，它允许你打开键盘设置、Wifi、蓝牙、设置等。了解更多请参考[Cordova-open-native-settings](https://github.com/guyromb/Cordova-open-native-settings) in github.

****

## Adding/Removing the Plugin

```
cordova plugin (add|rm) cordova-open-native-settings --save
```

## Using the plugin

```
cordova.plugins.settings.open(setting_constant, success_callback, failure_callback);
```

### Example For Setting("application_details")

```
//跳转到手机的设置页面
toSetting(): void {
    let $scope = this.$scope;
    let $log = this.$log;
    let $window = this.$window;

    if ($window.cordova && cordova.plugins.settings) {
        console.log('openNativeSettingsTest is active');
        cordova.plugins.settings.open("application_details", () => {
            $log.debug("opened settings");
        },
            () => {
                $log.debug("failed to open settings");
            }
        );
    } else {
        $log.debug("openNativeSettingsTest is not active!");
    }
    $scope.authorityDialog.dialog.hide();
}
```

### More Settings Options

```
  "about", // ios
  "accessibility", // ios, android
  "account", // ios, android
  "airplane_mode", // ios, android
  "apn", // android
  "application_details", // ios, android
  "application_development", // android
  "application", // android
  "autolock", // ios
  "battery_optimization", // android
  "bluetooth", // ios, android
  "castle", // ios
  "captioning", // android
  "cast", // android
  "cellular_usage", // ios
  "configuration_list", // ios
  "data_roaming", // android
  "date", // ios, android
  "display", // ios, android
  "dream", // android
  "facetime", // ios
  "home", // android
  "keyboard", // ios, android
  "keyboard_subtype", // android
  "locale", // ios, android
  "location", // ios, android
  "locations", // ios
  "manage_all_applications", // android
  "manage_applications", // android
  "memory_card", // android
  "music", // ios
  "music_equalizer", // ios
  "music_volume", // ios
  "network", // ios, android
  "nike_ipod", // ios
  "nfcsharing", // android
  "nfc_payment", // android
  "nfc_settings", // android
  "notes", // ios
  "notification_id", // ios
  "passbook", // ios
  "phone", // ios
  "photos", // ios
  "print", // android
  "privacy", // android
  "quick_launch", // android
  "reset", // ios
  "ringtone", // ios
  "browser", // ios
  "search", // ios, android
  "security", // android
  "settings", // ios, android
  "show_regulatory_info",
  "sound", // ios, android
  "software_update", // ios
  "storage", // ios, android
  "store", // ios, android
  "sync", // android
  "tethering", // ios
  "twitter", // ios
  "touch", // ios
  "usage", // ios, android
  "user_dictionary", // android
  "video", // ios
  "voice_input", // android
  "vpn", // ios
  "wallpaper", // ios
  "wifi_ip", // android
  "wifi", // ios, android
  "wireless" // android
```
