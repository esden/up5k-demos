# Port of the MIST NES core to iCEBreaker

This port of the NES MIST core is currently designed for the iCEBreaker FPGA
development board, with an iCEBreaker 12bit DVI Pmod for video output and
gamepads & audio Pmod for SNES controller.

Currently it can run any NROM, MMC1, UNROM or CNROM game requiring either less
than 64kB PRG and CHR ROM, or less than 128kB PRG ROM and 8kB CHR RAM. Sound is
a tiny bit big for the 5k UltraPlus so is not included. By removing all the
mappers - and some registers needed for reliable performance - you can  just
about get it to fit  but it uses every single PLB in the device.

It would be much better suited to a 8k board with more external RAM.  Then you
would have room for bigger games (up to the size of the board's RAM), more
mapper support (e.g. MMC3) and sound. The only changes needed would be changing
cart_mem to use external RAM instead of UltraPlus SPRAM, and creating a new
Makefile and pcf file.

'Streaming' games from SQI flash might be just about doable from a timing point
of view but I don't think there are enough PLBs available at present on the 5k,
and it would probably be quite a bit of work for it to work reliably.

Credit to the original developer of the NES core, Ludvig Strigeus for making
such an awesome project, to Dave Shah for the initial port of the core to
iCE40UP5k and Lawrie Griffiths for the initial port to the iCEBreaker! Like the
original core this is licensed under the GNU GPL.

# Building and flashing

Building the core is pretty easy just run:

```
make
```

You can flash the NES core to your iCEBreaker by just running:

```
make prog
```

You will need a NES ROM to play a game. There are plenty free homebrew games as
well as commercial games for the NES that provide ROMs for you to play in an
emulator.

Just copy the `*.nes` ROM file into the `rom` subdirectory. Make sure to name
the file to match the following pattern `game_*.nes` you might want to avoid
special characters and spaces in the ROM image name to prevent possible issues.

After you copy a rom into the directory just run:

```
make prog_games
```

This will generate `.bin` files out of the `game_*.nes` files and flash the
resulting combined binary to your iCEBreaker.
 
