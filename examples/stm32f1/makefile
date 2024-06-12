
build:
	cargo build --bin blinky --release

qemu:
	/root/qemu/qemu-8.2.2/build/qemu-system-arm \
  -cpu cortex-m3 \
  -machine stm32vldiscovery \
  -nographic \
  -kernel ./target/thumbv7m-none-eabi/release/blinky


.PHONY: build qemu
