# Comments

A comment in a bash script starts with a sharp symbol (#) and is ignored
by the shell interpreter:

~~~bash
# test script #1
# Written by Jason Bourne
~~~

A comment may also be just one portion of a line:

~~~bash
cd - # change to the user's previous working directory
~~~

Note that a shbang line is a comment from the point of view of the shell
interpreter \-- it\'s there for the kernel to use, not the shell!
