
- [[#Process Logging|Process Logging]]

### Process Logging
- Recording / monitoring activities associated with individual processes
- A few examples of these activities are:
	1. **Lifecycle Events**: 
		- This includes events like when a process is created (forked), when it exits, or when it's killed.
	2. **System Resource Usage**: 
		- Logging resource consumption of a process, such as CPU usage, memory allocation, and file descriptor utilization.
	3. **Inter-process Communication (IPC) Events**: 
		- Logging communications or signals between processes.
	4. **Errors and Exceptions**: 
		- Any error or unexpected behavior within the process can be logged for debugging or monitoring purposes.
	5. **System Calls**: 
		- Every interaction a process makes with the operating system via system calls (e.g., file operations, network activities) can be logged.

In the project spec, creating a kernel-wide process log level attribute suggests that processes will have a logging mechanism with varied verbosity levels. These levels may dictate what details about a process is logged. For example:
	A higher log level might record all system calls, IPC events, and more detailed info
	Whereas a lower log level might only record critical errors
The intended capability to "get and set" the log level indicates that we will create system calls to control the verbosity of this logging.
The system call that allows a process to "add a process log message at a defined log level" suggests processes will have the ability to log custom messages, which will be recorded if the current log level deems them relevant.

### Kernel Data Structures
- 'task_struct'
	- this is the data structure used by Linux to manage processes
	- each process has an associated task_struct