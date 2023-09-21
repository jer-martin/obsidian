## Completed:
process log level attribute
get and set system calls
system call for log message at defined log level
static library functions
## TODO:
harness functions???
check for superuser in set_level
manpage



## Where to create system call
	/usr/rep/src/reptilian-kernel/arch/x86/entry/syscalls 

	 nvim syscall_64.tbl

### System call prototype
	goto_kernel
	cd include/linux
	nvim syscalls.h

This goes on the next clean line:

	asmlinkage int sys_sample_syscall(int sample_param);

### System call definition
	goto_kernel
	cd kernel
	nvim sys.c

This goes on the next clean line (example text):

	SYSCALL_DEFINE1(sample_syscall, int, sample_param)
	{
	    return sample_param + 1; // Adds 1 to the parameter and returns it
	}

the 1 denotes that theres 1 parameter for the function (i.e. for set log msg you want there to be 2 - log level and message)
### Init system call
	sudo make -j8 && sudo make install && sudo make modules_install

restart reptilian, ssh back in, then system calls are installed

**MAKE SURE TO CHECK DMESG FOR PRINTK OUTPUTS**

# Library stuff
make a p1 folder in home if you havent already and unzip the tar given with the assignment

	mkdir process_log

write the library in process_log.c and the definitions in process_log.h. compile the library with these commands

	gcc -c process_log.c -o process_log.o
	ar rcs libprocess_log.a process_log.o
	
do *NOT* use coderunner's implementation of 'run code', as you need to follow this compilation

	gcc getlevel.c -L/home/reptilian/p1/process_log -lprocess_log -o getlevel

(this is an example for the getlevel test file)



