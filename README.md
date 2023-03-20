# Setting up Frida-Server in Termux

## Introduction
This guide will help you install and set up Frida-Server in Termux without any errors.

## Requirements
- A rooted Android device
- Termux installed on your Android device
- Install Termux according to your phone's arch [here](https://apkcombo.com/termux/com.termux/).
- Install MT Manager [here](https://apkcombo.com/mt-manager/bin.mt.plus/).

## To Start with Termux
- Give storage permission to Termux by using this command
 ```
 termux-setup-storage
```
- Update dependencies in Termux
```
 pkg update
pkg upgrade
```
- Install python by using this command
```
pkg install python
```
- Install sudo by by using this command
```
pkg install tsu
```

## Installation Steps
1. Download the Frida-core devkit
- For arm64 arch [here](https://github.com/frida/frida/releases/download/16.0.11/frida-core-devkit-16.0.11-android-arm64.tar.xz).
- For arm arch [here](https://github.com/frida/frida/releases/download/16.0.11/frida-core-devkit-16.0.11-android-arm.tar.xz).
2. Extract the contents of the downloaded file to any path you desire.I am using MTmanager in my case, You can use any filemanager.For instance, let's extract it to `/storage/emulated/0/devkit`.
3. Open Termux and paste the following command: `export FRIDA_CORE_DEVKIT=/storage/emulated/0/devkit`
4. Install frida-tools using python: `pip install frida-tools`
5. Download Frida-server from [here](https://github.com/frida/frida/releases/download/16.0.11/frida-server-16.0.11-android-arm64.xz).
6. Extract the contents of the downloaded file and rename it to `frida-server`.
7. Move the `frida-server` file to `/data/local/tmp/` folder and give it 777 permissions or in termux change directory by using `cd /data/local/tmp/` cmd then use `chmod 777 *` cmd to grant rwx permissions for frida-server.
8. Open termux then change directory to /data/local/tmp/ then use tsu like this
```
cd /data/local/tmp/
tsu
``` 
9. Start the Frida-server by opening by running this command:
```
./frida-server -l 127.0.0.1:1234
```
10. Open another session in Termux and run the following command to start Frida with your desired package name and script:
```
frida -H 127.0.0.1:1234 -no-pause -f pkg.name -l script.js
```
Note: Use android 10 os with close to aosp rom like pixel roms etc to run frida-server without any errors!

Congratulations! You have successfully set up Frida in Termux on your Android device.
