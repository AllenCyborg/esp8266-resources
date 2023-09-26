# esp8266-resources
Some resources for reference when using esp8266 based boards.
[Installing AT Firmware on Esp01](https://www.sigmdel.ca/michel/ha/esp8266/ESP01_AT_Firmware_en.html)

# 1. UART not working on AT firmware version 2
Problem: Firmware v 2.2.x does not return messages when AT commands are sent.

Cause: AT 2.x changed the UART0 pins from GPIO1 & GPIO3 to GPIO15 & GPIO13, requiring extra connections to the new pins as most boards are still wired up with pins 1 & 3.

GitHub [issue](https://github.com/espressif/esp-at/issues/755)

esp forum post with [solution](https://www.esp32.com/viewtopic.php?t=26869&start=10)

## Solution
The solution is to restore UART0 pins by either compiling with the changes or modifying the bin files.
The modification can be done using the [at.py](https://github.com/espressif/esp-at/tree/master/tools) tool.
[Instructions to modify the existing binary](https://www.esp32.com/viewtopic.php?t=26869&start=10#:~:text=There%20is%20no%20need%20to%20compile,Firmware%20on%20an%20ESP%2D01S.)

### Already Modified 2.2.0
A custom bin of 2.2.0 with UART restored can be found at:
https://github.com/CytronTechnologies/esp-at-binaries

