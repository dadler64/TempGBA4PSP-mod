# -x assembler-with-cpp
# gpSP makefile
# Gilead Kutnick - Exophase
# Updated by Dadler


# Global definitions
EBOOT_TITLE = TempGBA mod
PROJECT_NAME = TempGBA
SRC_DIR = ../src
RES_DIR = ../res
PSPSDK = ${shell psp-config --pspsdk-path}
PREFIX = ${shell psp-config --psp-prefix}

BUILD_PRX = 1
ENCRYPT = 1

PSP_FW_VERSION = 371
PSP_LARGE_MEMORY = 1


PSP_EBOOT_ICON = $(RES_DIR)/ICON0.png
PSP_EBOOT_PIC1 = $(RES_DIR)/PIC1.png
#PSP_EBOOT_SND0 = $(RES_DIR)/SND0.at3
PSP_EBOOT_TITLE = $(EBOOT_TITLE)

EXTRA_TARGETS = EBOOT.PBP

COMMON_FILE = \
 common.h cpu.h memory.h video.h input.h sound.h main.h message.h \
 mh_print.h gui.h zip.h png.h \ ku_bridge.h exception.h ch_print.h

MAINOBJS = \
 cpu.o memory.o video.o input.o sound.o main.o message.o mh_print.o \
 gui.o zip.o png.o mips_stub.o ku_bridge.o exception.o cheats.o \
 ch_print.o

OBJZ = adler32.o crc32.o deflate.o infback.o inffast.o inflate.o inftrees.o trees.o zutil.o
OBJG = compress.o uncompr.o gzclose.o gzlib.o gzread.o gzwrite.o

OBJS = $(MAINOBJS) $(OBJZ) $(OBJG)

TARGET = $(PROJECT_NAME)

VPATH = $(SRC_DIR) $(SRC_DIR)/zlib

CFLAGS = \
 -O2 -G0 \
 -march=allegrex -mfp32 -mgp32 -mlong32 -mabi=eabi \
 -fomit-frame-pointer -fstrict-aliasing \
 -falign-functions=32 -falign-loops -falign-labels -falign-jumps \
 -Wall -Wundef -Wpointer-arith -Wbad-function-cast -Wwrite-strings -Wmissing-prototypes -Wsign-compare -Werror \
 -DZLIB_CONST

ASFLAGS = ${CFLAGS}

INCDIR = ../SDK/include $(SRC_DIR) $(SRC_DIR)/zlib $(SRC_DIR)/libpower
LIBDIR = ../SDK/lib

LIBS = $(SRC_DIR)/libpower/libpsppower.a -lpspgu -lpsprtc -lpspaudio -lpspkubridge

include ${PSPSDK}/lib/build.mak

