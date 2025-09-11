# Computer Resources 

Every digital computer system has finite resources, managed by the
operating system.

One or more of these three broad categories of resources constrain
(limit) the system\'s ability to execute each running program:

- **Memory** - The availability of adequate memory, and the 
performance of that memory.

- **CPU** - The ability of the CPU to execute the instructions 
contained in the program at a particular speed.

- **Input/Output** (I/O) - This is a very broad category that 
includes storage, networking, printers, keyboard and mouse, and so forth.

## Processes

On a multitasking computer system, a *process* is a single instance of
an executing computer program. For example, *ssh* is one program. If
there are no running instances of ssh on a computer system, then there
are no ssh processes. If one user starts one ssh session, then one there
is one ssh process. If five users start a combined total of twelve ssh
sessions, then there are twelve ssh processes.

Each process is assigned a Process ID (PID) and is allocated its own
resources, such as memory. Processes are scheduled to run (execute) on a
CPU core for a fraction of a second, and then the operating system may
intervene and switch the CPU core to run another processes. However, if
a process is waiting for an I/O resources, such as data from a storage
device, a packet of data from the network, or a keystroke from the user,
it may inform the operating system that it does not need to be executed
until that resource is available. A process which is ineligible for
execution because it is waiting for a resources is called a *sleeping*
process.

## Resource Conflicts 

When the resource requirements of running computer programs
significantly exceed available resources, system performance will become
unsatisfactory.

It is important to be able to identify the resource consumption of each
process, and each operating system provides multiple tools to do this.
They also provide tools to terminate processes if they are unstable or
consuming excessive resources.

## Challenges with Monitoring Resource Usage 

It is difficult to accurately monitor a process\' resource utilization
because it will change from microsecond to microsecond. In addition,
some resources are very difficult to accurately measure:

### Memory

On contemporary computer systems, memory is very actively and
dynamically managed by the Operating System using the hardware\'s
virtual memory features. This enables many useful techniques, including:

- Demand Loading - Only the portion of programs which are used are loaded. 
Code for features that are not used is not loaded into memory. For example,
in a word processor (such as LibreOffice/OpenOffice or Word), features such 
as table of content generation, endnotes, and watermarks are not used in 
many documents, and the code for those features will not be loaded in many 
cases.
- Sharing of Memory - Shared libraries (also called Dynamically Linked 
Libraries) may be used by many different processes. These libraries are 
loaded into memory only once, using demand loading, regardless of the 
number of processes using each library. Similarly, a program which is 
running in two or more processes will be loaded into memory only once, 
and shared between the processes. This significantly reduces memory 
requirements.
- Swap - When system memory (RAM) is approaching full utilization, 
the operating system may take some of the least-recently-used areas of 
memory and place them in storage (hard disk or solid state disk) or compress 
them in order to avoid running out of free memory. Areas of memory swapped 
out may be swapped back in if they are later required.

Due to the utilization of these techniques and others, the memory
consumption of a program can be calculated in many different ways. For
example:

- You could add up the full size of the program, all of the shared libraries, and the data used by a process, but that would yield a large number (a pessimistic view of memory consumption). The process is likely not occupying that much memory, and terminating the process will typically release only a fraction of that memory because most of the shared libraries will still be loaded into memory and in use by other programs.
- You could add up just the portion of the program in memory plus the data area in memory used by a process, but this would understate the full memory utilization because it does not include the shared libraries nor the portion of the program or data which has been swapped out or which has not (yet) been demand-loaded.

Therefore resource monitoring tools may present several different
statistics about memory usage for each process, or may try to present a
rough approximation of the amount of total system memory which can be
reasonably attributed to a process.

### CPU

Each CPU core is independently capable of executing programs. Most
modern CPUs have multiple cores (Symmetric Multi Processing, SMP),
enabling multiple programs to be executed simultaneously. Many modern
CPUs can execute more than one *thread* on a core (Symmetric Multi
Threading, SMT), meaning that they have hardware support for rapid
switching between two or more processes (or, in some cases,
sub-processes called *threads*) on one core \-- so a 4-core CPU
may be marketed as capable of running up to 8 tasks. However, this does
not mean that 8 programs can be fully executed at once!

To use an analogy, a SMP processor is a bit like an apartment building,
where each core is like an apartment and can fully accommodate a family
(whether a single, couple, roommates, or parents and children), or, in
the case of the CPU, fully execute a process. SMT capability is a bit
like Airbnb rentals, which enable those units to be shared out quickly
when they\'re not in use by the main occupants, or in the case of the
CPU, quickly run other threads when the core (or part of the core) is
not in use.

Further complicating the issue is the fact that CPUs may have multiple
cores of different specifications \-- some fast, power-hungry cores used
for heavy tasks, and other slower, energy-efficient cores for lighter
tasks. Cores may be shut down and started up by the OS as needed. For
example, some Seneca lab computers have an Intel CPU with 12 cores
consisting of 10 performance cores (capable of running 2 threads) and 2
efficiency cores (capable of running 1 thread). In a similar way, a
Google Pixel 8 phone has 4 energy-efficient/low-performance Arm
Cortex-A510 cores, 4 mid-range Cortex-A715 cores, and one
high-energy-usage/very high-performance Cortex-X3 core.

In addition, current CPUs can operate at a range of speeds, and the OS
and hardware work together to dynamically tune the speed to balance
temperature, energy usage, and performance.

Therefore, statistics reporting the percentage of CPU capability in use
by a process may report the percentage of a core\'s capability in use,
either with or without considering SMT capabilities, or they may report
the percentage of the full CPU\'s capability (including all cores). When
cores of different specifications are part of a single CPU, it may be
difficult to determine the relative ratio of performance between the
different types of cores, especially as the speed of those cores is
being adjusted \-- and therefore utilization percentages are almost
always a rough approximation.
