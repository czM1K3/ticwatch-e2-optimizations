# Ticwatch E2 Optimizations
In this repository there are optimization/debloat for Mobvoi Ticwatch E2 watches. **If you don't own this watch, please, don't buy it!** After all updates it is completly messy and laggy. So, there are some optimizations. And please note that you are doing it at your own risk. I'm not responsible for any possible problems that you encounter with.

## Enabling ADB
For most tweaks we will need access to watches with ADB.
- Download ADB - [tutorial from xda](https://www.xda-developers.com/install-adb-windows-macos-linux/)
- Open Settings on your watch
- Go to System and About
- Then keep tapping on Build number until you see message, that you are developer
- Go back to main screen of setting and on the bottom you should see Developer options, so open them
- Scroll down until you see ADB debugging and check it
- Then enable debugging over Wi-Fi and you should see an IP address of your watch and port of adb (for example: 192.168.0.2:5555)
- On the computer type "adb connect your-ip-address" where you swap "your-ip-address" to one from previous step
- Then on watch just confirm and you should be good to go

## Reducing animations
One of the easiest optimizations is to disable or reduce animations. For that open Developer options and scroll to "Window animation scale" and set it to 0.5x (animations will be 2x faster) or to off (to skip animations). And repeat this with next 2 options. You may experiment with those speeds, but turning them off will be the fastest.

## Disabling some apps
The best think to do is to disable unused apps and bloatwere. Some can increase speed and increase battery life and some may not do anything.
If you want to restore any app, just enter the same command as to disable them and just replace "disable-user" to "enable".

### Disable Mobvoi bloatware
This will probably broke communication with Mobvoi app. (for me it never worked, so not big deal)
```
adb shell pm disable-user --user 0 com.mobvoi.companion.aw
adb shell pm disable-user --user 0 com.mobvoi.wear.account.aw
adb shell pm disable-user --user 0 com.mobvoi.wear.appsservice
adb shell pm disable-user --user 0 com.mobvoi.wear.privacy.aw
adb shell pm disable-user --user 0 com.mobvoi.wear.system.aw
```

### Disable default Mobvoi watch faces
```
adb shell pm disable-user --user 0 com.mobvoi.wear.watchface.aw
```

### Disable default Google watch faces
```
com.google.android.clockwork.complications.watchfaces.analog
com.google.android.clockwork.complications.watchfaces.digital
```
**Please, don't disable all available watch faces!!!**

### Disable Mobvoi Fitness and Health apps
This will probably increase batery life and smoothnes but you will not be able to track your steps and workouts
```
adb shell pm disable-user --user 0 com.mobvoi.wear.fitness.aw
adb shell pm disable-user --user 0 com.mobvoi.wear.health.aw
```

### Disable Google Fit
For me this app didn't work anyway
```
adb shell pm disable-user --user 0 com.google.android.apps.fitness
```

### Disable some Google bloat
This breaks Google Assistant's voice recognition
```
adb shell pm disable-user --user 0 com.google.android.googlequicksearchbox
```

### Disable Google Handwriting
(I don't even know where to access this thing)
```
adb shell pm disable-user --user 0 com.google.android.apps.handwriting.ime
```

### Disable Alarms, Stopwatch and Timer
```
adb shell pm disable-user --user 0 com.google.android.deskclock
```

## Last step
Last step would probably be to disable ADB Debugging in the settings.