# I use the built-in rules from GNU Makefile, which are handy.

# Set linked binaries as c++ dependencies
LINK.o = $(LINK.cc)


DEBUG = 1
EXECUTABLE_NAME = main

# compiler configuration
CXX_STANDARD = -std=c++17
CXX_WARNINGS = -Wall -Wextra -pedantic
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) $(CXX_STANDARD)
LDFLAGS = 

# example conditional
ifeq ($(DEBUG), 1)
	CXXFLAGS += -g -O0
else
	CXXFLAGS += -O3
endif

COMPILER_CALL = $(CXX) $(CXXFLAGS)

build: $(EXECUTABLE_NAME)
	@echo The compiler call was $(COMPILER_CALL)
	@echo all built

clean:
	rm -f *.o $(EXECUTABLE_NAME)

execute: build
	./main

# Set dependencies
$(EXECUTABLE_NAME): main.o my_lib.o
	$(CXX) -o $@ $^ $(LDFLAGS)

main.o: main.cc my_lib.h
my_lib.o: my_lib.cc

# Declare non produced targets
.PHONY: build clean execute
