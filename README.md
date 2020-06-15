# Application Board 2.0 recovery using Mac OS

## Pre-requistes

- [BOSSA tool](https://github.com/shumatech/BOSSA/releases) 
- [X-code command line tools](https://developer.apple.com/download/more/?=xcode)
- [Homebrew](https://brew.sh/)
  - Once brew is installed, install the `libusb` and `dfu-util` by running the following command in the terminal
  
```terminal
brew install libusb dfu-util
```

## Board references

![ApplicationBoard20Recovery](Application%20Board%202.0%20Recovery.jpg "Application Board 2.0 Recovery")

## Steps

1) Install the Bossa tool. For ease of access the installer has been made available as part of this repository. You can always find the latest version from the [release](https://github.com/shumatech/BOSSA/releases) folder of the tool's repository.

2) Erase the flash of the microcontroller and load the ROM bootloader by shorting J203 with a jumper cable. Restart the board with the pins shorted and wait for up to 5 seconds, and then power off the board again.

3) Run the below command and then power on the board and run it again. Note the additional device detected.

```terminal
ls /dev/tty.*
```

> Note: If no device is detected, check the cables and connection to the board.

4) Assuming the BOSSA tool is installed, run the following on the terminal in this directory

```terminal
bossac -e -w -v -b -p /dev/tty/"device name" Bootloader_APP2.0.bin
```

1) Upon completion of the bootloader firmware update, restart the board with Button 2 pressed.

2) Navigate to the app20-flash directory and build the app20-flash tool by running `make` in the terminal.
3) Use the tool to load the application board firmware by executing the following in the app2.0

```
./app20_flash DevelopmentDesktop_2.0_Firmware_V3.4.fwu2
```

8) Restart the board.
