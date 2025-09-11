# Looping

In the Windows CMD shell, looping is performed with the *FOR* statement.

Loops are controlled by an iterator variable, which has special rules:

- The iterator variable name must be a __single letter__
- The variable name is __case sensitive__
- The variable name is written with a single preceeding percent sign
[%] at all times when used from the command line, or double preceeding 
percent signs [%%] inside a script

## Delayed Expansion 

When the body of a *FOR* loop is executed, the variables are expanded
(replaced by their values) before the loop begins. That means that any
variables that are contained in the loop have their values locked-in and
they can\'t be changed while the loop is executing.​

To allow updated variable values to be accessed within a loop:​

1\. Set the EnableDelayedExpansion option:​

~~~cmd
SETLOCAL EnableDelayedExpansion​
~~~

​2\. Change any variables which will be updated during the execution of
the loop by replacing the percent-signs ( `%` ) with exclaimation-marks (
`!` ):​

~~~cmd
%ERRORLEVEL%    ->    !ERRORLEVEL!​
~~~

## Loop throush a List of Files or Parameters 

To loop through a list of values such as filenames, use:

~~~cmd
FOR %variable IN (files) DO list​
~~~

The *variable* will be sequentially set to each of the given *files*
values, and the loop body (*list*) will be executed once for each
value.

The *files* value may be:

- A list of filenames: `FOR %F IN (file1.txt file2.pdf file3.c) DO ECHO %F`
- A filename pattern: `FOR %F IN (*.pdf) DO ECHO %F`
- Fixed strings: `FOR %C IN (Red Green Blue) DO ECHO %C`
- Or a list of all of the parameters: `FOR %P IN (%*) DO ECHO %P`

The `/D` option can be used along with a filename pattern to match only
directories:

~~~cmd
FOR /D %variable IN (files) DO list
~~~

### Example

~~~cmd
@echo off​ SETLOCAL EnableDelayedExpansion​ FOR %%F IN (\*) DO (​

rem The CHOICE command presents a Y/N choice and sets %ERRORLEVEL%
rem to 1 if the user selected Y and 2 if the user selected N

CHOICE /M "DELETE %%F"​
IF !ERRORLEVEL!==1 (​
  ECHO ...Deleting %%F​
  DEL %%F​
) ELSE (​
  ECHO ...Skipping %%F​
)​
~~~

## Loop through a Range of Integers 

~~~cmd
FOR /L (start, step, end) DO list
~~~

This type of loop counts forward or backwards from *start* to *end* by
a given *step*.

Example:​ ​

~~~cmd
@echo off​
rem Count from 0 to 5 in increments of 1​
FOR /L %%I IN (0,  1, 5) DO ECHO ... %%I ...​
 
rem Count from 4 to 0 in increments of -1​
FOR /L %%I IN (4, -1, 0) DO ECHO ... %%I ...
~~~

Output:

~~~plain
0
1
2
3
4
5   <- This is the end of output from the first loop, having gone from 0 to 5
4   <- The second loop starts output here, going from 4 to 0
3
2
1
0
~~~
