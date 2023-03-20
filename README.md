# Setting up Frida in Termux

## Introduction
This guide will help you install and set up Frida in Termux without any errors.

## Requirements
- A rooted Android device
- Termux installed on your Android device

## Installation Steps
1. Download the Frida-core devkit from [here](https://github.com/frida/frida/releases/download/16.0.11/frida-core-devkit-16.0.11-android-arm64.tar.xz).
2. Extract the contents of the downloaded file to any path you desire. For instance, let's extract it to `/storage/emulated/0/devkit`.
3. Open Termux and paste the following command: `export FRIDA_CORE_DEVKIT=/storage/emulated/0/devkit`
4. Install frida-tools using python: `pip install frida-tools`
5. Download Frida-server from [here](https://github.com/frida/frida/releases/download/16.0.11/frida-server-16.0.11-android-arm64.xz).
6. Extract the contents of the downloaded file and rename it to `frida-server`.
7. Move the `frida-server` file to `/data/local/tmp/` folder and give it 777 permissions.
8. Start the Frida-server by opening a new session in Termux and running either of these commands:
```
./frida-server -l 127.0.0.1:1234
./frida-server -l localhost:1234
```
9. Open another session in Termux and run the following command to start Frida with your desired package name and script:
```
frida -H 127.0.0.1:1234 -no-pause -f pkg.name -l /data/local/tmp/script.js 
frida -H localhost:1234 -no-pause -f pkg.name -l /data/local/tmp/script.js
```
Note: The script should be present in `/data/local/tmp` folder or you should define the path where it is stored.

Congratulations! You have successfully set up Frida in Termux on your Android device.
