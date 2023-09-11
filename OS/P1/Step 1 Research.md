- [[#Process Logging|Process Logging]]
- [[#Kernel Data Structures|Kernel Data Structures]]
- [[#Kernel Log Levels and Process Log Levels|Kernel Log Levels and Process Log Levels]]



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
<th>Header 1</th>
<th>Header 2</th>
<th>Header 3</th>
<th>Header 4</th>
</tr>
</thead>
<tbody>
<tr>
<td>Row1Col1</td>
<td>Row1Col2</td>
<td>Row1Col3</td>
<td>Row1Col4</td>
</tr>
<tr>
<td>Row1Col1</td>
<td>Row1Col2</td>
<td>Row1Col3</td>
<td>Row1Col4</td>
</tr>
<tr>
<td>Row1Col1</td>
<td>Row1Col2</td>
<td>Row1Col3</td>
<td>Row1Col4</td>
</tr>
<tr>
<td>Row1Col1</td>
<td>Row1Col2</td>
<td>Row1Col3</td>
<td>Row1Col4</td>
</tr>
<tr>
<td>Row1Col1</td>
<td>Row1Col2</td>
<td>Row1Col3</td>
<td>Row1Col4</td>
</tr>
<tr>
<td>Row1Col1</td>
<td>Row1Col2</td>
<td>Row1Col3</td>
<td>Row1Col4</td>
</tr>
<tr>
<td>Row1Col1</td>
<td>Row1Col2</td>
<td>Row1Col3</td>
<td>Row1Col4</td>
</tr>
<tr>
<td>Row1Col1</td>
<td>Row1Col2</td>
<td>Row1Col3</td>
<td>Row1Col4</td>
</tr>
<!-- Add more rows as needed -->
</tbody>
</table>
</div>

