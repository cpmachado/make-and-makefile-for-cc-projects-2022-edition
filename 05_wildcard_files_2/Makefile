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
	EXECUTABLE_NAME := $(EXECUTABLE_NAME)-debug
else
	CXXFLAGS += -O3
	EXECUTABLE_NAME := $(EXECUTABLE_NAME)-release
endif

COMPILER_CALL = $(CXX) $(CXXFLAGS)

CXX_SRC = $(wildcard *.cc)
CXX_OBJ = $(patsubst %.cc, %.o, $(CXX_SRC))

build: $(EXECUTABLE_NAME)
	@echo The compiler call was $(COMPILER_CALL)
	@echo all built

clean:
	rm -f $(CXX_OBJ) $(EXECUTABLE_NAME)

execute: build
	./main

# Set dependencies
$(EXECUTABLE_NAME): $(CXX_OBJ)
	$(CXX) -o $@ $^ $(LDFLAGS)

main.o: main.cc my_lib.h
my_lib.o: my_lib.cc

# Declare non produced targets
.PHONY: build clean execute
