
bin ?= hello
mode ?= debug

# 根据mode的值设置profile变量
ifeq ($(mode),release)
	profile := --release
else
	profile := 
endif

elf := ./target/thumbv7m-none-eabi/$(mode)/$(bin)

qemu := /root/qemu/qemu-8.2.2/build/qemu-system-arm

build:
	cargo build --bin $(bin) $(profile)

run: build
	$(qemu) \
  -cpu cortex-m3 \
  -machine stm32vldiscovery \
  -nographic \
  -kernel $(elf)


GDB_PATH := /root/qemu/gdb-14.2/build-arm-eabi/bin/arm-none-eabi-gdb
gdb := RUST_GDB=$(GDB_PATH) rust-gdb

gdbserver:
	$(qemu)\
		-cpu cortex-m3 \
		-machine stm32vldiscovery \
		-nographic \
		-kernel $(elf) \
		-s -S

gdbclient: 
	$(gdb) -ex 'file $(elf)' -ex 'target remote localhost:1234'

