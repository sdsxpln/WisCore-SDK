.SUFFIXES : .x .o .c .s

CUR_PATH = $(shell pwd)
CROSS_TOOLCHAIN ?= /opt/mipsel-openwrt-linux-4.8.3/mipsel-4.8.3.2
UNAME ?= mt7628_op

LIB += -L$(CROSS_TOOLCHAIN)/$(TARGET_DIR)/usr/lib #-L$(CROSS_TOOLCHAIN) 
INC += -I$(CROSS_TOOLCHAIN)/$(TARGET_DIR)/usr/include -I../common/include
CC = mipsel-openwrt-linux-gcc -O2 -D_LARGEFILE64_SOURCE=1 $(INC)

LDFLAGS=$(LIB)
STRIP=mipsel-openwrt-linux-strip

export STAGING_DIR=$(CROSS_TOOLCHAIN)

TARGET = tunnel
SRCS := ../common/src/RKIoctrlApi.c tunnel.c \
		../common/src/RKUartApi.c \
		../common/src/RKLog.c
		
EXT_LIBS+=-lpthread
		
all:  tunnel

tunnel: $(SRCS)
	$(CC) $(LDFLAGS) $(EXT_LIBS) -o $(TARGET) $(SRCS)
	$(STRIP) $(TARGET) 

clean:
	@rm -f *.o -v
	@rm -f $(TARGET) -v

distclean: 
	@rm -f $(TARGET)-*


