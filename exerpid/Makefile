prefix = /usr/local

all: src/pipe

src/pipe: src/pipe.c
	@echo "CFLAGS=$(CFLAGS)" | \
		fold -s -w 70 | \
		sed -e 's/^/# /'
	$(CC) $(CPPFLAGS) $(CFLAGS) $(LDCFLAGS) -o $@ $^

install: src/pipe
	install -D src/pipe \
		$(DESTDIR)$(prefix)/bin/pipe

clean:
	-rm -f src/pipe

distclean: clean

unistall:
	-rm -f $(DISTDIR)$(prefix)/bin/pipe
