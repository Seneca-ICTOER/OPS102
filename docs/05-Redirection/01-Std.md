# Standard File Descriptors/Handles

On Linux, other Unix-like systems, and on Windows, programs may open
*file descriptors* (Linux terminology) or *file handles*
(Windows terminology). Each file descriptor/handle is a numbered channel
connected to a file or device.

By default, three channels are opened automatically by the shell when a
process is started. These are:

```plain
0 - Standard Input (stdin) - this is the default input channel for 
    the program

1 - Standard Output (stdout) - this is the default output channel 
    for the program, used to output "normal" messages

2 - Standard Error (stderr) - this is the default error channel 
    for the program, used to output error messages
```

Without redirection, all three of these descriptors/handles are
connected to the terminal. Therefore, the command will get input from
the terminal, send output messages to the terminal, and send error
messages to the terminal.