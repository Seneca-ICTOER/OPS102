# Monitoring and Terminating Processes 

## Monitoring and Terminating Processes on Windows 

### Graphical User Interface 

To manage processes graphically on Windows, use the *Task Manager*
tool. You can access this from the Start menu, or by pressing
Ctrl-Alt-Delete and selecting Task Manager from the menu that appears.

The Task Manager display shows processes grouped by executable name,
along with approximate resource usage.

To terminate a process, select it using the mouse, and then click on the
End Task button in the lower-right corner of the display.

### Command Line Interface using the CMD Shell 

To manage processes using the CMD shell (the default shell on Windows),
use these commands:

1\. \*\*tasklist\*\* - displays a list of tasks (processes) active on
the system. You can use options to select which processes are displayed,
as well as the output format (table, list, or comma-separated values).

2\. \*\*taskkill\*\* - terminates a process. By default, this command
attempts to get tasks to terminate in a safe manner (for example, if the
program is saving a file, that operation will be completed before the
program terminates). If a program does not respond to request, you can
specify the */f* option, which forcibly terminates the program.

You can specify the process to be terminated in one of two ways:

*  By process ID, using the `*`/PID *nnn*`*` option, which will terminate the process with the specified process ID.
*  By image (program or library) name, using the `*`/IM *name*`*` option, which terminates processes with the given image name. Asterisk wildcard characters may be specified as part of the name. Names must include the extension (for example, use `*`taskkill /im firefox.exe`*` or `*`taskkill /im firefox*`*` instead of `*`taskkill /im firefox`*`). 

The tasklist and taskkill commands also provide a mechanism for
filtering the process selection; see the online documentation for
details (*help tasklist* or *help taskkill*).

### Command Line Interface using Powershell 

Powershell is an alternate Windows shell. You can use these commands to
view and terminate processes using Powershell:

1\. \*\*get-process\*\* - Displays a list of current processes with
basic information about each. You can specify a program name as a
positional argument (without the filename extension); see the online
documentation for other available options.

2\. \*\*stop-process\*\* - Terminates a process. You may specify a PID
using the -ID option (*stop-process -id *pid**) or a program name
(without the filename extension) using the -NAME option (*stop-process
-name *name**).

-   -   Tip - Short Names:\*\* Many Powershell commandlets (built-in
        commands) have short names. The short name for the *get-process*
        command is *ps* and the short name for the *stop-process*
        command is *kill*, which conveniently match the names of similar
        commands on Linux!

## Monitoring and Terminating Processes on Linux 

### Command Line Interface 

From the bash (default shell) command line on Linux, you can view the
current process table using the process status command *ps*. By default,
it will show only processes associated with the current shell, and will
show only the process ID (PID), terminal, total execution time, and
command name:

```plain

$ ps
   PID TTY          TIME CMD
303632 pts/4    00:00:00 bash
303771 pts/4    00:00:00 ps
```

There are many ps options available to control which processes are
displayed and what information is displayed about each process. These
are the more commonly-used:

```plain

-u user   - Displays all processes owned by user
-e   - Shows every process
-l   - Shows long output, including process status (S), process ID (PID), parent process ID (PPID), approximate memory size (SZ), total execution time (TIME), and program name (CMD)
-f   - Shows full output, including process ID (PID), parent process ID (PPID), process start time (STIME), total execution time (TIME), and program name (CMD)
```

To terminate a process on Linux, send it a signal using the *kill*
command. Processes are specified by ID:

```plain

kill PID
```

By default, processes are send the terminate signal (signal 15,
SIGTERM). This requests that the process terminate gracefully (for
example, by completing pending operations before stopping). If a program
does not respond to this signal, the kill signal (signal 9, SIGKILL) may
be specified; this signal tells the operating system to abruptly and
forcefully terminate the process. Either of these forms is accepted:

```plain

kill -9 PID
kill -KILL PID
```

There are many other signals that may be sent to processes; to see a
list of all available signals, run the command *kill -l* or see the
online documentation for signal(7) (by running the command: *man 7
signal*).

To find all processes associated with a given program, use the pgrep
command: *pgrep *name**

To terminate processes by program name, use the killall command:
*killall *name**

## Text User Interface 

