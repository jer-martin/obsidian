## To-Do List for System Call Project

### Testing Harness

- [x]  Implement `#define PROC_LOG_CALL <number>` in header.
- [x]  Implement `int* retrieve_set_level_params(int new_level)`.
- [x]  Implement `int* retrieve_get_level_params()`.
- [x]  Implement `int interpret_set_level_result(int ret_value)`.
- [x]  Implement `int interpret_get_level_result(int ret_value)`.
- [x]  Implement `int interpret_log_message_result(int ret_value)`.

### Report (p1.txt)

- [ ]  Explain kernel-level changes for the new system call.
- [ ]  Describe the testing procedure.
- [ ]  List any known bugs.
- [ ]  Format the report in man page format and limit it to 500 words.

### Screencast

- [ ]  Record a screencast demonstrating changes and how they work.
- [ ]  Ensure the screencast is no longer than 5 minutes.
- [ ]  Make sure audio speed-up is prohibited, and video is unlisted.

### Kernel Patch File (p1.diff)

- [ ]  Generate a patch file including all changes to all relevant files.

### Compressed Archive (process_log.tar.gz)

- [ ]  Ensure the compressed tar archive contains the following:
    - [ ]  `process_log.h`
    - [ ]  `Makefile`
    - [ ]  Any other source files needed to compile the library.

### Build and Test

- [ ]  Test applying the patch, building, and installing the kernel.
- [ ]  Test building and linking the user-level library.