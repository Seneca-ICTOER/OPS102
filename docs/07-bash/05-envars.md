# Environment Variables 

By default, a variable is local to the shell in which it is running.

You can *export* variables to make them *environment variables*.
That means that they are passed to programs executed by the shell.

Environment variables are used by all proccesses, not just the shell,
and are commonly used to pass configuration information to programs.

To create an environment variable named X with a value of 999:

~~~plain
$ X=999
$ export X
~~~

Or in a single step:

~~~plain
$ export X=999
~~~

You can view all of the current variables (and shell functions) with the
*set* command, or just the environment variables with the *printenv*
command (you\'ll probably want to pipe the output through *less*).

The term *environment variable* is often shortened to the abbreviation
*envar*.

## Common Environment Variables 

| Environment Variable | Purpose | Examples |
|:---                  |:---     |:---      |
| PS1 | Normal (first-level) shell prompt | PS1="Enter command: "<br />PS1="[\u@\h \W]\$ " |
| EDITOR | Path to the default text editor (typically /usr/bin/nano) | EDITOR=/usr/bin/vi |
| PATH | A colon-separated list of directories that will be searched when looking for a command | PATH="$PATH:."<br />PATH="/usr/bin:/usr/sbin:." |
| LANG | The default language -- used to select message translations as well as number, currency, date, and calendar formats. | LANG=en_CA.UTF-8<br />LANG=fr_CA.UTF-8 |
| HOME | The user's home directory - used for relative-to-home pathnames. | HOME=/var/tmp |
| RANDOM | A random integer (0-32767) | |

