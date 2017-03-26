==uboot spi flash

32768 / 512 = 64
32768 / 4096 = 8
32768 / 8192 = 4

hex 8000 = 32768

=> spiflash 0x42000000 466878 0
SPI readed 466878 bytes from 0 offset, time 0.754

=> md.b 0x42000000 40
42000000: 0e 00 00 ea 65 47 4f 4e 2e 42 54 30 0e 16 ca 4f    ....eGON.BT0...O
42000010: 00 60 00 00 53 50 4c 01 00 00 00 00 00 00 00 00    .`..SPL.........
42000020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
42000030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................

=> md.b 0x42008000 40
42008000: 27 05 19 56 06 ed eb 1f 58 c6 18 18 00 06 9e e6    '..V....X.......
42008010: 4a 00 00 00 00 00 00 00 37 65 3a 1e 11 02 05 00    J.......7e:.....
42008020: 55 2d 42 6f 6f 74 20 32 30 31 37 2e 30 31 2d 68    U-Boot 2017.01-h
42008030: 79 70 68 6f 70 20 6d 69 5a 79 20 66 6f 72 20 73    yphop miZy for s

> 

== spl image header 

	> file u-boot-dtb.img 
	u-boot-dtb.img: u-boot legacy uImage, U-Boot 2017.01-hyphop miZy for s\276, Firmware/ARM, Firmware Image (Not compressed), 434150 bytes, Mon Mar 13 21:29:36 2017, Load Address: 0x4A000000, Entry Point: 0x00000000, Header CRC: 0x0E96408B, Data CRC: 0xE9871486

	-rw-r--r-- 1 root root 434214 Mar 13 21:29 u-boot-dtb.img

	static int spl_spi_load_image(struct spl_image_info *spl_image,
			      struct spl_boot_device *bootdev)
	
	struct image_header *header;
	header = (struct image_header *)(CONFIG_SYS_TEXT_BASE);
	
	spi0_read_data((void *)header, CONFIG_SYS_SPI_U_BOOT_OFFS, 0x40);
	err = spl_parse_image_header(spl_image, header);
	

	typedef struct image_header {
	__be32		ih_magic;	/* Image Header Magic Number	*/
	__be32		ih_hcrc;	/* Image Header CRC Checksum	*/
	__be32		ih_time;	/* Image Creation Timestamp	*/
	__be32		ih_size;	/* Image Data Size		*/
	__be32		ih_load;	/* Data	 Load  Address		*/
	__be32		ih_ep;		/* Entry Point Address		*/
	__be32		ih_dcrc;	/* Image Data CRC Checksum	*/
	uint8_t		ih_os;		/* Operating System		*/
	uint8_t		ih_arch;	/* CPU architecture		*/
	uint8_t		ih_type;	/* Image Type			*/
	uint8_t		ih_comp;	/* Compression Type		*/
	uint8_t		ih_name[IH_NMLEN];	/* Image Name		*/
	} image_header_t;
	
	typedef struct image_info {
	ulong		start, end;		/* start/end of blob */
	ulong		image_start, image_len; /* start of image within blob, len of image */
	ulong		load;			/* load addr for the image */
	uint8_t		comp, type, os;		/* compression, type of image, os type */
	uint8_t		arch;			/* CPU architecture */
	} image_info_t;
	
	
	spi0_read_data((void *)spl_image->load_addr, CONFIG_SYS_SPI_U_BOOT_OFFS,
		       spl_image->size);
	
	