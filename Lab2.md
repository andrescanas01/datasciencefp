# Lab 2: My First Kernel Mod
Andres Canas

## Description
The purpose of this project is to configure the log messages displayed to the screen upon booting Reptilian. 
By doing this the system can print out a personal message of the coder's choice, everytime the system is booted.
For this project the format of the message will be as follows: "#### Name (ID) Message ####"

## Design
The outcome of this project can be achieved by modifying the kernel source code. One of the important pieces of
information given in the project description is the need to add the boot message near the rcu_end_inkernel_boot() function.
The other important piece is that only the KERN_ERR log level ouptut will display to the screen in non-(verbose or debug) mode.
With this information we can perform the following steps:  
1.) connect and cd to kernel directory (cd usr/rep/src/reptilian-kernel)  
2.) use grep to find the source file that contains the rcu_end_inkernel_boot() function (grep -r "rcu_end_ink")  
3.) cd into the folder that contains the file which contains the function call (cd init)  
4.) open the file to make changes (nano main.c)  
5.) add print messages before the rcu_end_inkernel_boot() call (printk(KERN_ERR "#### Name (ID) Message ####")  
6.) Save the file and Make  

## Verification
Once these steps are completed, the reptilian kernel can be rebooted to check for the new message.
To test this on another system you must first create a patch file using the steps from the project description.
The user on the new system must apply the patch file in the kernel source directory using:  
$ git apply patch_file.diff  
$ make && sudo make install & sudo make modules_install  
