# miZy-uboot

Advanced u-boot (for sunxi Orange Pi Zero, another sunxi boards maybe work too ), ready for full load linux from spi-flash, i2c display, FEL mode, and many other improvement 

Its just a part of miZy project, and same as other our parts can standalone used

## Features

* spi flash boot + ready for full load linux from spi-flash
* ready for fast full linux load, with boot-time about 4-8 sec (MMC-SPI), from power-on time
* 4x increase SPI-flash reading speed in SPL-loader and UBOOT ( spi work on 24Mhz freq now )
* i2c available on TWI0 (PA11 PA12)
* splash screen on ssd1306 i2c OLED 128x64 display TWI0 connected
* ready for uboot splash screen customization
* FEL mode - set or disable fel or restore normal spl boot, direct from uboot shell
* support any LZMA LZO GZIP uboot packed images, and direct as uboot shell cmd
* accept uboot images with bad crc 
* fast advanced configuration for build-in uboot environment, without recompilation
* ready for next USB loading from any 3 usb ports
* new improved building system full automated, speed + size optimized 
* easy write new patches with find_changes script
* led indication and splash for boot process
* many other small fix & adds

## SPI NOTE

by default device can not have SPI flash or have only 2M bytes (mx25l1606e its enough for uboot only),
needed re/install SPI flash to 4M or 8M or 16M bytes if u need  full load linux from spi-flash. For example 
we have tested on W25q128 spi flash, and this worked well!

## Get Source, Prepare & Build - need only 10-30 sec for build uboot

    cd /tmp
    mkdir zero_builder
    cd  zero_builder

    git clone https://github.com/hyphop/miZy-uboot
    cd miZy-uboot

    ./uboot_prepare
    ./uboot_build

## Output

u-boot-sunxi-with-spl0-i2c-mizy.bin -> ./uboot-mizy/u-boot-sunxi-with-spl.bin
    
## Deps and cross compilation

toolchain-arm_cortex-a9+neon_gcc-5.3.0_musl-1.1.15_eabi
...

## miZy 
 
![miZy](pics/miZy.logo.wb128x64x2.png)
miZy - open source minimalistic tiny fast embedded Linux system, (for sunxi Orange Pi Zero, another sunxi boards maybe work too )

## NOTES

some added source code part low quality ( sorry but I'm new to uboot ), some parts not annotated not documenated, we stay in active develop now!
wellcome to join and improve & tidy this code.

## LINKS

- [https://github.com/hyphop/miZy-uboot](https://github.com/hyphop/miZy-uboot)
- [https://hyphop.github.io/mizy/](https://hyphop.github.io/mizy/)
