[English](README.md) | [繁體中文](README.zh-TW.md)

# OBS Image Reaction Plugin
Image that reacts to sound source.

## Installing binaries
Download binaries from [official releases](https://github.com/scaledteam/obs-image-reaction/releases/) or more user-friendly version from [ashmanix](https://github.com/ashmanix/obs-image-reaction/releases).

For Windows (OBS 33 and later), extract the zip and move the "image-reaction" folder into "C:\ProgramData\obs-studio\plugins\" (the ProgramData folder is hidden; type `%ProgramData%` in the Run dialog to open it, and create `plugins` if it does not exist). Do not put it in "C:\Program Files\obs-studio\": OBS 33 does not look for this folder there (that location is legacy and deprecated).

The folder must contain `image-reaction.dll` directly, and a `data` folder next to it. Restart OBS, then check Tools > Plugin Manager.

For GNU/Linux (OBS 33 and later), extract the archive and move the "image-reaction" folder into "~/.local/share/obs-studio/plugins/" (create the folders if they do not exist). The folder must contain `image-reaction.so` and a `data` folder next to it.

For Mac OS, extract the archive and move "image-reaction.plugin" into "~/Library/Application Support/obs-studio/plugins/" (create the folders if they do not exist). You may need to allow the plugin in System Settings > Privacy & Security if it is not signed. Alternatively, try this port from ashmanix: https://github.com/ashmanix/obs-image-reaction .

## Building and installing for GNU/Linux:
```
git clone https://github.com/scaledteam/obs-image-reaction
cd obs-image-reaction
mkdir build
cd build
cmake ..
make
mkdir -p ~/.local/share/obs-studio/plugins/image-reaction
cp image-reaction.so ~/.local/share/obs-studio/plugins/image-reaction/
cp -r ../data ~/.local/share/obs-studio/plugins/image-reaction/
```

## Building for Windows from GNU/Linux:
You need to download MinGW, OBS Studio source code, Wine, install OBS Studio using wine.
Note: these cross-build instructions predate OBS 33 and have not been verified with it.
```
git clone https://github.com/scaledteam/obs-image-reaction
cd obs-image-reaction
mkdir build-win
cd build-win
cmake ..  -DCMAKE_SYSTEM_NAME=Windows  -DCMAKE_CXX_COMPILER=/usr/bin/x86_64-w64-mingw32-g++-win32  -DCMAKE_C_COMPILER=/usr/bin/x86_64-w64-mingw32-gcc-win32 -DLIBOBS_INCLUDE_DIR=~/git/obs-studio-27.0.1/libobs -DLIBOBS_LIB=~/.wine/drive_c/Program\ Files/obs-studio/bin/64bit/obs.dll
make
```
Then install the result as described above: the "image-reaction" folder with `image-reaction.dll` and `data/` goes into "C:\ProgramData\obs-studio\plugins\".
