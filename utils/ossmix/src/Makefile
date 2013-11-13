# Makefile for Open Sound System module ossmix

OSFLAGS=-Wall -DOSS_LITTLE_ENDIAN
OSSLIBDIR="/usr/lib/oss"
#THISOS=kernel/OS/Linux
CFLAGS+=-O
CSOURCES=ossmix.c

CFLAGS += -Wall

obj = ossmix.o


all: 
	$(CC) $(CFLAGS) $(EXTRA_CFLAGS) -s -o $(DESTDIR) $(OBJECTS) $(LIBRARIES) $(LDFLAGS) ossmix.c 
clean:
	rm -f *.o
install:
	sleep 1
