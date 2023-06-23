# Oz-DWM

This is my custom fork of suckless' DWM.

## Dependancies & Install
* feh: for background
* libx11: for obvious reasons
* fontawesome: for emojis on the status bar
* cmake: build

Clean install and build
```bash
sudo apt install feh libx11 fontawesome cmake
git clone https://github.com/James-Oswald/oz-dwm.git
#cmake build 
mkdir oz-dwm/build
cd oz-dwm/build
cmake ..
make

#add "exec dwm" to your .xinitrc to start on x server startup
```

## Defaults and Keys
* Terminal (Mod4 + Enter): Alacritty
* Browser (Mod4 + B): Chromium
* Editor (Mod4 + C): VSCode

## Main Modifications
1) Uses the CMake build system
2) Expects feh on PATH, uses feh to set the background at DWM launch. Installs the background when `make install` is run
3) Patches with gaps

