# STM32F7-template

Build template for the STM32F7 microprocessors, specifically the STM32F7 discovery boards. Developed for and tested with STM32F769I-Disco, easily adaptable for others.

## GNU Toolchain

https://developer.arm.com/open-source/gnu-toolchain/gnu-rm

GNU ARM Embedded Toolchain, pre-built for ARM Cortex-M and Cortex-R processors.

## Libraries

http://www.st.com/en/embedded-software/stm32cubef7.html

In the `Libraries/` folder, you can find STM32F7Cube embedded software stack composed of:

  - STM32F7xx HAL (Hardware abstraction layer?) drivers
  - low-layer CMSIS (Cortex Microcontroller Software Interface Standard) drivers
  - BSP (Board Support Package) - middleware components (RTOS, USB, FatFs, graphics and TCP/IP).

## Programming & debugging

https://github.com/texane/stlink

Open source version of the STMicroelectronics Stlink Tools, made for Linux (in my case built from binaries for Ubuntu)

## Usage

  - clone the template
  - run make in the `Demo/` directory
  
This way, you can have several project directories that use a common makefile, which you need only fix in one place: `Makefile.common`, a concept adapted from [STM32-Template github project](https://github.com/geoffreymbrown/STM32-Template).

The demo project basically just toggles some LED's on and off.

### Other STM32F7 boards

Should be pretty easy to adapt to use with other STM32F7 discovery boards, just go through `Makefile.common` and include appropriate `.c` files for your board (Look for those included that have more than STM32F7 defined in their filename)
