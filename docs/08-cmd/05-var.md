# Variables

## Setting a Variable 

To set a variable, use the *set* keyword with a variable name, an equal
sign, and the variable value:

~~~cmd
set A=5
set B=World
~~~

If the variable does not exist, it will be created. If it does exist,
the previous value will be discarded.

Variable names may contain letters, digits, or underscores, but must not
start with a digit. Case does not matter! The variable names *Number*,
*number*, and *NUMBER* all refer to the same variable.

Do not put spaces on either side of the equal sign.

Variables are not typed \-- they may be used as strings, integers, or
decimal values.

## Accessing a Variable 

To access a variable, place a percent sign \[%\] on either side of it,
and use it in a command as an argument (or as a command name):

~~~cmd
> SET B=World
> echo %B%
World
> echo Hello $B
Hello World
~~~

## Quoting

### Word Splitting and Quoting 

Quoting in the Windows shell is very different from Bash!

Using single or double quotes causes the quotes themselves to be
included as part of the string or argument in most cases, but not when
dealing with a filename:​

~~~cmd
> ECHO "Hello"​
"Hello"​

> ECHO test > "test file"​
~~~

​Quoting is not required when assigning a string value which contains
spaces to a variable:

~~~cmd
> SET A=One Two Three
> ECHO %A%
One Two Three
~~~

## Carat Symbols 

Escaping characters to remove their special meaning is performed using
the carat \[\^\] symbol in Windows.​ In this example, the ampersand \[&\]
symbol would normally cause an error, but it can be treated as a regular
character by escaping it with a carat:

~~~cmd
> echo Lost ^& Found
Lost & Found
~~~


When piping, a CMD subshell is started for each command in the pipeline,
and it is necessary to use triple carat symbols \^\^\^ to escape
characters:​

~~~cmd
> echo Lost ^^^& Found | find "Lost" ​
Lost & Found ​
~~~
