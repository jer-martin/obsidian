### The Boot Process
- i386 boot process
	- **BIOS
		- Binary Input and Output System (Legacy since 2017, replaced by UEFI)
	1. Execute BIOS Init (drivers, etc)
	2. Run Power-On Self Test (POST)
	3. Get boot device via NVRAM (no standard)
	4. Load "boot sector" into volatile RAM
	5. Execute Boot Block program from the boot sector (one block)
	6. 


