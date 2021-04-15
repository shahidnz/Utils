# How to pull an .APK from android mobile to PC

Identify the package name of the app whose .APK you want to pull out. If not sure, open the `Settings > Apps` then tap on your app. Its package name would be listed.
Let's assume it is `my_fav_app.apk`. 
Open the mobile shell in PC (Windows, Mac, or Linux) and note the current directory shown in the shell.

### These commands will work on all the platforms (Windows, Linx and MacOS)

Run below command
```
adb shell 
pm list packages | grep -i my_fav
```

E.g.
```
C:\Users\ShahidSiddiqui>adb devices
List of devices attached
125d8873        device
emulator-5554   device
```
Since I have multiple android devices connected, I'll mention which device to use by giving additional flag `-s <device id>`.

You can also jump into the mobile shell and run the relevant part of the command. E.g.
```
C:\Users\ShahidSiddiqui>adb -s 125d8873 shell
```

Since I am connected to the shell of the mobile, I can dive deep.
```
joyeuse:/ $ pm list packages | grep -i abbv
package:com.abbvie.mycare.dev
joyeuse:/ $
```

If you are not able to find, then remove the grep and run the command again, locate your app by scrolling up and down the shell, like this-
```
pm list packages
```

So, in my case I got the app's package name using command line.

Now we need to get the path of the this app. Provide the package name, viz.
```
pm path com.abbvie.mycare.dev
package:/data/app/com.abbvie.mycare.dev--qZbSY4oBD-gNaxlIt6Q_g==/base.apk
```

The path is found. Now just pull the package. Open another terminal on PC and execute:

`adb pull <path of apk> <name to save>`

```
adb pull /data/app/com.abbvie.mycare.dev--qZbSY4oBD-gNaxlIt6Q_g==/base.apk mycare.apk
```

This new file just pulled will be available in your PC by name as mycare.apk.

Visit [here](https://mssiddiqui.medium.com/unique-source-of-knowledge-e13079276d8) for more insights.

