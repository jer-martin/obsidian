## Completed:
process log level attribute

get and set system calls

## TODO:
system call for log message at defined log level

static library functions



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

### Init system call
	sudo make -j8 && sudo make install && sudo make modules_install

restart reptilian, ssh back in, then system calls are installed

**MAKE SURE TO CHECK DMESG FOR PRINTK OUTPUTS**

# Library stuff
seems to me like you can make your library anywhere, so i made a p1 folder in /home and began writing the lib in source.c

you also need to make a header file with function defintions, i did this under source.h in the same folder

