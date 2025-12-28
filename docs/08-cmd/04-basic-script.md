# A Basic CMD Script Example 

Here is a simple example script using two commands, *echo* and *date*:

~~~plain
@echo off
echo The current date is:
date /t
~~~

The script can then be executed. Normally, the current working directory
is not searched, so to run the a script in the current directory, you
will need to explicitly specify the directory name like this:

~~~plain
> now
The current date is:
2024-12-11
~~~
