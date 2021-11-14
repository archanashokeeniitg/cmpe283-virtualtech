# Introduction

I did the assignment myself.

## Question 
Your assignment is to create a Linux kernel module that will query various MSRs to determine 
virtualization features available in your CPU. This module will report (via the system message log) the 
features it discovers.
At a high level, you will need to perform the following:
•Configure a Linux machine, either VM based or on real hardware. You may use any Linux 
distribution you wish.
•Download and build the Linux kernel source code
•Create a new kernel module with the assignment functionality
•Load (insert) the new module
•Verify proper output in the system message log.


## steps for processing-


Install VMware Fusion(Mac OS) on my mac.

Download Ubuntu 20.04 desktop verison iso file.

Create a virtual machine with Fusion that will run Ubuntu usingthe iso.

Increase the size of hard disk in Fusion setting.

Select "enable hypervisor application in this virtual machine".

Start virtual machine.

Login to Canvas, download relevant files and cmpe283-1.c.

setup environment following https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel

