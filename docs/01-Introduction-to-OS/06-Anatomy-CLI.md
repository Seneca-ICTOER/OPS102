# Anatomy of a Command Line Interface (CLI) 

A CLI is provided by two programs:

1.  A terminal program, which is responsible for collecting user input 
and displaying the output from the shell and commands.

2.  A shell, which interprets the user's written commands.

These may be on the same machine, or they may be on different computers.
For example, it is common to access both Linux and Windows systems over
a remote connection, using a protocol such as SSH ("secure shell", which
protects the connection using encryption). In that case, the terminal
program runs on the computer in front of the user, and the shell runs on
the remote computer system.