# Using Regular Expressions

Regular expressions can be used in many places, including:

- Linux
    - GNU `grep`
    - The bash test command `[[ "string" =~ regexp ]]`
        - Note that the regular expression is __not__ quoted
        - If you need to use a space in your regular expression, store the regex in a variable and use the variable as the regex argument in the command.
        - Example: `X="ABC"; if [[ "$X" =~ ^[[:upper:]]{3}$ ]]; then echo "MATCH" ;
 else echo "NO MATCH" ; fi`
    - The `less` command, using the / and ? keystrokes for searching forward and backward
    - The `vi`/`vim` editor, also using the / and ? keystrokes for searching forward and backward
    - The `sed` and `awk` utilities

- Windows
    - `findstr /R` (see notes below)
    - Many PowerShell commands

- Programming Languages (Cross-Platform)
    - Cross-platform Shells (Powershell, zsh, bash)
    - Python
    - JavaScript
    - Perl
    - C / C++ via [PCRE/PCRE2 library](https:*www.pcre.org/ "wikilink")\
    - *...and many others!*
