# Lab 3: Adding Reptilian System Calls
Andres Canas

## Description
The purpose of this project is to add system calls to the linux kernel. By adding a system call we are making our own
modifications/improvements to the operating system. The purpose of the system calls in this project is to allow for Process Log Level Messages (similar to KERNEL Log Levels).
Processes will able to get or set the kernel-wide process log level according to its credentials. Each process will also be able to send log messages to the kernel if
their level permits. The latter part of the project is to create library functions to test the system calls. This involves compiling c files to create a library '.a' through a Makefile.

## Design
There are a number of steps needed to add a system call to the reptilian kernel. The basic steps can be found here:
https://williamthegrey.wordpress.com/2014/05/18/add-your-own-system-calls-to-the-linux-kernel  
I added the system call by modifying the following files:  
1.) Adding the syscall definition and ID to the syscall table in /linux/syscalls_64.tbl  
2.) Declaring the system call function protoype in the syscalls.h header file.  
3.) Implementing the syscall definitions and global process_log_level variable in kernel/sys.c  

There were certain measures taken to ensure the security rules in the project description when implementing the system calls. For example, only superusers
are able set the kernel-wide process log level. To achieve this security the set function in sys.c uses current_cred()->cred.val, available in cred.h in the include files, 
to obtain the user's credential level.

The latter part of the project involved creating the static library. The steps were as follows:  
4.) creating process_log directory  
5.) creating a header file, process_log.h, with the function declarations given in the project description  
6.) creating a c file to implement the functions, process_log.c  
7.) creating a Makefile to compile the source files and create a static library, libprocess_log.a  
8.) Tar the source, header, and makefile into a compressed folder  


## Verification
Once these steps are completed, you must remake and reboot reptilian to test the system calls.
To test this on another system you must first create a patch file using the steps from the project description.
The user on the new system must apply the patch file on a clean kernel source directory using:  
$ git apply patch_file.diff  
$ make && sudo make install && sudo make modules_install  
The system calls can then be tested through the compressed folder made in step 8 from Design:  
1.) Uncompress the folder using tar  
2.) Navigate into the folder and build the library using make  
3.) Link against the library to test the library and harness functions with your own test files.  

##Contact
Thank you, for any questions please email andrescanas001@ufl.edu
