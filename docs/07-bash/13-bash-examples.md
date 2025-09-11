# Bash Example Scripts

## Computer Architecture 

This script displays a message based on the architecture of the
computer:

~~~bash
#!/usr/bin/bash​
architecture="$(uname -m)" # uname gets system information​
​
if `[`"$architecture" == "x86_64"`]("$architecture"_==_"x86_64" "wikilink")`​
then​
   echo "Your computer architecture is Intel/AMD x86_64."​
elif `[`"$architecture" == "aarch64"`]("$architecture"_==_"aarch64" "wikilink")`​
then​
   echo "Your computer uses the 64-bit Arm architecture."​
else​
  echo "Your computer uses an unrecognized architecture."​
fi
~~~

## Age Check 

This script checks whether a customer is of legal drinking age in
Ontario:

~~~bash
#!/usr/bin/bash​
read -p "Enter the customer's date of birth: " B​
​
# Calculate the time in seconds that the customer turns/tuned 19​
D="$(date -d "$B + 19 years" +%s)"​
 ​
# Get the current time in seconds
NOW="$(date +%s)"​

# Tell the user if the customer is old enough to be served alcohol​
# This tests checks to see if the customer's 19th birthday is
# less than (before) the current date.
if `[`"$D" -lt "$NOW"`]("$D"_-lt_"$NOW" "wikilink")`​
then​
    echo "The customer is of legal drinking age in Ontario."​
else​
    echo "The customer is too young to legally drink in Ontario."​
fi
~~~

## Coinflip

This script flips a virtual coin:

~~~bash
#!/usr/bin/bash​

COINFLIP=$((RANDOM % 2))​  # % is the modulus operator
if `[`"$COINFLIP" == 0`]("$COINFLIP"_==_0 "wikilink")`​
then​
    echo "Heads! 🙂"​
else​
    echo "Tails 😦"​
fi
~~~

The COINFLIP variable is set to the remainder of the division of
`$RANDOM` by 2. Therefore, it will have a random value of 0 or 1.

Note that this script uses extended Unicode characters \-- however, for
these to display properly, your terminal and your terminal font must
both support the extended characters. Besides emoji, extended characters
may be used to display accented characters, symbols, and characters from
other languages.

## Cautious File Delete 

This script checks a file, provided as a positional argument
(parameter), to ensure that it is a regular file and is writable, and
then asks the user if they want to delete it. Note that this script uses
the *-f* (file) test, *-w* (writeable) test, and combines a number of
string tests with the *\|\|* (OR) operator:

~~~bash
#!/usr/bin/bash​
if `[`"$#" -ne 1`]("$#"_-ne_1 "wikilink")\
then
    echo "$(basename $0): Error: one filename argument must be provided." >&2
    exit 1
fi
F="$1"  # Put the first (and only!) argument value into the variable F
if [ ! -f "$F" ]​
then​
    echo "The filename '$F' does not refer to a regular file - skipping."​
elif [ ! -w "$F" ]​
then​
    echo "The file '$F' is not writeable (by you) - skipping."​
else​
    read -p "Delete the regular file '$F'? (Y/N): " YESNO​
    if [[ "$YESNO" == "Y" || "$YESNO" == "y" || "$YESNO" == "Yes" ​
           || "$YESNO" == "yes" || "$YESNO" == "YES" ]]​
    then​
        echo "Deleting the file '$F'..."​
        rm "$F"    # We should add some code to check if the rm succeeds or fails​
        echo "...done."​
    else​
        echo "Skipping the file '$F' as requested."​
    fi​
fi
~~~
