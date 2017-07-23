# STM32F7-template

Build template for the STM32F7 microprocessor, specifically the STM32F7 discovery boards.

## Toolchain

https://developer.arm.com/open-source/gnu-toolchain/gnu-rm

GNU ARM Embedded Toolchain, pre-built for ARM Cortex-M and Cortex-R processors.

## Libraries

http://www.st.com/en/embedded-software/stm32cubef7.html

STM32F7Cube embedded software stack composed of:

  - HAL drivers
  - low-layer CMSIS (Cortex Microcontroller Software Interface Standard) drivers
  - BSP (Board Support Package) - middleware components (RTOS, USB, FatFs, graphics and TCP/IP).


## Usage

  - clone the template
  - run make in the `Demo/` directory
  
This way, you can have several project directories that use a common makefile, which you need only fix in one place: `Makefile.common`, a concept adapted from [STM32-Template github project](https://github.com/geoffreymbrown/STM32-Template).

The demo project basically just toggles some LED's on and off.
