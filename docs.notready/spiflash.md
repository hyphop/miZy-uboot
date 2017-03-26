==sunxi spi flash read via uboot cmd

466878/512 = 
912*512 = 466944
466944 / 512 = 912

=> md.b 0x42000000 30
42000000: 55 aa 55 aa ff ff ff ff ff ff ff ff ff ff ff ff    U.U.............
42000010: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff    ................
42000020: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff    ................

=> spiflash 0x42000000 300000 0
SPI readed 300000 bytes from 0 offset, time 0.485


#define SPI0_CLK_DIV_BY_4           0x1001

=> spiflash 0x42000000 1000000 0
SPI readed 1000000 bytes from 0 offset, time 1.615

#define SPI0_CLK_DIV_BY_2           0x1000

=> spiflash 0x42000000 1000000 0
SPI readed 1000000 bytes from 0 offset, time 0.897

#define SPI0_CLK_DIV_BY_1           0x0001

=> spiflash 0x42000000 1000000 0
SPI readed 1000000 bytes from 0 offset, time 0.535

=> md.b 0x42000000 30      
42000000: 0e 00 00 ea 65 47 4f 4e 2e 42 54 30 0e 16 ca 4f    ....eGON.BT0...O
42000010: 00 60 00 00 53 50 4c 01 00 00 00 00 00 00 ff ff    .`..SPL.........
42000020: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff    ................

