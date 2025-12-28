# Script Parameters 

Arguments to a script are called parameters. You can access the
parameters using the special variables *%0*, *%1*, *%2*, and so forth.
*%0* contains the name of the script, *%1* contains the first parameter,
*%2* contains the second parameter, and so forth. (Note that there is no
second percent sign after the parameter number!)

The shift command gets rid of the first parameter and shifts every
parameter to a lower number.​

Examples:

~~~script
> type params.cmd​
@echo off​
ECHO PARAM 0: %0​
ECHO PARAM 1: %1​
ECHO PARAM 2: %2​

> params red green blue​
PARAM 0: params​
PARAM 1: red​
PARAM 2: green​

> type params-shift.cmd​
@echo off​
ECHO List of all arguments: %*​
:start​
IF "%1"=="" GOTO :done​
ECHO %1​
SHIFT​
GOTO :start​
:done​

> params-shift yellow orange red​
List of all arguments: yellow orange red​
yellow​
orange​
red
~~~

The special variable `%*` returns all of the parameters.

On the command line, parameters may be separated by:

- Space (or Tab)
- Comma [,]
- Semicolon [;]
- Equal sign [=]
