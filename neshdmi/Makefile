PROJ = nes

ADD_CLEAN_SUBDIR = rom

TOP = NES_ice40
PIN_DEF = up5k.pcf
DEVICE = up5k
ADD_SRC = $(wildcard *.v)
FREQ = 8
#USE_ARACHNEPNR = Y

include main.mk

prog_games:
	make -C rom prog

PHONY: prog_games