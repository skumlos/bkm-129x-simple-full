A full sized version of the BKM-129X compatible board

Revision D

Should be able to be created at ~$40, with the ADG1611BRUZ being the most expensive component.
Note that DG1411EEQ is pin-compatible with a slighly higher Ron.

This requires an Arduino Nano v3 *or* the ATMEGA328PB mounted, which is then loaded with the
latest BKM-129X-MCU code from https://github.com/skumlos/bkm-129x-mcu

The has 4 switches to be able to turn internal 75 Ohm termination on out pass signal through to the output BNCs. You 
can choose to set all switches down, and then terminate with external termination resistors. If you wish to omit the
switches altogther, bridge the two pins bottom left of each switch (when viewed component side, BNCs to left). 
A 0 Ohm 0805 should be able to reach here I guess.

Connections from top to bottom when viewing component side, with BNCs to the left:
               _______________________________________
            __| _                                     |
Y/G IN     |___|_|                                    |
            __| _                                     |
Y/G OUT    |___|_|                                   _|
            __| _                                   | |
B-Y/B IN   |___|_|                                  | |
            __| _                                   | |
B-Y/B OUT  |___|_|                                  | |
            __| _                                   | |
R-Y/R IN   |___|_|                                  | |
            __| _                                   | |
R-Y/R OUT  |___|_|                                  | |
            __| _                                   |_|
SYNC IN    |___|_|                                    |
            __| _                                     |
SYNC OUT   |___|_|                                    |
              |_______________________________________|

Just like the original BKM-129X.

For more information go to https://immerhax.com/?p=422

You are welcome to clone, produce and sell hardware based on this. Please keep changes and so on open source.

Cool kids give credit where due.

---------

Programming the onboard ATMEGA328PB is a little different than when using a pre-made Arduino board.
The reason for this is that the fuses of the ATMEGA aren't set when the MCU leaves the factory.
Thus to program it, you will need ATMEGA328PB support in the Arduino IDE. The easiest way is to
install the MiniCore board support package (through the Boards Manager), for installation
check the "How to install" at https://github.com/MCUdude/MiniCore.
When MiniCore is available,  select the ATMEGA328 under MiniCore in the board menu, then select
"External 16 MHz" in Clock, disable BOD, select ATMEGA328PB in Variant, select No bootloader.
Then press "Burn bootloader" (assuming your programmer and so on is already setup). This will
program the fuses. Last, upload the sketch by pressing "Upload using programmer". If you don't
do this, nothing will work, because the MCU won't know how to use the external clock and so on.


---------

Should be compatible with basically all monitors that accept the original BKM-129X

Check the MCU code for verified compatibility.

---------

Board revision history:

D: Change hole size in backplane connector to accomodate larger pin sizes,
   support 1117 LDOs, change to Kicad 5 footprints, general cleanup

C: Fixed THS7374 filter bypass.

B: Added onboard MCU option

A: Initial version

---------

Copyright © 2022 Martin Hejnfelt <martin@hejnfelt.com>
This work is free. You can redistribute it and/or modify it under the
terms of the Do What The Fuck You Want To Public License, Version 2,
as published by Sam Hocevar. See the LICENSE file for more details.

