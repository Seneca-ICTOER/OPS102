# Exit Status Codes 

When any process finishes executing, it exits with a numeric value. This
can be called the exit code, status code, exit status code, or error
code.

Usually, an exit status code of zero (0) means that no errors were
encountered, and a non-zero code means that something went wrong.
Therefore, it may be easiest to think of this as the error code, with 0
meaning no errors.

Be aware that program authors can use this value as they see fit, so the
status code may indicate something else, such as the number of data
items processed.

The special variable *\$?* is set to the exit status code of the last
command executed by the shell.

For example:

~~~plain
$ ls -d /etc
/etc
$ echo $?
0

$ ls -d /this/does/not/exist
ls: cannot access '/this/does/not/exist': No such file or directory
$ echo $?
2
~~~

Why is this important? Because exit status codes are the key to
conditional logic (if\...) and looping (for/while/until/\...) in bash
scripting.
