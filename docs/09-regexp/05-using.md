# Using Regular Expressions

Regular expressions can be used in many places, including:

- Linux
  - GNU `*`grep`*\
  - The bash test command `*`[[ "string" =~ regexp ]]`*\
    - Note that the regular expression is __not__ quoted
    - Example: `X="ABC"; if [[ "$X" =~ ^[[:upper:]]{3}$ ]]; then echo "MATCH" ;
 else echo "NO MATCH" ; fi`
  - The `less` command, using the / and ? keystrokes for searching forward and backward
  - The `vi`/`vim` editor, also using the / and ? keystrokes for searching forward and backward
  - The `sed` and `awk` utilities

- Windows
  - `findstr /R` (see notes below)

- Programming Languages (Cross-Platform)
  - Cross-platform Shells (Powershell, zsh, bash)
  - Python
  - JavaScript
  - Perl
  - C / C++ via [PCRE/PCRE2 library](https:*www.pcre.org/ "wikilink")\
  - ...and many others!
