# midway_pic_tool_py
A Python tool to read and (optionally) modify serial number and/or date from PIC16C57/PIC16F57 dumps used in many Williams/Atari/Midway games  
Fork & port of original C version by Pat Daderko (DogP) based on MAME midway_serial_pic_device::generate_serial_data from midwayic.cpp by Aaron Giles

**Usage:** midway_pic_tool <filename> -s [new SN (0-999999)] -m [new MM (1-12)] -d [new DD (1-31)] -y [new YYYY (1980-2155)]  --gameid [new game ID (0-999]
Enter 'random' as a serial number parameter to receive a random number.

Example output:
```
./midway_pic_tool.py 315_sf_rush.u96 -n -s random -m 5 -d 18 -y 2005
Game detected: San Francisco Rush
Original S/N: 315102134
Original date: 1/23/1997
Random serial requested
New S/N: 315814108
New date: 5/18/2005
Saving to 315_sf_rush_315814108_5_18_2005.u96
```

**NOTES:**
* Entering new values modifies original file unless -n is specified.
* KLOV user neSneSgB successfully tested this tool, though noted that SF Rush 2049 SE errored on boot with "IOASIC PROBLEM" if the first 3 digits of the S/N were changed.
* The ability to modify the first 3 numbers of the serial is a separate parameter to prevent accidental modification as some games verify this ID and will refuse to work if it is wrong.

The license for this code is BSD 3-Clause as it uses BSD 3-Clause licensed code from MAME midwayic.cpp by Aaron Giles.
