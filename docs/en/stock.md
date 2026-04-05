# ColorOS/OxygenOS Tips

## **Where is the Game Assistant?**

Game Assistant app is not pre-installed on OnePlus Pad 3.

On OnePlus Pad 2 Pro, it is pre-installed, but it includes excessive Chinese content. Updating it from Google Play Store is much better while retaining core functionalities.

1. Install/Update [Games by HeyTap](https://play.google.com/store/apps/details?id=com.oplus.games) from Google Play Store.

---

## **Disable Ram expansion**
If you are using the 16GB RAM model (and also for the 12GB model, depending on your usage pattern), it is recommended to turn off Ram expansion for better performance.

To turn it off, go to `About device > RAM > RAM expansion`

---

## ~~**Disable permission monitoring**~~
~~COS/OOS includes its own aggressive permission monitoring system that is far more restrictive than stock Android.~~

~~While intended for security, this feature often acts as an excessive limitation, interfering with legitimate power-user functions like advanced tools (e.g., Shizuku) or specific ADB commands.~~

~~Enabling 'Disable permission monitoring' in Developer Options allows you to bypass these overly restrictive controls. This removes inconveniences and grants greater freedom for system customization and the use of advanced applications.~~

Do not do this, or revert it if you have already done so. Starting from v16.0.5.xxx, display settings will not be appear correctly if you enable this option.

---

## **Disable Google Discover**
This is properly applicable on COS/OOS 16 only.

Enable USB debugging, and connect your device to PC.

Open a command prompt where adb is located and enter the following commands:

```
adb shell settings put secure assistant_screen_type 0
adb shell settings put secure assistant_screen_type_left_enable 0
```
