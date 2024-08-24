# I use the built-in rules from GNU Makefile, which are handy.

# Set linked binaries as c++ dependencies
LINK.o = $(LINK.cc)

build: main
	@echo all built

clean:
	rm -f *.o main

execute: build
	./main

# Set dependencies
main: main.o my_lib.o
main.o: main.cc my_lib.h
my_lib.o: my_lib.cc

# Declare non produced targets
.PHONY: build clean execute
