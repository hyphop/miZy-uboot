# spiread 

read data by bytes from sunxi spi-flash to ram

## USAGE

spiread HEX_DST DEC_OFFSET DEC_BYTES

* HEX_DST - mem addr always used as hex!
* OFFSET  - offset in bytes from begin of flash
* BYTES   - how many bytes read from flash to mem by addr HEX_DST

## EXTENSIONS

* spiread.h  - hex_dst hex_offset hex_bytes
* spiread.d  - hex_dst dec_offset dec_bytes
* spiread.dh - hex_dst dec_offset hex_bytes
* spiread.hd - hex_dst hex_offset dec_bytes

## NOTE 


spiread.d work same as spiread - offset and bytes in dec

## EXAMPLES

read 1048576 bytes from begin spi-flash to 0x42000000 addr

    => spiread 0x42000000 0 1048576
    SPI readed 1048576 bytes from 0 offset, time 0.560
    
read 1048576 bytes from hex A0000 offset to 0x42000000 addr

    => spiread.hd 0x42000000 A0000 1048576
    SPI readed 1048576 bytes from 655360 offset, time 0.560

same but all in dec offset and bytes
    
    => spiread.d 0x42000000 655360 1048576
    SPI readed 1048576 bytes from 655360 offset, time 0.560
    
same but all in hex

    => spiread.h 0x42000000 A0000 FFFFF
    SPI readed 1048576 bytes from 655360 offset, time 0.560

read full 8M and 16M flash to 0x00000000 addr

    => spiread.h 0 0 800000
    SPI readed 8388608 bytes from 0 offset, time 5.363
    => spiread.h 0 0 1000000
    SPI readed 16777216 bytes from 0 offset, time 10.676

check readed 0x40 bytes uboot-header data from spi-flash

    => mw.b 0 FF 40
    => spiread.h 0 8000 40 
    SPI readed 64 bytes from 32768 offset, time 0.000
    => md.b 0 40
    00000000: 27 05 19 56 2d d0 13 d2 58 d5 22 de 00 06 92 2e    '..V-...X.".....
    00000010: 4a 00 00 00 00 00 00 00 96 ab 7d 10 11 02 05 00    J.........}.....
    00000020: 55 2d 42 6f 6f 74 20 32 30 31 37 2e 30 31 2d 68    U-Boot 2017.01-h
    00000030: 79 70 68 6f 70 20 6d 69 5a 79 20 66 6f 72 20 73    yphop miZy for s
    
## SPEED

    sunxi spi-flash reading speed is about 1.5 - 1.78 Mb/s

    1048576/0.560 = 1872457 b/s
    16777216/10.676 = 1571489 b/s
    1/0.560 = 1.78571428571429
    16/10.676 = 1.4986886474335

    spi bus work on fixed 24Mhz, maybe we can improve speed later
