OBJECTS=access.o alloc.o attrask.o attrdict.o attrget.o attrs.o buffio.o \
	charsets.o clean.o config.o entities.o fileio.o gdoc.o iconvtc.o \
	istack.o language.o lexer.o mappedio.o message.o parser.o pprint.o \
	sprtf.o streamio.o tagask.o tags.o tidylib.o tmbstr.o utf8.o win32tc.o

CFLAGS=-I. -I../include
DESTDIR=$(PREFIX)/bin
MANDIR=$(PREFIX)/man/man1
INSTALL=install -c


tidy:  tidy.o $(OBJECTS)
	$(CC) $(CFLAGS) -o tidy tidy.o $(OBJECTS)

tidy.o:  ../console/tidy.c
	$(CC) $(CFLAGS) -c -o tidy.o $<

clean:
	rm -f $(OBJECTS) tidy tidy.1 ../man/tidy-help.xml

install-man: tidy.1
	$(INSTALL) tidy.1 $(MANDIR)

$(MANDIR):
	mkdir -p $(MANDIR)

../man/tidy-help.xml: tidy
	./tidy -xml-help > ../man/tidy-help.xml

tidy.1: ../man/tidy1.xsl.in tidy ../man/tidy-help.xml $(MANDIR)
	(cd ../man; xsltproc tidy1.xsl.in tidy-help.xml) > tidy.1

install-bin: tidy
	$(INSTALL) tidy $(DESTDIR)

install: install-bin install-man

