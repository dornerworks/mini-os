#
# arm architecture specific makefiles.
# It's is used for arm32 and arm64
#

TOPLEVEL_DIR = $(CURDIR)/../..
include ../../Config.mk

# include arch.mk has to be before mini-os.mk!

include arch.mk
include ../../minios.mk

# Sources here are all *.c *.S without $(MINIOS_TARGET_ARCH).S
# This is handled in $(HEAD_ARCH_OBJ)
ARCH_SRCS := $(sort $(wildcard *.c))

# The objects built from the sources.
ARCH_OBJS := $(patsubst %.c,$(OBJ_DIR)/%.o,$(ARCH_SRCS))

ARCH_OBJS += hypercalls32.o

all: $(OBJ_DIR)/$(ARCH_LIB)

# $(HEAD_ARCH_OBJ) is only build here, needed on linking
# in ../../Makefile.
$(OBJ_DIR)/$(ARCH_LIB): $(ARCH_OBJS) $(OBJ_DIR)/$(HEAD_ARCH_OBJ)
	@echo 'Hello'
	$(AR) rv $(OBJ_DIR)/$(ARCH_LIB) $(ARCH_OBJS)

clean:
	rm -f $(OBJ_DIR)/$(ARCH_LIB) $(ARCH_OBJS) $(OBJ_DIR)/$(HEAD_ARCH_OBJ)

