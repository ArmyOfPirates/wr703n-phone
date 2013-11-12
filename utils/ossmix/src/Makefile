# Makefile for Open Sound System module ossmix

OSFLAGS=-Wall -DOSS_LITTLE_ENDIAN
OSSLIBDIR="/usr/lib/oss"
THISOS=kernel/OS/Linux
CFLAGS+=-O
CSOURCES=ossmix.c

CFLAGS += -Wall

obj = ossmix.o


ossmix: 
	$(CC) $(CFLAGS) -s -o $(DESTDIR)/ossmix $(OBJECTS) $(LIBRARIES) $(LDFLAGS) 
clean:
	rm -f *.o
