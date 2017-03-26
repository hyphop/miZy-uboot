== => lzodec 
lzodec - lzop uncompress a memory region

Usage:
lzodec srcaddr dstaddr dstsize|srcsize

==example

=> load mmc 0:1 42000000 splash.cmd.lzo
143 bytes read in 384 ms (0 Bytes/s)

=> lzodec 42000000 43000000 && echo ok
Uncompressed size: -1 = 0XFFFFFFFF, ret: -4

=> lzodec 42000000 43000000 200 && echo ok
Uncompressed size: 192 = 0XC0, ret: 0
ok
