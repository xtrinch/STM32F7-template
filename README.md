# STM32F7-template

Build template for the STM32F7 microprocessors, specifically the STM32F7 discovery boards. Developed for and tested with STM32F769I-Disco, easily adaptable for others. Uses linux kernel kbuild system for creating .config file used for dynamic inclusion of HAL libraries. Tested on Ubuntu 16.04.2 LTS and on Windows 10 with cygwin make & gcc, both with ARM GNU Toolchain.

## Prerequisites

### GNU Toolchain

https://developer.arm.com/open-source/gnu-toolchain/gnu-rm

GNU ARM Embedded Toolchain, pre-built for ARM Cortex-M and Cortex-R processors.

### Libraries

http://www.st.com/en/embedded-software/stm32cubef7.html

Inside the downloaded zip file, you can find STM32F7Cube embedded software stack composed of:

  - STM32F7xx HAL (Hardware abstraction layer?) and low-layer drivers
  - CMSIS (Cortex Microcontroller Software Interface Standard) drivers
  - BSP (Board Support Package) - middleware components (RTOS, USB, FatFs, graphics and TCP/IP).

## Usage

  - clone the template
  - amend the toolchain and libraries path in `Makefile.common`
  - run `make config` or `make menuconfig` or the like in `Demo/` directory, this will create `.config` file in same directory
  - run make in the `Demo/` directory
  
This way, you can have several project directories that use a common makefile, which you need only fix in one place: `Makefile.common`, a concept adapted from [STM32-Template github project](https://github.com/geoffreymbrown/STM32-Template).

The demo project basically just toggles some LED's on and off.

### Other STM32F7 boards

Should be pretty easy to adapt to use with other STM32F7 discovery boards, just go through `Makefile.common` and include appropriate `.c` files for your board (Look for those included that have more than STM32F7 defined in their filename)

## Programming & debugging the board

### Linux debugging
https://github.com/texane/stlink

Open source version of the STMicroelectronics Stlink Tools, made for Linux (in my case built from binaries for Ubuntu):

  - Start st-util in one window with `st-util -1`
  - Start GDB with `arm-none-eabi-gdb test.elf` or `make debug` in `Demo/` directory:
      - `(gdb) target extended-remote :4242`
      - `(gdb) load`
      - `(gdb) continue`
      
### Windows flashing
http://www.st.com/en/embedded-software/stsw-link004.html

  - Download ST-LINK Utility and add directory with st-link_cli executable to user/system PATH variable
  - Run `make flash-windows` in `Demo/` directory

## Acknowledgements

### kbuild-template

https://github.com/embedded-it/kbuild-template.git

Modified kbuild version taken from here.
