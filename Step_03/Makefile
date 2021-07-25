#
# Reusable Makefile to build bare metal rPi executable logic
#
CPU_TYPE := cortex-a53+nosimd
CPU := cortex-a53
LLVMPATH := /usr/local/opt/llvm/bin
LINKER := link.ld
KERNEL := kernel8
CSRCS = $(wildcard *.c)
COBJS = $(CSRCS:.c=.o)
SSRCS = $(wildcard *.S)
SOBJS = $(SSRCS:.S=.o)
RUN_ARGS = -cpu $(CPU) -M raspi3 -kernel $(KERNEL).img -serial null -serial stdio

CFLAGS = -Wall -O2 -ffreestanding -nostdinc -nostdlib -mcpu=$(CPU_TYPE)

# Debugging - print out variable
#$(info    CSRCS = $(CSRCS) ; COBJS = $(COBJS))
#$(info    SSRCS = $(SSRCS) ; SOBJS = $(SOBJS))

all: clean $(KERNEL).img

%.o: %.S
	$(LLVMPATH)/clang --target=aarch64-elf $(CFLAGS) -c $< -o $@

%.o: %.c
	$(LLVMPATH)/clang --target=aarch64-elf $(CFLAGS) -c $< -o $@


$(KERNEL).img: $(SOBJS) $(COBJS)
	$(LLVMPATH)/ld.lld -m aarch64elf -nostdlib $^ -T $(LINKER) -o $(KERNEL).elf
	$(LLVMPATH)/llvm-objcopy -O binary $(KERNEL).elf $@

.PHONY: clean
clean:
	rm $(KERNEL).img $(KERNEL).elf *.o >/dev/null 2>/dev/null || true

run: clean $(KERNEL).img
	qemu-system-aarch64 $(RUN_ARGS)


# Portions of this file are 
# Copyright (C) 2018 bzt (bztsrc@github)
# https://github.com/bztsrc/raspi3-tutorial/blob/master/01_bareminimum/Makefile.clang
#
# Permission is hereby granted, free of charge, to any person
# obtaining a copy of this software and associated documentation
# files (the "Software"), to deal in the Software without
# restriction, including without limitation the rights to use, copy,
# modify, merge, publish, distribute, sublicense, and/or sell copies
# of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be
# included in all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
# EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
# MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
# NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
# HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
# DEALINGS IN THE SOFTWARE.
#
#
