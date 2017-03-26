=> spiflash ${kernel_addr_r} 3097200 655360
SPI readed 3097200 bytes from 655360 offset, time 1.655
=> im
  iminfo imxtract
=> iminfo 0x42000000

=> spiflash ${fdt_addr_r} 65536 524288   
SPI readed 65536 bytes from 524288 offset, time 0.035

=> spiflash ${ramdisk_addr_r} 2508708 5636096
SPI readed 65536 bytes from 524288 offset, time 0.035

setenv bootargs "mizy=there itype=openwrt root=/dev/ram0 rw console=tty1 console=ttyS0,115200 earlyprintk=ttyS0,115200 mtdparts=W25q128-flash.0:524288(uboot),65536(dtb),65536(script),4980736(kernel),6553600(initrd),-(user) panic=10 consoleblank=0 loglevel=3 sunxi_ve_mem_reserve=0 sunxi_g2d_mem_reserve=0 sunxi_fb_mem_reserve=16 bootfrom=fel"

bootm ${kernel_addr_r} ${ramdisk_addr_r}

