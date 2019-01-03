# Working with kendryte K210

## Information
* https://github.com/kendryte/kendryte-doc-datasheet/blob/master/en/SUMMARY.md

## Downloads
https://kendryte.com/downloads/

* SDK for first test : Kendryte K210 Standalone SDK
* Toolchain as per the OS : RISC-V 64bit toolchain for Kendryte K210_ubuntu_amd64

Example Code

https://github.com/kendryte/kendryte-standalone-demo/tree/master/hello_world

Python application for firmware flashing

https://github.com/kendryte/kflash.py

## Build
Copy the hello_world example in "kendryte-standalone-sdk-xx/src"

To build the project

```bash
cd kendryte-standalone-sdk-xx
mkdir build
cd build
cmake .. -DPROJ=hello_world -DTOOLCHAIN=/YOUR_PATH/kendryte-toolchain/bin && make
```
In case of error while loading shared libraries: libmpfr.so.4
```bash
sudo ln -s /usr/lib/x86_64-linux-gnu/libmpfr.so.6 /usr/lib/x86_64-linux-gnu/libmpfr.so.4
```

## Flash
Add user to dialout group on Linux for serial port access
```bash
sudo usermod -a -G dialout $(whoami)
```
Logout and login

```bash
python3 kflash.py -p /dev/ttyUSB0 firmware.bin
```
Flash and open term
```bash
python3 kflash.py -p /dev/ttyUSB0 -t firmware.bin
```
