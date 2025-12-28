# Reading Variable Values from Stdin: SET /P 

You can read values from standard input (stdin) and assign them to a
variable with the set command using the /p option (aka switch). When you
do this, the value specified on the right-hand side of the equal sign is
used as the prompt presented to the user:

~~~cmd
> set /p NAME=Enter your name:
Enter your name: J. Doe

> echo %NAME%
J. Doe
~~~

Here is a script which uses a couple of *SET /P* statements:

~~~cmd
@echo off​
set /p NAME=Please enter your name:​
echo Please to meet you, %NAME%​
set /p FILE=Please enter a filename:​
echo Saving your name into the file...​
echo NAME=%NAME% >> %FILE%​
echo Done.​
~~~

## Command Capture 

There is no direct equivalient to command capture, but it is possible to
use *SET /P* with redirection *from* standard input using the
less-than \[\<\] symbol to capture one line of text:

~~~cmd
> DATE /T >X
> SET /P D= ``<X
> ECHO %D%
2024-12-11
~~~