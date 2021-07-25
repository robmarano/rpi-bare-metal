# Step 3
## Bare Metal Raspberry Pi 3b+ Development

### Writing to the end-user through a serial connection, i.e., UART
Read bztscr's tutorial step for [Tutorial 03 - UART](https://github.com/bztsrc/raspi3-tutorial/blob/master/03_uart1/README.md) as well as isometimes's tutorial step for [Writing a bare metal OS for Raspberry Pi 4](https://github.com/isometimes/rpi4-osdev/blob/master/part3-helloworld/README.md)

This step demonstrates how to bootstrap the rPi with boot.S and run main() in C which writes to you the user via STDOUT via QEMU emulator using the UART0, which can be used with QEMU