# Basic Requirements for Shell Scripts 

1\. **Create a text file containing shell commands.** Use any text
editor (nano, vi, VS Code, gnome-text-editor, eclipse, \...) to create
the file.

2\. **Tell the operating system which shell to use.** Add a
\"shbang\" line to the very top of the file, containing the text:

~~~bash
#!/usr/bin/bash
~~~

The first two chacters, the \*\*sh\*\*arp (#) and \*\*bang\*\* (!) give
this line its name. They are recognized by the operating system kernel
as identifying a script. The remainder of this line is interpreted by
the kernel as the name of the shell which is to be used to interpret the
script. In this case, */usr/bin/bash* is the absolute path of the bash
shell. You can substitute other interpreters to write scripts in other
shell dialects (such as the Z-shell, */usr/bin/zsh*) or languages (such
as python, */usr/bin/python*).

Note that there must be nothing in font of the #! characters \-- no
space and no blank lines.

3\. **Ensure that the script has appropriate permissions.** The
kernel requires execute \[x\] permission, and the shell requires read
\[r\] permission. Set this up with the chmod command (for example,
`chmod u+rx scriptname`).

Here is a simple example script using two commands, *echo* and *date*:

~~~bash
#!/usr/bin/bash
echo "The current date and time is:"
date
~~~

Notice the presence of the shbang line.

If this is save into the file named \"now\", the permission could be set
with this command:

~~~plain
$ chmod u+rx now
~~~

The script can then be executed. Normally, the current working directory
is not searched, so to run the a script in the current directory, you
will need to explicitly specify the directory name like this:

~~~plain
$ ./now
The current date and time is:
Sat Mar  6 12:03:32 EST 2038
~~~