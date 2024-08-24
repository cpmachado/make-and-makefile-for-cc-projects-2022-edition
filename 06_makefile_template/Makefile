# I use the built-in rules from GNU Makefile, which are handy.

# Set linked binaries as c++ dependencies
LINK.o = $(LINK.cc)


DEBUG ?= 1
EXECUTABLE_NAME ?= main

INCLUDE_DIR = include
SRC_DIR = src
BUILD_DIR = build

# compiler configuration
CXX_STANDARD = -std=c++17
CXX_WARNINGS = -Wall -Wextra -pedantic
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) $(CXX_STANDARD)
CPPFLAGS = -I $(INCLUDE_DIR)
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


CXX_SRC = $(wildcard $(SRC_DIR)/*.cc)
CXX_OBJ = $(patsubst $(SRC_DIR)/%.cc, $(BUILD_DIR)/%.o, $(CXX_SRC))

build: $(BUILD_DIR)/$(EXECUTABLE_NAME)
	@echo all built

clean:
	rm -rf build

execute: build
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

# Set dependencies
$(BUILD_DIR)/$(EXECUTABLE_NAME): $(CXX_OBJ)
	$(CXX) -o $@ $^ $(LDFLAGS)

$(BUILD_DIR)/main.o: $(SRC_DIR)/main.cc $(INCLUDE_DIR)/my_lib.h

$(BUILD_DIR)/%.o: $(SRC_DIR)/%.cc 
	mkdir -p $(BUILD_DIR)
	$(COMPILER_CALL) $(CPPFLAGS) -c -o $@ $<

# Declare non produced targets
.PHONY: build clean execute
