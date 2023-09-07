### The Boot Process 
- i386 boot process - **BIOS
	Binary Input and Output System (Legacy since 2017, replaced by UEFI)**
    1. Execute BIOS Init (drivers, etc)
    2. Run Power-On Self Test (POST)
    3. Get boot device via NVRAM (no standard)
    4. Load "boot sector" into volatile RAM
    5. Execute Boot Block program from the boot sector (one block)
    6. Bootstrap OS with bootloader routine (flexible)

- x64 boot process - **UEFI
    Unified Extensible Firmare Interface Standard (New hotness)**
    1. Execute architecture firmware
    2. Execute EFI Manager (init & drivers)
    3. Get boot device via NVRAM (standardized)
    4. On disks, get boot loader from EFI partition

- ARM (like many platforms) has no standardized boot process

# Operating Systems

### [Algorithm](ALGO%2008-24-23%20Lecture%201.md)
- A set of instructions with finite initial store and state, a starting point, and unimbiguous ordering until the endpoint
- Flow chart/pseudocode
### Program
- The sequence of instructions that embody an algorithm
- Source -> assembly -> machine code
### Process
- A program in execution
- Program + process state (current instruction, state of memory, resources)
### Job
- A task to be completed
- Often a program (or collection thereof) awaiting execution or a process during execution
    *The words "process" and "job" are used interchangeably, but they are technically different*

## Why do we need an OS?
- How to load a program on a computer?
    - Mini-toggle switch per bit in the data register
    - Mini-toggle switch per bit in the address register
    - Button to load data from register into memory
- How to access I/O devices?
    - Uniform interface
        - use the same read/write routines
    - Safety
        - restrict access to read/write routines
- What about running multiple programs?
    - Manage resources
    - Protect private info 
    - Facilitate interactions

## What's the OS's job?
- #### Process Manager
    - Next program to be executed
    - Time to be given to each program
- #### Memory Manager
    - Best use of memory to run as many programs as possible
- #### I/O Device Manager
    - Which program should use a particular I/O device?
- #### Extended Machine
    - Provides user programs with a better, simpler, cleaner, model of the computer

## What the OS is not
- User interface
- System tools
- Libraries

He Doesnt Appreciate The Wonder Of Nature (frog = ugly)

## Many different types of OS
- Mainframe
- Server
- Multiprocessor
- Embedded
- etc.

## OS Generations
1. Gen 1 - 1945-1955
2. Gen 2 - 1955-1965
3. Gen 3 - 1965-1980
4. Gen 4 - 1980 - Present
5. Gen 5 - 1990 - Present

- #### Generation 1
    - Vacuum Tubes and plugboards
    - No OS
    - Single program execution
    - Programmer = Operator
- #### Generation 2
    - Transistors and batch systems
    - Role of the "programmer" became well defined
        - Programmer $\ne$ Operator
    - Different types
        - Uniprogrammed
            - Large portions of idle time on I/O
        - Multiprogrammed
            - Keeps CPU busy at all times
            - No user interaction
- #### Generation 3
    - Ics and multiprogramming
        - Allowed for miniaturization
    - Software developed directly using terminals
        - Each user has a terminal
    - Computers become fast enough to perform multiple tasks per second

## Ontogeny Recapitulates Phylogeny
- Each new species of computer goes through same development as ancestors
- Consequence of impermanence

