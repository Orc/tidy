OBJECTS=access.o alloc.o attrask.o attrdict.o attrget.o attrs.o buffio.o \
	charsets.o clean.o config.o entities.o fileio.o gdoc.o iconvtc.o \
	istack.o language.o lexer.o mappedio.o message.o parser.o pprint.o \
	sprtf.o streamio.o tagask.o tags.o tidylib.o tmbstr.o utf8.o win32tc.o

CFLAGS=-I. -I../include
DESTDIR=$(PREFIX)/bin
INSTALL=install -c


tidy:  tidy.o $(OBJECTS)
	$(CC) $(CFLAGS) -o tidy tidy.o $(OBJECTS)

tidy.o:  ../console/tidy.c
	$(CC) $(CFLAGS) -c -o tidy.o $<

clean:
	rm -f $(OBJECTS) tidy

install: tidy
	$(INSTALL) tidy $(DESTDIR)

