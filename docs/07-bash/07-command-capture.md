# Command Capture 

You can capture the output (stdout) of a command as a string using the
notation `\$( )` and then use that string in a variable assignment or as
a command argument:

~~~plain
$ echo "The current date and time is: $(date)"
The current date and time is: Mon 19 Jun 2034 12:02:11 AM EDT

$ FILES="$(ls|wc -l)"
$ echo "There are $FILES files in the current directory $(pwd)"
There are 2938 files in the current directory /bin
~~~
**Avoid Backticks!** You may see old scripts that use backticks
        (reverse single quotes) for command capture, like this:

~~~bash
``  $ A=`ls` `
~~~

This is an archaic syntax which is depricated \-- avoid doing this. Some
fonts make it hard to distiguish between backticks and single-quotes,
and nesting backticks is difficult.

