
<img src="https://user-images.githubusercontent.com/2157285/46095220-e38ba580-c1c8-11e8-94dc-730d14f834c8.png" width="200">

# Starlight
Starlight is a dark/light mode manager for OS X. It measures the surrounding ambient light and then performs light/dark theme adjustments based on that. Starlight is a daemon server and performs an adjustment task every 10 seconds. Starlight is a very lightweight task and uses 0~0.2% of your CPU and 5 MB of memory.

## How to build it?
You must be using macOS mojave or later (to even have the light/dark possibility) and then you must have Xcode installed (in a version that supports Swift 4.1+). This build system only uses Swift compiler so if you have `swiftc` in such way that it supports `4.1+` you can use it. You also have to have GNU Make installed.

```
% make install
```

This will install `starlight` to your `/usr/local/bin` and the `starlight-daemon.plist` to your `~/Library/LaunchAgents`

## How to use it?
Starlight runs with a factory preset, but you can change its settings by putting a

```js
{
    "intervals":    10,             // The time interval in seconds that starlight
                                    // measures, performs changes and goes to idle
                                    // mode again.


    "minimumLux":   75000,          // Minimum lux amount to be in the light mode.
                                    // if the amount that is measured is under the
                                    // minimumLux amount, then it will change to
                                    // dark mode and in other cases back to light.


    "sunset":       "18:00",        // By setting these two times, from sunset to
    "sunrise":      "06:00",        // sunrise, starlight forces dark mode.


    "wallpapers": {                 // By setting this, starlight changes the
        "light": "~/light.png",     // wallpaper. You have to specify the path of
        "dark":  "~/dark.png"       // the light and dark theme.
    },                              //
                                    // NOTE: Remember that this changes "all" the
                                    // wallpapers of all the screens and monitors.
                                    // so use it with caution.


    "vscode": {                     // this setting changes the theme of Visual
        "light": "Light Theme",     // Studio Code by changing the value of the
        "dark":  "Dark Theme"       // "workbench.colorTheme"
    }
}
```