[P1 Research](P1%20Research.md)
### Broken Down Into Smaller Steps:
### 1) Create a kernel-wide process log level attribute

1.1) Research where in the kernel structure a global attribute would best fit.

1.2) Define possible values for the log level (e.g., INFO, DEBUG, ERROR, WARN).

1.3) Implement the kernel-wide attribute to store the log level.

1.4) Implement initialization of this attribute during kernel startup.

1.5) Test the attribute's functionality and ensure it's set and retrieved properly.

### 2) Create system calls that allow a process to get or set the process log level of the system

2.1) Familiarize yourself with how system calls are added in the Linux/Reptilian kernel.

2.2) Design the system call interface (function signatures) for getting and setting the log level.

2.3) Implement the system call to retrieve the kernel-wide log level.

2.4) Implement the system call to set the kernel-wide log level.

2.5) Add the new system calls to the kernel's system call table.

2.6) Test the system calls from user-space to ensure they work as expected.

### 3) Create system call that allows a process to add a process log message at a defined log level

3.1) Design the system call interface for adding a log message with a specified log level.

3.2) Implement the system call, checking the log level against the kernel-wide attribute.

3.3) If the message log level is appropriate (e.g., greater than or equal to the kernel-wide log level), log the message.

3.4) Add this system call to the kernel's system call table.

3.5) Test the new system call from user-space to ensure log messages are handled correctly.

### 4) Create static library functions that allow the system calls to be invoked via a C API

4.1) Setup a development environment for creating a static library in C.

4.2) Design the C API's function signatures for the operations (get log level, set log level, add log message).

4.3) Implement each function in the C API to invoke the respective system call.

4.4) Compile and package these functions into a static library.

4.5) Provide a sample program or test suite to demonstrate how to link with this library and use the API.

4.6) Test the static library with multiple scenarios to ensure the C API behaves as expected.