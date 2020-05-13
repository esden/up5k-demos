all: games.bin

GAMES = $(sort $(wildcard game*.nes))
IMAGES = $(GAMES:.nes=.bin)

games.bin: $(IMAGES)
	cat $^ > $@

game%.bin: game%.nes
	./nes2bin.py $< $@

prog: games.bin
	iceprog -o 1024k $<

clean:
	rm -f *.bin

PHONY: all prog clean