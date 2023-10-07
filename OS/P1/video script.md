Good morning! Today I will be going over the changes made to the reptilian kernel for P1.
Let's start with definitions. I made structures for the syscalls in syscalls.h and syscall_64.tbl. These are just simple definitions so that the kernel recognizes the calls, so let's move on. 
I implemented the calls in sys.c. Let's look at those now.
Here you can see the implementations of set_log_level, get_log_level, and set_log_message.
Set log level is simple, it runs two validity checks and then sets and returns the new level.
Get log level is also simple, as it just returns the current log level, no matter what it is.
Setting the log message is where the fun begins. First, I made an array that maps log levels to their corresponding error code. I then made a switch statement to be sure that every log message level matches the intended level.
After the switch statement, we can see the implementation for the message set. Similarly to the level set, it runs validity checks and then retrieves the process ID and name and logs the message.

Lets see these calls in action. 
First, I will run setlevel and getlevel to make sure they work.
sudo ./setlevel 4
sudo ./getlevel

Here is the library and harness implementations,
the functions that actually perform the syscalls are obviously simple, and then we have the retrieve parameters functions which just take in the parameters passed in to be used by the harness. I also have interpret functions, which simply return the return value, as the value was already interpreted in sys.c.

Next, I am going to run the harness_test testing suite provided by Professor Gomes.

Finally, we will run the library test.

As you can see, all the tests pass and the log level in the message matches the intended logging level.

I believe that is all the changes I made. Thanks for watching!