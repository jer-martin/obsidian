- [[#Process Logging|Process Logging]]
- [[#Kernel Data Structures|Kernel Data Structures]]
- [[#Kernel Log Levels and Process Log Levels|Kernel Log Levels and Process Log Levels]]
- [[#System Call|System Call]]



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
	- *if we want to associate the log level with an individual process, this is the place*
		- however, this is not the place for a kernel-wide attribute
- Global Kernel Variable
	- if the log level is truly system-wide, we may want to simply declare it as a global variable within a relevant kernel source file
		- for example, a logging related file, or one of the main files of the kernel
- Kernel Configuration *(/proc or /sys filesystems)*
	- this is where we put it if we want the attribute to be *dynamic*
		-  dynamic in this context means 'settable at runtime without rebooting'
	- /sys is preferable, as it is designed to export kernel attributes to user-space

### Kernel Log Levels and Process Log Levels

<div style="overflow-x: auto;">
<table border="1" style="width: 100%; border-collapse: collapse;">
<thead>
<tr>
<th>Kernel Level Name</th>
<th>Description</th>
<th>#</th>
<th>Process Level Name</th>
</tr>
</thead>
<tbody>
<tr>
<td>KERN_EMERG</td>
<td>Emergency / Crash Imminent (no process logging)</td>
<td>0</td>
<td>PROC_OVERRIDE</td>
</tr>
<tr>
<td>KERN_ALERT</td>
<td>Immediate Action Required</td>
<td>1</td>
<td>PROC_ALERT</td>
</tr>
<tr>
<td>KERN_CRIT</td>
<td>Critical / Serious Failure Occurred</td>
<td>2</td>
<td>PROC_CRITICAL</td>
</tr>
<tr>
<td>KERN_ERR</td>
<td>Error Condition Occurred</td>
<td>3</td>
<td>PROC_ERROR</td>
</tr>
<tr>
<td>KERN_WARNING</td>
<td>Warning; recoverable, but may indicate problems</td>
<td>4</td>
<td>PROC_WARNING</td>
</tr>
<tr>
<td>KERN_NOTICE</td>
<td>Notable, but not serious (e.g. security events)</td>
<td>5</td>
<td>PROC_NOTICE</td>
</tr>
<tr>
<td>KERN_INFO</td>
<td>Informational (e.g. init / shutdown)</td>
<td>6</td>
<td>PROC_INFO</td>
</tr>
<tr>
<td>KERN_DEBUG</td>
<td>Debug messages</td>
<td>7</td>
<td>PROC_DEBUG</td>
</tr>
<!-- Add more rows as needed -->
</tbody>
</table>
</div>

While exact implementation may vary, the lib functions must match the signatures laid out in these notes, and the system calls must apply the security model properly. Logged messages have format

	$log_level_name [\$executable, $pid]: $message"

For example:

	PROC_ERR [bacon_pancakes, 21]: Life is scary & dark. That is why we must find the light.


### System Call

The system will have a single, kernel-wide process log level which should initialize on boot in the kernel and must be stored persistently (until shutdown / reboot). The rules for logging are as follows: 
1) Any process can read (get) the process log level. 
2) Any process may send a process log to the kernel. 
3) Only a process running as the superuser may write (set) the process log level. 
4) If a message’s log level is higher than the process log level, the message is ignored. 
5) If a message’s log level is lower than or equal to the process log level, the message will be logged. 
6) The system-wide a process log level should be initialized to zero (0) – i.e., override logging only. 
7) Log levels can have values between 0-7 (3-bit unsigned integer). Invalid level results in call failure. 
8) Any successfully logged message should be logged with the corresponding kernel log level. 
9) Messages will have a maximum length of 128 characters. 

 System calls are called via: 

	 syscall(call_num, param1, param2)

To log a message, the call should be:

	syscall(PROC_LOG_CALL, msg, level)

*Call parameters are limited to no more than two!*