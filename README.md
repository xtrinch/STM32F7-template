# STM32F7-template

Build template for the STM32F7 microprocessors, specifically the STM32F7 discovery & eval boards. Uses linux kernel kbuild system for creating .config file used for dynamic inclusion of HAL libraries and board/processor specific files. 

Tested on Ubuntu 16.04.2 LTS and on Windows 10 with cygwin binutils, both with ARM GNU Toolchain, and board STM32F76I-Discovery.

## Prerequisites

### GNU Toolchain

https://developer.arm.com/open-source/gnu-toolchain/gnu-rm

GNU ARM Embedded Toolchain, pre-built for ARM Cortex-M and Cortex-R processors.

### Libraries

http://www.st.com/en/embedded-software/stm32cubef7.html

Inside the downloaded zip file, you can find STM32F7Cube embedded software stack composed of:

  - STM32F7xx HAL (Hardware abstraction layer) and LL (low-layer) drivers
  - CMSIS (Cortex Microcontroller Software Interface Standard) drivers
  - BSP (Board Support Package) - middleware components (RTOS, USB, FatFs, graphics and TCP/IP).

With this template, you can have several project directories that use a common makefile, `Makefile.common`, which you manipulate via `.config` file.

## Demo project usage

The demo project basically just toggles some LED's on and off.

  - clone the template
  - run `make (menuconfig|config|xconfig|gconfig)` in `Demo/` directory, this will create `.config` file in same directory
  - run make in the `Demo/` directory

## Usage on new project

  - copy makefile from Demo project, point it to the directory where you cloned this template
  - run `make (menuconfig|config|xconfig|gconfig)` to create `.config` file
  - run `make init`, which will copy all appropriate template user-application files for your board from the stm32f7cube framework into current directory (you configure which board it is in `.config` file)
  - run `make` to compile
  - voila

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

### Concept

Concept adapted from [STM32-Template github project](https://github.com/geoffreymbrown/STM32-Template).

### kbuild-template

Adapted kbuild version for building embedded projects taken from [kbuild-template github project](https://github.com/embedded-it/kbuild-template.git
).
