== => lzmadec                              
lzmadec - lzma uncompress a memory region

Usage:
lzmadec srcaddr dstaddr [dstsize]

==example

=> load mmc 0:1 42000000 splash.cmd.lzma
81 bytes read in 368 ms (0 Bytes/s)

=> lzmadec 42000000 41000000 
Uncompressed size: 192 = 0XC0
=> md.b 41000000 100

=> lzmadec 42000000 45000000 30
Uncompressed size: 59 = 0X3B

