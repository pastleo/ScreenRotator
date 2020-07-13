# Simple Qt screen rotation manager

Reads from accelerometer sensors, and rotate display according to the readings.

Works only in X11 for now.

Similar to the current solution implemented in Gnome, but works on all other desktop environments as well (KDE, XFCE, etc).

## Compilation requirements

 - cmake
 - gcc
 - Qt5 (with modules x11extras, sensors)
 - xrandr
 - XInput (Xi)
 
On ubuntu, run the following command to install dependencies:
```
sudo apt install -y git cmake build-essential qtbase5-dev libxrandr-dev libxi-dev libqt5x11extras5-dev libqt5sensors5-dev 
```

## Building
```
git clone https://github.com/GuLinux/ScreenRotator
mkdir ScreenRotator/build
cd ScreenRotator/build
cmake ..
make all
sudo make install
```

## Why this fork?

the AUR [screenrotator](https://aur.archlinux.org/packages/screenrotator-git/) can auto-rotate my 2-in-1 laptop with ease,

however, sometimes I want to rotate when I want it to, so I modify a bit and make a fork

by default this fork still does auto-rotation (to make it behave the same as original), but you can turn it off: https://youtu.be/10Fbdn8byM8

when auto-rotation is off (or maybe I should call it manual mode), rotation can be done like this: https://youtu.be/NRrZMKTKHSs

## How to use this fork on ArchLinux

Build ScreenRotator using this `PKGBUILD`: https://github.com/pastleo/ScreenRotator/blob/feature/rotate-control-aur/aur/PKGBUILD

```sh
git clone -b feature/rotate-control-aur https://github.com/pastleo/ScreenRotator.git
cd ScreenRotator/aur
makepkg -si
```

### How to use manual mode instead of auto-rotation at login?

by setting `DEFAULT_AUTO_ROTATION_OFF` environment variable, initial auto-rotation will be off (aka manual mode) at login:

https://github.com/pastleo/ScreenRotator/commit/429aa0fb4cfeb751684e78f0724e2ea2aee1e693#diff-5cd02d4f22f42f4d7a72b791395c07d3R56

for example, in `~/.xprofile`:

```
export DEFAULT_AUTO_ROTATION_OFF=true
```

## Links

Main icon: https://www.iconfinder.com/icons/326583/orientation_rotation_screen_icon#size=256

