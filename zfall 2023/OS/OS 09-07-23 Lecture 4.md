### System Resources
- The OS is responsible for managing:
	- CPU Time
	- Working memory
	- Storage

### Key Concepts
- Files
	- Logically named persistent storage
	- A paradigm for I/O devices, communication
- Process
	- Program *in execution*
	- ***NOT THE SAME AS A PROGRAM***
- Procedural call
	- Procedures are named code with:
		- Local variables
		- Parameters, passed by:
			- value (5)
			- reference (mem address of 5)
			- name (var_5)
		- pointer to entry / return
- System call
	- A system call involves a *context switch* into *kernel mode* for execution
	- Usually, there is a *system library entry point* (fread, fwrite)

### File Storage
- Operating systems facilitate storage of data via ***file systems***
	- pattern to the arrangement of data on a disk
	- have a mounting scheme (C:\\. /mnt/disk, etc.)
	- other possible features:
		- redundancy

### Programs & Processes & Threads, Oh My!
- When we run a program, we create a ***process***
	- a running program (*in execution*)
	- has some address space
	- is associated with specific resources (container)
	- has one or more threads of execution

![](../zassets/Pasted%20image%2020230907161805.png)

