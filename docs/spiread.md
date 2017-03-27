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

## SPEED

    sunxi spi-flash reading speed is about 1.5 - 1.78 Mb/s

    1048576/0.560 = 1872457 b/s
    16777216/10.676 = 1571489 b/s
    1/0.560 = 1.78571428571429
    16/10.676 = 1.4986886474335

    spi bus work on fixed 24Mhz, maybe we can improve speed later
