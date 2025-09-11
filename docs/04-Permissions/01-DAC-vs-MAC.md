# Discretionary versus Mandatory Access Controls 

In multi-user operating systems it is important to be able to control
access to information. This is usually done at the file and directory
levels.

There are two broad categories of access controls applied to files and
directories:

1. Discretionary Access Controls (DACs) - these are access controls that 
can be set to any value at the discretion of the users or administrators 
of the computer system.

2.  Mandatory Access Controls (MACs) - these are access controls that 
are applied across the entire system in a uniform way, and cannot be 
individually overridden by the users or administrators. An example of 
a Mandatory Access Control system is SELinux (security-enhanced Linux), 
a system originally developed by the National Security Agency of the 
US Federal Government and now part of the Linux Kernel 
(via KSM - Kernel Security Modules). SELinux uses *type enforcement* 
and *labelling* of both resources (such as files and network connections) 
and processes (running programs) to determine whether a specific process 
should have access to a specific resource, and to deny access when it does not.
SELinux is used in several operating systems, including Android, Fedora, 
CentOS, and Red Hat Enterprise Linux.

In this OPS102 course, we will be looking only at DACs.
