[English](README.md) | [繁體中文](README.zh-TW.md)

# OBS 聲控圖片插件
根據音訊來源變化顯示不同圖片的 OBS 插件。

## **安裝二進位檔**
可以從 [官方發布](https://github.com/scaledteam/obs-image-reaction/releases/) 下載插件，或下載由 [ashmanix](https://github.com/ashmanix/obs-image-reaction/releases) 提供的更易用版本。

### **Windows 安裝**
1. 下載插件並解壓縮。
2. 將 **image-reaction** 資料夾放入 "C:\ProgramData\obs-studio\plugins\"（OBS 33 及以上版本）。ProgramData 是隱藏資料夾，可在執行對話框輸入 `%ProgramData%` 開啟；若沒有 `plugins` 資料夾請自行建立。不要放在 "C:\Program Files\obs-studio\"，OBS 33 不會在該位置尋找此資料夾（該位置為舊式且已棄用）。
3. 重新啟動 OBS，並在來源清單中找到 **「聲控圖片」**。

### **GNU/Linux 安裝**
1. 下載插件並解壓縮。
2. 將 **image-reaction** 資料夾放入 "~/.local/share/obs-studio/plugins/"（OBS 33 及以上版本）。資料夾內須有 `image-reaction.so` 與旁邊的 `data` 資料夾。
3. 重新啟動 OBS。

### **MacOS 安裝**
可以嘗試使用 ashmanix 提供的 macOS 版本： [https://github.com/ashmanix/obs-image-reaction](https://github.com/ashmanix/obs-image-reaction)。

## **在 GNU/Linux 上編譯與安裝：**
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

## 在 GNU/Linux 交叉編譯 Windows 版本：
如果你需要在 GNU/Linux 上編譯 Windows 版本，你需要下載 MinGW、OBS Studio 原始碼、Wine，並使用 Wine 安裝 OBS Studio。
注意：以下交叉編譯指令早於 OBS 33，尚未在 OBS 33 上驗證。
```
git clone https://github.com/scaledteam/obs-image-reaction
cd obs-image-reaction
mkdir build-win
cd build-win
cmake ..  -DCMAKE_SYSTEM_NAME=Windows  -DCMAKE_CXX_COMPILER=/usr/bin/x86_64-w64-mingw32-g++-win32  -DCMAKE_C_COMPILER=/usr/bin/x86_64-w64-mingw32-gcc-win32 -DLIBOBS_INCLUDE_DIR=~/git/obs-studio-27.0.1/libobs -DLIBOBS_LIB=~/.wine/drive_c/Program\ Files/obs-studio/bin/64bit/obs.dll
make
```
編譯完成後，依上述 Windows 安裝說明，將 "image-reaction" 資料夾（內含 `image-reaction.dll` 與 `data/`）放入 "C:\ProgramData\obs-studio\plugins\"。
