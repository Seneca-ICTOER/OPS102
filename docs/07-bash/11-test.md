# The test Command 

To perform tests, such as comparisons, bash provides the *test* command.

Test accepts parameters that comprise a test, such as a test for string
equality, and returns a status code of 0 if the test succeeds or non-0
if it fails:

~~~bash
test "$NAME" == "Chris"
~~~

This is used with the *if* statement like this:

~~~bash
if test "$NAME" == "Chris"
then
  SUPERPOWERS="Yes"
fi
~~~

However, this syntax is a bit ugly! So bash provides a synonym for
*test* which is *\[\[ \]\]*:

~~~bash
if `[`"$NAME" == "Chris"`]("$NAME"_==_"Chris" "wikilink")\
then
  SUPERPOWERS="Yes"
fi
~~~

Remember that the double square-brackets are really just the *test*
command in disguise. This means that the arguments are command
arguments, and need to be separated by spaces, just as they would with
any other command such as *ls* or *cp*.

- Note: The original test command in the original Unix shell
        (the Bourne shell) was aliased to the single square bracket *\[
        \]*. For compatibility, this is still available in the bash
        shell. However, the double square-bracket version of the test
        command has some improved capabilities, and is recommended
        (except when you need a script that is compatible with a wide
        range of different shells).

### Available Tests 

There are four main types of tests available:

## Tests Group 1: Filesystem Entries 

These tests check a filename to see if it is a regular file, a
directory, or a symbolic link:

~~~bash
[`-f filename`](-f_filename "wikilink")`   # True if filename is a regular file
[`-d filename`](-d_filename "wikilink")`   # True if filename is a directory
[`-L filename`](-L_filename "wikilink")`   # True if filename is a symbolic link
~~~

-  Note: If a symbolic link points to a file, then both the
        *-f* and *-l* tests will succeed. If a symbolic link points to a
        directory, then both the *-d* and *-l* tests will succeed.

## Tests Group 2: File Permissions 

These tests check a filename to see if the person running the script can
read, write, or execute the file (or access the directory):

~~~bash
[`-r filename`](-r_filename "wikilink")`   # True if filename is readable
[`-w filename`](-w_filename "wikilink")`   # True if filename is writable
[`-x filename`](-x_filename "wikilink")`   # True if filename is executable (accessible if a directory)
~~~

## Tests Group 3: Strings 

These tests accept two string arguments, which are compared:

~~~bash
[`string1 == string2`](string1_==_string2 "wikilink")`   # True if the strings are equal
[`string1 != string2`](string1_!=_string2 "wikilink")`   # True if the strings are not equal
[`string1 > string2`](string1_>_string2 "wikilink")`   # True if string1 sorts after string2 lexicographically
[`string1 < string2`](string1_<_string2 "wikilink")`   # True if string1 sorts before string2 lexicographically
~~~

-  A note on the term *lexicographically*: Sorting
        *lexicographically* means sorting according to character code.
        This is like sorting alphabetically, but it applies to
        non-alphabetic characters as well, such as digits and
        punctuation marks. See the manpage for \"ascii\" to see the
        sequence of the first 128 character codes (or refer to a Unicode
        table for all of the character codes).

When sorting lexicographically, a comes before aa, which comes before b:

~~~plain
a
aa
b
~~~

In a similar way, 1 comes before 11, which comes before 2:

~~~plain
1
11
2
~~~

Note that this is different from numeric order, where 2 would preceed
11:

~~~plain
1
2
11
~~~

## Test Group 4: Integers 

These tests accept to integer arguments, which are compared:

~~~bash
[`integer1 -eq integer2`](integer1_-eq_integer2 "wikilink")`  # Integers are equal
[`integer1 -ne integer2`](integer1_-ne_integer2 "wikilink")`  # Integers are not equal
[`integer1 -gt integer2`](integer1_-gt_integer2 "wikilink")`  # Integer1 is greater than integer2
[`integer1 -ge integer2`](integer1_-ge_integer2 "wikilink")`  # Integer1 is greater than or equal to integer2
[`integer1 -lt integer2`](integer1_-lt_integer2 "wikilink")`  # Integer1 is less than integer2
[`integer1 -le integer2`](integer1_-le_integer2 "wikilink")`  # Integer1 is less than or equal to integer2
~~~

## Other Tests 

The four groups of tests above will cover the vast majority of
situations. There are additional tests available to test other
conditions, such as whether a variable is defined, or a file refers to a
device. See the man page for bash(1) for more information if you\'re
interested in other tests: *man bash*

## Negating and Combining Tests 

The *!* operator can be used to negate a test:

~~~bash
[`! -f "$FILE"`](!_-f_"$FILE" "wikilink")`   # True if "$FILE" is not a file (doesn't exist, or is a directory)
~~~

The AND operator *&&* combines tests, with the result being True if the
tests on the left and right are both true:

~~~bash
[`$A -lt $B && $B -lt $C`]($A_-lt_$B_&&_$B_-lt_$C "wikilink")`  # True if A is less than B, and also B is less than C.
~~~

The OR operator *\|\|* combines tests, with the result being True if
either of the tests are true:

~~~bash
[`| $A -lt 0 `]($A_-gt_$B "wikilink")` # True if either: A is greater than B, or if A is less than 0.
~~~

You can use multiple *!*, *&&*, and *\|\|* operators toegether:

~~~bash
[`-f "$FILE" && -r "$FILE" && -w "$FILE"`](-f_"$FILE"_&&_-r_"$FILE"_&&_-w_"$FILE" "wikilink")` # True if "$FILE" is a readable, writable regular file.
~~~

## Tips on Using Tests 

- Remember to quote any arguments which include whitespace, or which may be 
null (empty).
- Be careful with the `<` and `>` comparison operators: if you have 
a syntax error, you may accidentally redirect data (which in the case of 
`>` might overwrite a file!)
