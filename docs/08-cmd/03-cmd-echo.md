# Command Echos​ 

Windows defaults to displaying each command in a script before executing
it (the opposite of the default in the bash shell). If you do not want
each command to be displayed, you can:​

- Add an @ sign in front of each command, or​
- Issue the echo off command.​

Usually, you\'ll combine these in a script, using this as one of the
first lines:​

~~~cmd
@echo off​
~~~