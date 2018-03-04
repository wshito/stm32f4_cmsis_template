# stm32f4_cmsis_template for Eclipse IDE

This is a CMSIS project template for STM32F4 microcontroller to develop on GNU ARM Eclipse.  The HAL dependency is removed.

## Usage

1. Download the ZIP archive and rename the directory to the new project name.
1. Import the project as existing Eclipse project.  The project name will be stm32f4_cmsis_template at this point.
2. Rename the project name using the refactoring menu.

The template contains the simple blinky example in `src/main.c` for STM32F4-Discovery board.  Building project will make both hex and elf files.

## Clock Settings

The board initialization is done in `src/_initialize_hardware.c`.  Here is the default settings.

- `HSE` Oscillator is enabled by compiler option, `HSE_VALUE`.
- `PLL` source is set to `HSE`.
- `VCO` in `PLL` is set 1MHz.
- `PLLN` is set 336. Thus `VCO x PLLN = 336 MHz`.
- `PLLP` is set 2.  Thus `PLLN / PLLP = 168 MHz`. --> **This is set for `SYSCLK`.**
- `PLLQ` is set 7.  Thus `PLLN / PLLQ = 48 MHz` for USB OTG FS, SDIO, and RNG.
- `SYSCLK` source is `PLLCLK` (168 MHz).
- `AHB` is equal to `SYSCLK`.  `AHB = 168 MHz`.
- Low speed bus `APB1 = AHB / 4 = 42 MHz`.
- High speed bus `APB2 = AHB / 2 = 84 MHz`.
