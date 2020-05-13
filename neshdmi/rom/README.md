Copy the NES ROM files into this directory. Make sure that they all follow the
pattern of `game_*.nes`.

You can build the `games.bin` by running `make` in this directory.

Runnig `make prog` will flash the resulting `games.bin` at offset `1Mb` offset
into the FPGA board FLASH.

