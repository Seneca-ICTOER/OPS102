# Looping in Bash 

There are four types of loops in bash:

- `for *VARIABLE* in *LIST*`
- `for (( ; ; ))`
- `while *EXPR*`
- `until *EXPR*`


In every case, the actual body of the loop is contained within *do* \...
*done* keywords.

## for VARIABLE in LIST 

This type of loop iterates through a list of values; the *VARIABLE* is
sequentially set to the each of the items in the list of values and the
body of the loop is executed for each value. The list of values may be
constants:

~~~bash
for X in 1 2 3
do
  ... body of the loop ...
done
~~~

~~~bash
for COLOUR in red green blue
do
  ... body of the loop ...
done
~~~

Or the list may be the list of parameters (arguments to the script),
written as *\"\$@\"*:

~~~bash
for A in "$@"
do
  ... body of the loop ...
done
~~~

The most common use of this type of loop may be one or more globbing
patterns (filename patterns with wildcard characters), which will be
replaced with a list of all matching filenames:

~~~bash
for SOURCEFILE in *.c
do
  ... body of the loop ...
done
~~~

One thing to remember with this last form of the loop is that *if the
pattern does not match any file* then the pattern itself will be
assigned to the variable. For example, in the example above, if there
are no files that match the pattern `*.c` then the variable SOURCEFILE
will be set to the actual pattern: `SOURCEFILE=*.c`

This can be used in various ways. For example, this loop will compile
all of the C source files found in the current directory:

~~~bash
for SOURCEFILE in *.c
do
  echo "=== Compiling $SOURCEFILE ==="
  
  # This next line removes the extension from the filename
  BINARY="$(echo $SOURCEFILE | cut -d. -f1)"
  
  gcc SOURCEFILE -o $BINARY
done
~~~

(It\'s also possible to generate the `LIST` in other ways \-- for
example, from the output of another command, captured with `$( )` )

## The \"C-style\" for loop: for (( ; ; )) 

This loop is very similar to the \"for\" loop available in the C
language. The C parenthesis are changed to bash double-parenthesis, to
invoke the bash arithmetic syntax, and the curly-braces `{ }` used in C
are replaced by the bash *do* and *done* keywords. The three arguments
in the double-parenthesis are the initial condition (variable
initialization), the control condition (an expression that, while true,
causes the loop to continue), and the increment/decrement (an expression
which is executed at the end of each loop, which typically increments or
decrements a counter).

For example, this loop counts from 1 to 10:

~~~bash
for (( i=0; i<=10; i++ ))
do
  echo $i
done
~~~

## while EXPR 

This loop continues as long as the expression *EXPR* is true:

~~~bash
while [[ "$A" == "$B" ]]
do
  ... body of the loop ...
done
~~~

*EXPR* may be any single bash command, or a list of bash commands
separated by newline characters (ENTER key) or semicolons, or a pipeline
of commands. Most commonly it is a `test` `[[` command.

## until EXPR 

This loop continues as long as the expression *EXPR* is false:

~~~bash
until [[ "$X" -gt "$Y" ]]
do
  ... body of the loop ...
done
~~~

This loop will continue as long as *\$X* is less than or equal to *\$Y*
\-- as soon as the expression becomes true (when *\$X* is greater than
*\$Y*), the loop will stop.

# Examples

Here are a few bash scripting examples that include loops:

## tput Colour Codes 

The *tput* command outputs terminal codes to stdout to perform actions
such as setting the text colour, clearing the screen, and so forth.

The *tput setaf *n** and *tput setab *n** commands set the
foreground and background text colours, respectively. To see the
available colours, this script can be used:

~~~bash
#!/usr/bin/bash
for ((C=0; C<16; C++))
do
  tput setaf $C   # Set foreground to colour $C
  echo "Colour $C"
done
tput sgr0   # Reset to "normal" text mode
~~~

## Number-Guessing Game 

This is the main example from the lecture. Study this code and 
ensure that you understand what it does (tip: test it, and alter it to see
what effect your changes have):

~~~bash
#!/usr/bin/bash

MAX=100       # Maximum value of secret
MAX_TRIES=7   # Maximum number of tries (guesses)
GAMES=0       # How many games have been played
WINS=0        # How many games the user has won

clear     # Clear the screen
tput setaf 5  # Select purple text
echo "=== Number-Guessing Game ==="
echo
echo "I have a secret number between 1 and $MAX"
echo "Your mission is to guess it in as few tries as possible."
echo "You have a maximum of $MAX_TRIES guesses to succeed."
echo

PLAY="Y"
# This next loop continues until the user says
# they don't want to play again
while [[ "$PLAY" == "Y" || "$PLAY" == "y" || "$PLAY" == "YES" ||
     "$PLAY" == "Yes" || "$PLAY" == "yes" ]]
do
      # Generate a random number from 1-MAX
  SECRET=$(( RANDOM % MAX + 1 ))  

      # Un-comment this line when debugging!
      # echo "NOTE: the secret number is $SECRET"

  GUESS=0
  TRIES=0
  ((GAMES++))

  # This next loop continues until the user guess correctly
  # or the maximum number of guesses is exhausted
  until `[`| $TRIES -ge $MAX_TRIES `]($GUESS_-eq_$SECRET "wikilink")\
  do
      tput setaf 15   # White text
      read -p "Enter your guess (#$((++TRIES))): " GUESS
      if `[`$GUESS -gt $SECRET`]($GUESS_-gt_$SECRET "wikilink")\
      then
          tput setaf 1    # Red text
          echo "Too high!"
      elif `[`$GUESS -lt $SECRET`]($GUESS_-lt_$SECRET "wikilink")\
      then
          tput setaf 1    # Red text
          echo "Too low!"
      else
          tput setaf 10   # Green text
          echo "You got it in $((TRIES)) tries!"
          ((WINS++))
      fi
      echo
  done
  if `[`! $GUESS -eq $SECRET`](!_$GUESS_-eq_$SECRET "wikilink")\
  then
      tput setaf 11   # Yellow text
      echo "You lose after $TRIES attempts. The number was $SECRET. "
  fi

  tput setaf 15   # White texxt
  echo 
  read -p "Do you want to play again (Y/N)? " PLAY
  echo

done
tput setaf 5  # Purple text

# In the next line, the multiplication 
# must preceed the division because 
# this is integer math
echo "You executed $GAMES missions and succeeded $WINS times ($((WINS*100/GAMES))% success)."

echo
tput sgr0 # Reset to normal text
~~~