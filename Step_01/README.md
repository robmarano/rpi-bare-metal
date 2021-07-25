# Step 1
## Bare Metal Raspberry Pi 3b+ Development

### My environment
I'm working on a Mac (Un*x-based) system with as much GNU toolchain components as possible. Others may use GNU-based toolchains for ARM development, e.g., YAGARTO, but I choose the LLVM.org toolchain, explained [here](https://llvm.org/). On my Mac I install it using HomeBrew:
```
brew install llvm
```
which installs at this location <code>/usr/local/opt/llvm/bin</code>

In this step, we create an initial, reusable [Makefile](./Makefile)

We will build the code to run on a virtual rPi using <code>qemu-system-aarch64</code>. See QEMU's site for [AARCH64 documentation for the ARM platform](https://wiki.qemu.org/Documentation/Platforms/ARM).

Next to succesfully link the compiled object code to the (virual) hardware, you will need to use the [link.ld](./link.ld) file.

Next, [Step_02](./Step_02/README.md)