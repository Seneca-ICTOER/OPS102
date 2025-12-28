# What does an Operating System do? 

An operating system performs four main functions:

## 1. Management and Separation of Resources 

Think of the specifications that were advertised when you bought your
last computer (or smartphone):

- multiple CPU cores
- several gigabytes of RAM memory
- storage in the gigabytes to terabytes range
- a display with a particular resolution
- various peripherals, such as cameras, speakers, and so forth

All of these are system resources. The operating system manages these
resources to ensure that they are used effectively, and to ensure that
there are no conflicts over their use.

As requested by the user(s), or as triggered by other factors such as
the time of day or operational requirements, the OS will create
processes \-- running instances of computer programs. Each process is
allocated compute resources by being permitted to run on one or more
computer cores. To run a large number of processes, the OS will switch
between them, stopping one process and starting another as needed to
ensure that all of the processes get a fair share of system resources
(which may not always be an equal share).

The operating system will allocate the available memory to processes and
to the operating system\'s internal operations. The OS will program the
system hardware to ensure that no process can overwrite memory allocated
to another process.

The OS will also allocate storage space to various files as they are
created and extended, and deallocate space when those files are
truncated (shortened) or deleted. The space allocated to one file will
be protected from use in other files.

Display space is similarly shared; the operating system will ensure that
multiple programs can each display in their own windows, but prevent
them from destroying graphics being displayed by other windows.

Peripheral devices are managed in different ways according to the
characteristics of the device. For example, sound output from multiple
processes will be combined for simultaneous output to the speakers (or
other output devices). However, when a process accesses a printer,
output from that processes is collected into a document, and the
documents are queued for sequential printing, because simultaneous
access would result in garbled output.

## 2. Security Enforcement 

It's important to keep information private in some contexts, and to
share information in other contexts. The operating system is responsible
for enforcing security rules. For example, on a smartphone, a social
media app shouldn't be able to access data from a banking app, and on a
cloud server, one customer shouldn't be able to access another
customer's data. However, multiple smartphone apps might be permitted to
access a photo album, and a company employee might need to view a report
generated on a server from multiple customers' data.

The operating system is responsible for enforcing the security rules but
not for creating them \-- the system administrators and/or users are
responsible for creating and maintaining the security settings and
policies which the operating system enforces.

## 3. Hardware Abstraction 

There are many different types of devices that perform similar
functions, and multiple ways that these devices can be connected. For
example:

- A keyboard may be connected via a USB connection or a wireless Bluetooth  connection, or may be created as a virtual keyboard on a touchscreen.
- A mouse may be connected via a wired USB, wireless USB dongle, or  wireless Bluetooth connection. But there are also other types of devices  which can provide the same capability of allowing the user to interact  with the display, including trackpads, trackballs, and touchscreens.  
- Sound may be played over built-in speakers, an external analog speaker,  an analog headset, a digital speaker or headset with a USB connection,  a Bluetooth speaker, earbuds, or headset, or played through a television connected via HDMI.

The operating system abstracts away these hardware details. This means
that programs can access devices in a general way without having to be
programmed to individually deal with each type of device that may be
used. This enables a program to request keyboard input or play sounds
without regard to the details of the specific hardware available.

## 4. Maintaining the Programming Model 

The operating system, computer hardware, and development tools
(compiler, linker, and so forth) work together to present the
"programming model" -- a conceptual framework which software developers
use when creating software.

As a simple example, several different application programs may be
designed to occupy the same area of memory; obviously, this presents a
conflict when these applications are used at the same time, so the
operating system works with the computer's hardware to load the
applications into different areas of physical memory, and then use the
computer's virtual memory capabilities to make each program appear to be
loaded into the region of memory for which it was written.