In addition to the command-line interface (CLI) tools mentioned above,
there are several text user interface (TUI) tools available which
display a full-screen view of the current process status which is
updated periodically.

The most common TUI process monitoring tool is *top*, which displays
output like this:

```plain

top - 11:51:05 up 1 day, 22:23,  2 users,  load average: 0.63, 0.62, 0.66
Tasks: 530 total,   1 running, 529 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.2 us,  1.4 sy,  0.0 ni, 97.1 id,  0.0 wa,  0.2 hi,  0.1 si,  0.0 st
MiB Mem :  28797.0 total,    730.7 free,  17121.8 used,  10944.4 buff/cache
MiB Swap:   8192.0 total,   8188.0 free,      4.0 used.  10960.2 avail Mem 
   PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
299042 qemu      20   0   11.4g   8.2g  30336 S  18.5  29.2  23:06.23 qemu-system-x86                     
  2382 chris     20   0 1313576 201884  78048 S   2.6   0.7  11:56.51 Xorg                                
  7037 chris     20   0   33.0g 562524 275008 S   2.6   1.9  24:20.54 chrome                              
  2654 chris     20   0 6512860 298252 136624 S   2.3   1.0  16:25.62 gnome-shell                         
304806 chris     20   0 1005964  54372  40312 S   2.3   0.2   1:00.46 gnome-system-mo                     
  8265 chris     20   0  851044  64084  39280 S   1.0   0.2  14:41.79 gnome-terminal-                     
  1111 polkitd   20   0  603836  12488   7528 S   0.7   0.0   3:37.71 polkitd                             
  7089 chris     20   0   33.0g 324364 171304 S   0.7   1.1   5:50.08 chrome                              
  7354 chris     20   0 1134.3g 355716 129476 S   0.7   1.2   6:32.51 chrome                              
296095 chris     20   0 1132.2g 160168 115772 S   0.7   0.5   1:14.49 chrome                              
299134 qemu      20   0   11.0g   2.9g  27264 S   0.7  10.2   1:25.34 qemu-system-x86                     
     1 root      20   0  217576  28572  10624 S   0.3   0.1   0:54.85 systemd                             
  1118 root      20   0   15232   7552   6784 S   0.3   0.0   0:25.38 systemd-machine                     
  2823 root      20   0  249680  19604   8064 S   0.3   0.1   7:15.86 sssd_kcm                            
  2955 chris     20   0  684472  17024  14720 S   0.3   0.1   9:13.72 gsd-smartcard                       
  3340 root      20   0  542844  13952  11776 S   0.3   0.0   0:04.69 abrt-dbus                           
  7090 chris     20   0   32.6g 155276 108568 S   0.3   0.5  13:29.98 chrome                              
  7363 chris     20   0 1132.3g 335376 120948 S   0.3   1.1   3:16.12 chrome                              
295131 chris     20   0 1136.3g 426468 132800 S   0.3   1.4   3:13.88 chrome                              
311918 chris     20   0  225500   4224   3072 R   0.3   0.0   0:00.21 top                                 
     2 root      20   0       0      0      0 S   0.0   0.0   0:00.20 kthreadd                            
     3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                              
     4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                          
     5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 slub_flushwq                        
```

This display is sorted by processor utilization (shown in the %CPU
column); you can change the sort order to memory utilization (%MEM) by
pressing Shift-M, and change back to processor utilization by pressing
Shift-P.

By default, this display is updated every 3 seconds; you can change the
update frequency by pressing S and typing a new update frequency (in
seconds between updates).

To terminate a process, press K; the program will prompt you for the
process ID to be killed (defaulting to the one at the top of the
display, using the most resources), and the signal to be sent to that
process (defaulting to signal 15, SIGTERM).

To see help messages about available options, press the ? key.

To exit from top, press the Q key (quit).

The *top* command is available on most Linux and Unix-like systems,
including matrix.senecacollege.ca. There are several newer commands
available, including *htop* and *btop*, but these are not present on all
systems.

## Graphical User Interface 

If you\'re using a GUI on a Linux system, many graphical process
monitoring and control tools are available, including the [Gnome System
Monitor](https:*gitlab.gnome.org/GNOME/gnome-system-monitor "wikilink")
and [Conky](https:*github.com/brndnmtthws/conky "wikilink").