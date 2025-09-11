# Variables

## Setting a Variable 

To set a variable, simply type the variable name, an equal sign, and the
variable value:

~~~bash
A=5
B=World
TheNameOfTheUser=Jason
~~~

If the variable does not exist, it will be created. If it does exist,
the previous value will be discarded.

Variable names may contain letters, digits, or underscores, but must not
start with a digit.

Unlike some computer languages such as C, variables do not need to be
declared. Variables are not typed \-- they may be used as strings,
integers, or decimal values.

Note that there must not be a space on either side of the equal sign.

## Accessing a Variable 

To access a variable, place a dollar sign \[\$\] in front of it, and use
it in a command as an argument (or as a command name):

~~~bash
$ B=World
$ echo $B
World
$ echo Hello $B
Hello World
~~~

## Quoting

### Word Splitting and Quoting 

Spaces and tabs are used to split a bash command line into individual
\"words\". This means that if you use an argument that contains a space,
it will be treated as two separate arguments:

~~~plain
$ mkdir test
$ cd test           # this is new so it will be empty
$ touch new file
$ ls -l
total 0                                                                                                                 
-rw------- 1 chris.tyler users 0 Mar  6 12:12 file                                                                      
-rw------- 1 chris.tyler users 0 Mar  6 12:12 new    
~~~

Notice that *touch new file* created two files, because *new* and *file*
were treated as separate arguments.

To prevent word splitting, quote the text.

~~~plain
$ mkdir test
$ cd test          # this directory is new so it will be empty
$ touch "new file"
$ ls -l 
total 0                                                                                                                 
-rw------- 1 chris.tyler users 0 Mar  6 12:15 new file 
~~~

Notice that only one file was created by the command `touch \"new
file\"` because the quotes prevented word splitting, and the single
argument *new file* was used as a single filename.

You\'ll also need to use quoting when assigning a string variable value
containing a space:

~~~plain
$ A="Seneca Polytechnic"
~~~

You can quote text with single-quotes \[\'\] or double-quotes \[\"\].
Variable expansion takes place inside double quotes (this is called
*interpolation*), but not inside single quotes:

~~~plain
$ B=World
$ echo "Hello $B"    # notice that $B is replaced with the value of B
Hello World
$ echo 'Hello $B'    # notice that $B used as-in
Hello $B
~~~

You should always double-quote variables that may contain a space in
their value when using them as command arguments. This is especially
true for filenames \-- you never know when a user is going to put a
space in a filename! Many scripts work find with opaque filenames (those
containing no whitespace) but fail with non-opaque names.

Here is an example \-- the difference between the first *ls* statement
(which does not double-quote the variable) and the second *ls* statement
(where the variable expansion is double-quoted):

~~~plain
$ touch "red maple"

$ FILE="red maple"

$ ls $FILE
ls: cannot access 'red': No such file or directory
ls: cannot access 'maple': No such file or directory

$ ls "$FILE"
'red maple'
~~~

### Backslashes

A backslash \[\\\] character outside of quotes or inside double quotes
instructs the shell to ignore any special meaning that the following
character may have. Examples:

~~~plain
$ touch "new file"
$ ls -l new\ file     # The space loses its special meaning as an argument separator
-rw-r--r--. 1 chris chris 0 Jun 18 22:49 'new file'

$ echo "This string contains a \"quoted\" string"
This string contains a "quoted" string

$ A=Testing
$ echo "  \$A"   # The dollar sign loses its special meaning
  $A
~~~

