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

Download relevant files and cmpe283-1.c from canvas.

setup environment following https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel

```
[ 3514.291866] CMPE 283 Assignment 1 Module Start
[ 3514.291868] Pinbased Controls MSR: 0x7f00000016
[ 3514.291869]   External Interrupt Exiting: Can set=Yes, Can clear=Yes
[ 3514.291870]   NMI Exiting: Can set=Yes, Can clear=Yes
[ 3514.291871]   Virtual NMIs: Can set=Yes, Can clear=Yes
[ 3514.291872]   Activate VMX Preemption Timer: Can set=Yes, Can clear=Yes
[ 3514.291873]   Process Posted Interrupts: Can set=No, Can clear=Yes
[ 3514.291874] Exit Controls MSR: 0x7fffff00036dff
[ 3514.291875]   Save debug controls: Can set=Yes, Can clear=No
[ 3514.291876]   Host address-space size: Can set=Yes, Can clear=Yes
[ 3514.291877]   Load IA32_PERF_GLOBAL_CTRL: Can set=Yes, Can clear=Yes
[ 3514.291878]   Acknowledge interrupt on exit: Can set=Yes, Can clear=Yes
[ 3514.291879]   Save IA32_PAT: Can set=Yes, Can clear=Yes
[ 3514.291880]   Load IA32_PAT: Can set=Yes, Can clear=Yes
[ 3514.291880]   Save IA32_EFER: Can set=Yes, Can clear=Yes
[ 3514.291881]   Load IA32_EFER: Can set=Yes, Can clear=Yes
[ 3514.291882]   Save VMX-preemption timer value: Can set=Yes, Can clear=Yes
[ 3514.291883]   Clear IA32_BNDCFGS: Can set=No, Can clear=Yes
[ 3514.291884]   Conceal VMX from PT: Can set=No, Can clear=Yes
[ 3514.291885]   Clear IA32_RTIT_CTL: Can set=No, Can clear=Yes
[ 3514.291886]   Load CET state: Can set=No, Can clear=Yes
[ 3514.291887]   Load PKRS: Can set=No, Can clear=Yes
[ 3514.291887] Entry Controls MSR: 0xffff000011ff
[ 3514.291888]   Load debug controls: Can set=Yes, Can clear=No
[ 3514.291889]   IA-32e mode guest: Can set=Yes, Can clear=Yes
[ 3514.291890]   Entry to SMM: Can set=Yes, Can clear=Yes
[ 3514.291891]   Deactivate dual-monitor treatment: Can set=Yes, Can clear=Yes
[ 3514.291892]   load IA32_PERF_GLOBAL_CTRL: Can set=Yes, Can clear=Yes
[ 3514.291893]   Load IA32_PAT: Can set=Yes, Can clear=Yes
[ 3514.291894]   Load IA32_EFER: Can set=Yes, Can clear=Yes
[ 3514.291895]   Load IA32_BNDCFGS: Can set=No, Can clear=Yes
[ 3514.291896]   Conceal VMX from PT: Can set=No, Can clear=Yes
[ 3514.291896]   Load IA32_RTIT_CTL: Can set=No, Can clear=Yes
[ 3514.291897]   Load CET state: Can set=No, Can clear=Yes
[ 3514.291898]   Load PKRS: Can set=No, Can clear=Yes
[ 3514.291899]   Save debug controls: Can set=Yes, Can clear=No
[ 3514.291900]   Host address-space size: Can set=Yes, Can clear=Yes
[ 3514.291901] Procbased Controls MSR: 0xfff9fffe0401e172
[ 3514.291902]   Interrupt-window exiting: Can set=Yes, Can clear=Yes
[ 3514.291903]   Use TSC offsetting: Can set=Yes, Can clear=Yes
[ 3514.291904]   HLT exiting: Can set=Yes, Can clear=Yes
[ 3514.291905]   INVLPG exiting: Can set=Yes, Can clear=Yes
[ 3514.291905]   MWAIT exiting: Can set=Yes, Can clear=Yes
[ 3514.291906]   RDPMC exiting: Can set=Yes, Can clear=Yes
[ 3514.291907]   RDTSC exiting: Can set=Yes, Can clear=Yes
[ 3514.291908]   CR3-load exiting: Can set=Yes, Can clear=No
[ 3514.291909]   CR3-store exiting: Can set=Yes, Can clear=No
[ 3514.291910]   CR8-load exiting: Can set=Yes, Can clear=Yes
[ 3514.291911]   CR8-store exiting: Can set=Yes, Can clear=Yes
[ 3514.291912]   Use TPR shadow: Can set=Yes, Can clear=Yes
[ 3514.291913]   NMI-window exiting: Can set=Yes, Can clear=Yes
[ 3514.291913]   MOV-DR exiting: Can set=Yes, Can clear=Yes
[ 3514.291914]   Unconditional I/O exiting: Can set=Yes, Can clear=Yes
[ 3514.291915]   Use I/O bitmaps: Can set=Yes, Can clear=Yes
[ 3514.291916]   Monitor trap flag: Can set=Yes, Can clear=Yes
[ 3514.291917]   Use MSR bitmaps: Can set=Yes, Can clear=Yes
[ 3514.291918]   MONITOR exiting: Can set=Yes, Can clear=Yes
[ 3514.291919]   PAUSE exiting: Can set=Yes, Can clear=Yes
[ 3514.291920]   Activate secondary controls: Can set=Yes, Can clear=Yes
[ 3514.291921] Procbased Controls 2 MSR: 0x8ff00000000
[ 3514.291921]   Virtualize APIC accesses: Can set=Yes, Can clear=Yes
[ 3514.291922]   Enable EPT: Can set=Yes, Can clear=Yes
[ 3514.291923]   Descriptor-table exiting: Can set=Yes, Can clear=Yes
[ 3514.291924]   Enable RDTSCP: Can set=Yes, Can clear=Yes
[ 3514.291925]   Virtualize x2APIC mode: Can set=Yes, Can clear=Yes
[ 3514.291926]   Enable VPID: Can set=Yes, Can clear=Yes
[ 3514.291927]   WBINVD exiting: Can set=Yes, Can clear=Yes
[ 3514.291928]   Unrestricted guest: Can set=Yes, Can clear=Yes
[ 3514.291929]   APIC-register virtualization: Can set=No, Can clear=Yes
[ 3514.291930]   Virtual-interrupt delivery: Can set=No, Can clear=Yes
[ 3514.291930]   PAUSE-loop exiting: Can set=No, Can clear=Yes
[ 3514.291931]   RDRAND exiting: Can set=Yes, Can clear=Yes
[ 3514.291932]   Enable INVPCID: Can set=No, Can clear=Yes
[ 3514.291933]   Enable VM functions: Can set=No, Can clear=Yes
[ 3514.291934]   VMCS shadowing: Can set=No, Can clear=Yes
[ 3514.291935]   Enable ENCLS exiting: Can set=No, Can clear=Yes
[ 3514.291936]   RDSEED exiting: Can set=No, Can clear=Yes
[ 3514.291937]   Enable PML: Can set=No, Can clear=Yes
[ 3514.291937]   EPT-violation #VE: Can set=No, Can clear=Yes
[ 3514.291938]   Conceal VMC non-root operation from Intel PT: Can set=No, Can clear=Yes
[ 3514.291939]   Enable XSAVES/XRSTORS: Can set=No, Can clear=Yes
[ 3514.291940]   Mode-based execute control for EPT: Can set=No, Can clear=Yes
[ 3514.291941]   Use TSC scaling: Can set=No, Can clear=Yes

```

