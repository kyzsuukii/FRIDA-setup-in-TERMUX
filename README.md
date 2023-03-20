# Frida-Server Setup
Setup Frida-core devkit in order to install frida in termux without any errors!
Follow the steps below to install and use Frida in Termux without any errors:

Download the Frida-core devkit from here.
Extract the devkit to any directory you prefer. For example, /storage/emulated/0/devkit.
In Termux, run the command export FRIDA_CORE_DEVKIT=/path/to/devkit where /path/to/devkit is the path to the directory where you extracted the devkit.
Install frida-tools using the command pip install frida-tools.
Download the Frida-server from here and extract it.
Rename the extracted file to frida-server and move it to /data/local/tmp/.
Give the server executable permissions by running the command chmod 777 /data/local/tmp/frida-server.
Start the Frida-server by opening a new session in Termux and running either ./frida-server -l 127.0.0.1:1234 or ./frida-server -l localhost:1234.
In another Termux session, use the command frida -H 127.0.0.1:1234 -no-pause -f pkg.name -l /path/to/script.js or frida -H localhost:1234 -no-pause -f pkg.name -l /path/to/script.js to run the desired script. Note that the script should be present in /data/local/tmp or you should define the path to where it is stored.
