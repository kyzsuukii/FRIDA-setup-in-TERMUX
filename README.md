# Setting up FRIDA in Termux

## Introduction
This guide will help you install and set up enviroment for [FRIDA](https://github.com/frida/frida/) in Termux.

## Requirements
- A rooted Android device
- Termux installed on your Android device
- Install Termux according to the architecture of your device [here](https://github.com/termux/termux-app/releases/).

## To Start with Termux
- Grant storage permission to Termux by using this command:
 ```
$ termux-setup-storage
```
- Update and install all required dependencies in Termux.
```
$ pkg update
$ pkg install python tsu -y
```
## Guide to Installing [FRIDA](https://github.com/frida/frida/)
1. First, create a folder named `frida-devkit` and navigate to that directory using 'cd frida-devkit'.
2. Download the Frida-core devkit [here](https://github.com/frida/frida/releases/).
 * Select based on the architecture of your device.
 * I recommend using wget to download from the releases page.
```
$ wget https://github.com/frida/frida/releases/latest/download/frida-devkit-android-ARCH-VERSION.tar.xz
```
 * Replace `ARCH` with the architecture of your device.
 * Replace `VERSION` with the version number of the latest release.
3. After downloading the devkit, extract its contents using the following command:
```
tar -xfv frida-devkit-android-ARCH-VERSION.tar.xz
```
 * Again, replace `ARCH` with the architecture of your device.
 * Also, replace `VERSION` with the version number of the devkit you downloaded.
4. Install frida and frida-tools using pip with following command: 
```
$ FRIDA_CORE_DEVKIT=$PWD pip install frida frida-tools
```
 * Make sure you are in the `frida-devkit` directory and that the Frida devkit has been extracted in the same directory
5. Congratulations, Frida has been successfully installed on Termux!
## How to setup FRIDA-SERVER
1. Download Frida-server from releases [here](https://github.com/frida/frida/releases/).
 * Again, I recommend using wget to download from the releases page.
```
$ wget https://github.com/frida/frida/releases/latest/download/frida-server-android-ARM-VERSION.tar.xz
```
 * Replace `ARCH` with the architecture of your device.
 * Replace `VERSION` with the version number of the latest release.
2. After downloading frida-server, extract it and rename the result to `frida-server` using the following command:
```
$ mv frida-server-android-ARCH-VERSION frida-server
```
 * Again, Replace `ARCH` with the architecture of your device.
 * Replace `VERSION` with the version number of the frida-server you downloaded.
3. give 755 permission to the frida-server file using the chmod command, run the following command:
```
chmod 755 frida-server
```
 * This will set the file permissions to allow the owner to read, write, and execute the file, and allow others to read and execute the file.
4. then move frida-server to `$PREFIX/bin` by following command
$ mv frida-server $PREFIX/bin
5. Now, frida-server is ready to be fired up.

## How to use
1. Enter root mode using `tsu` command
```
$ tsu
```
2. Navigate to the `/data/local/tmp directory`, use the following command:
```
$ cd /data/local/tmp/
```
3. Run frida-server, using command:
```
$ frida-server --listen=localhost:27042 -C
```
3. Open a new session on Termux, swipe the left side of the screen and open a new session. You can then use Frida in the new session.
4. For using frida with frida-server you need use `-H` options. ex:
 * spawn mode
```
$ frida -H localhost:27042 -f package.name -l your_script.js
```
 * attach mode
 ```
 $ frida -H localhost:27042 -n AppName -l your_script.js
 ```