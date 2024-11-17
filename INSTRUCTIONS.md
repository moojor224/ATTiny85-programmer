# How to program the ATTiny85

## Required materials:

 - arduino nano
 - 1x 10k ohm resistor
 - 2x 330 ohm resistor
 - 3.3v LED
 - 10uF electrolytic capacitor
 - 100nF ceramic capacitor

 1. add boards json: https://raw.githubusercontent.com/porrey/Snapduino/IDE/package_porrey_snapduino_index.json
 2. prepare arduino nano (one-time only)
    1. select Arduino Nano board/port
    2. turn off cap switch
    3. plug in usb to arduino nano
    4. `File > Examples > ArduinoISP > ArduinoISP`
    5. upload program
    6. turn on cap switch
 3. burn bootloader (one-time for each ATTiny85 chip)
    1. Select Snapduino
    2. Select COM Port for Arduino Nano
    3. Select programmer
       1. `Tools > Programmer > Arduino as ISP`
    4. Burn bootloader
       1. `Tools > Burn Bootloader`
 4. At this time, repeat step 3.4 for any other ATTiny85 chips
    1. If you need to burn the bootloader to a new chip after following steps 5 or reloading ArduinoIDE, start over from step 3.1, don't start from 3.4
 5. Calibrate bootloader for ATTiny85 (one-time only per ATTiny85 chip)
    1. Select Snapduino board
    2. Select FTDI adapter port
    3. Open serial monitor and set baud rate to 9600
    4. Unplug and replug the FTDI adapter if the Tiny Tuner text menu is not shown
    5. Wait for the `Tiny Tuner` menu to show up
    6. Send `x` until the calibration successful message shows up
       1. simply click on the text input box, type the letter x (lowercase) and press enter
       2. repeat
 6. Change `Arduino AVR Boards` board library version to `1.6.11` (this is because a bug was introduces in version 1.6.12 that prevents the ATTiny85 from being programmed with this method)
    1. Open the Boards Manager
       1. Via the sidebar menu, or `Tools > Board > Boards Manager`
    2. Search for `Arduino AVR Boards`
    3. Click on the version dropdown menu, then select `1.6.11`
    4. Click install
    5. NOTE: this step will cause Arduino IDE to prompt you to update your board libraries every time you open the app. It is important that you **DO NOT UPDATE THE `Arduino AVR Boards` LIBRARY**, or you will be unable to program the ATTiny85
 7. Upload program to ATTIny85 chip
    1. Plug ATTIny85 into programming section of board
    2. Plug usb into red FTDI adapter
    3. Select Snapduino board
    4. Select port for FTDI adapter
    5. Upload test program to verify functionality (optional)
       1. `File > Examples > 01.Basic`
       2. Replace the `LED_BUILTIN` variable with the number `2` (there should be 3 instances of `LED_BUILTIN`)
       3. Press upload button
       4. After uploading, the LED should blink on and off on repeat
    6. Upload actual production code, assuming that the test code