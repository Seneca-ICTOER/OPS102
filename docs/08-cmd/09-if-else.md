# Conditional Logic: IF/ELSE 

The *IF* command takes a test, and uses the result of the test to
control the execution of one or more commands. An *ELSE* clause is
optional; if included, the first conditional commands should be placed
in parenthesis.​

~~~cmd
> set A=Blue                                       ​
> set B=Orange​
> set C=Blue​
​> if %A%==%C% echo Strings A and C match​
Strings A and C match​
> if %A%==%B% (echo Same!) else echo Different!​
Different!
~~~

### Available Tests 

There are four main types of tests available:

## Tests Group 1: Filesystem Entries 

Tests that a filename exists (regardless of the entry type: file or
directory):

~~~cmd
EXIST filename
~~~

## Tests Group 2: String Equality 

Test for string equality:

~~~cmd
`string1`*`==`*`string2`
~~~

## Tests Group 3: String and Numeric Comparisons 

These tests accept two string arguments, both strings or both integers,
which are compared. Adding the /i switch will make string comparisons
case-insensitive (UPPER/lowercase).​

~~~cmd
value1 EQU value2    True if the values are equal​
value1 NEQ value2    True if the values are not equal​
value1 LSS value2    True if the value1 less than value2 ​
value1 LEQ value2    True if the value1 less/equal to value2​
value1 GTR value2    True if the value1 greater than value2​
value1 GEQ value2    True if the value1 greater than or equal to to value2​
~~~

To force a string comparison, enclose *value1* and *value2* in quotes.
Otherwise, the shell will determine if the variables appear to contain
integer values and compare them as integers, or otherwise compare them
as strings.

## Tests Group 4: Variable Definition, Errorlevel 

Test to see if a variable is defined​: ​

~~~cmd
DEFINED variable    True if variable is defined​
~~~

Test to see if the ERRORLEVEL is above a threshold​:

~~~cmd
ERRORLEVEL value    True if ERORRLEVEL>=value​
~~~

Although it\'s probably better to just an integer comparison such as:
`%ERRORLEVEL% GEQ value​`

## Notes about IF and these Tests 

- These tests work only with the `*`IF`*` command
- The IF command can be used with `*`GOTO`*` and a label:

~~~cmd
IF test GOTO :skip​
...​
:skip​
~~~

Note that using a GOTO in a loop will make the shell forget about the
loop, regardless of where the label is located!​

## Negating and Combining Tests 

You can negate (invert) a test with the NOT operator:

~~~cmd
IF NOT EXIST %N% ECHO The file %N% does not exist.
~~~

Note that you cannot combine tests - there is no *AND* or *OR* operator.
