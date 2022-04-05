# ==============================================================================
# Generic makefile for large Rust/C projects
# ==============================================================================

# Define compilers
PREFIX = arm-none-eabi
CC = $(PREFIX)-gcc
CPP = $(PREFIX)-g++
LD = $(PREFIX)-gcc
AS = $(PREFIX)-as
CP = $(PREFIX)-objcopy
OD = $(PREFIX)-objdump

# Optimization
# O0 -> No optimization
# O1, O2, O3 -> Speed optimizations
# Os -> Size optimization
# Og -> Optimize for debugging
O_LEVEL = -O0

# Directories
COMDIR    := ../common
SRCDIR    := src
INCDIR    := inc
OBJDIR    := obj
LIBDIR    := ../../lib
TARGETDIR := ../../bin

# Define target
TARGET = $(TARGETDIR)/app

# Add common directories
SRCDIR += $(wildcard $(COMDIR)/src/*/)
INCDIR += $(wildcard $(COMDIR)/inc/*/)

# Find all source files and declare objects
SRC_C := $(shell find $(SRCDIR) -name [^.]*.c)
SRC_C += $(shell find $(SRCDIR) -name [^.]*.cpp)

# Define include paths
INCLUDES := $(INCDIR)
INCFLAGS := $(addprefix -I, $(INCLUDES))

# Get info from packages
LIBMAKES := $(shell find $(LIBDIR)/*/Makefile)
$(foreach SUBMAKE, $(LIBMAKES), $(eval include $(SUBMAKE)))

