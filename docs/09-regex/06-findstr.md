# Windows findstr and Regular Expressions 

The Windows `findstr` command accepts regular expressions or literal
expressions. It will guess what you're using, and may guess
incorrectly, so it's best to use the `/R` and `/L` options to directly
specify if your search pattern is a regexp or literal.

Findstr permits multiple search patterns in a quoted string, separated
by a space; this acts like a type of alternation. However, this makes it
impossible to use a literal space in a search pattern. If you wish to
include a space in your search pattern, prepend `/C:` to your search
string. You can use multiple `/C:` search strings.

For example, `FINDSTR /R /C:"red" /C:"blue" INPUTFILE` is roughly
equivalent to `grep -E "red|blue" INPUTFILE`

Findstr is also limited to (approximately) 127 characters in the regular expression.

For information on findstr's regular expression dialect, see `help findstr`. In particular, the findstr command does not support:

- alternation with the `|` symbol
- repetition other than with the `*` symbol
- named character classes `[[:*name*:]]`
- grouping `( )`
- 