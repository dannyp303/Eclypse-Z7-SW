# Cross-compiler
CC = arm-linux-gnueabihf-gcc
CXX = arm-linux-gnueabihf-g++

# Directories
SRC_DIR = src
BUILD_DIR = build
INCLUDE_DIRS = -I../zmodlib/Zmod -I../zmodlib/ZmodADC1410 -I../zmodlib/ZmodDAC1411 -I../libuio

# Source files
SRCS = $(SRC_DIR)/main.cpp \
       ../libuio/libuio.c \
       ../zmodlib/Zmod/linux/flash/flash.c \
       ../zmodlib/Zmod/linux/utils.c \
       ../zmodlib/Zmod/zmod.cpp \
       ../zmodlib/ZmodADC1410/zmodadc1410.cpp \
       ../zmodlib/ZmodDAC1411/zmoddac1411.cpp \
       ../zmodlib/Zmod/linux/reg/reg.c \
       ../zmodlib/Zmod/linux/dma/dma.c \
       ../zmodlib/Zmod/linux/dma/libaxidma.c

# Output binary
TARGET = $(BUILD_DIR)/zmodadc1410_demo

# Compiler flags
CXXFLAGS = -Wall -O2 $(INCLUDE_DIRS) -DLINUX_APP -fpermissive

# Linker flags
LDFLAGS = 

# Object files
OBJS = $(patsubst %.cpp,%.o,$(patsubst %.c,%.o,$(SRCS)))

# Build target
all: $(TARGET)

$(TARGET): $(OBJS)
	@mkdir -p $(BUILD_DIR)
	$(CXX) $(CXXFLAGS) -o $@ $^ $(LDFLAGS)

# Compile source files to object files
%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

%.o: %.c
	$(CC) $(CXXFLAGS) -c $< -o $@

# Clean up
clean:
	rm -rf $(BUILD_DIR) $(OBJS)

.PHONY: all clean 