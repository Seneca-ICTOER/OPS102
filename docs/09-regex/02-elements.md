# The Seven Basic Elements of Regular Expressions 

## 1. Characters

In a regular expression (regexp), any character that doesn\'t otherwise have a special meaning matches that character. So the digit `5`, for example, matches the digit `5`; similarly `cat` matches the letters `c`, `a`, and `t` in sequence.

A backslash can be used to remove any special meaning which a character has. The period character `.` is a type of wildcard (see below), so to search for a literal period, we place a backslash in front of it: `\.`

## 2. Wildcards

A period `.` will match any single character. Similarly, three periods `...` will match any three characters.

You can combine characters and wildcards: the regex `a.e` will match the letter `a` followed by any one character followed by the letter `e`. Therefore, it will match `age` but not `app` or `angle`.

## 3. Bracket Expressions / Character Classes 

Bracket Expressions or Character Classes are contained in square brackets `[ ]`

- A list of characters in square brackets will match any *one* character from the list of characters: `[abc]` will match `a`, `b`, or `c`

- A range of characters in square brackets, written as a starting character, a dash, and an ending character, will match any character in that range: the regular expression `[0-9]` will match any one digit.

- There are some pre-defined named character classes. These are selected by specifying the name of the character class surrounded by colons and square brackets, placed within outer square brackets, like `[[:digits:]]`. The available names are:
    - alnum - alphanumeric
    - alpha - alphabetic characters
    - blank - horizontal whitespace (space, tab)
    - cntrl - control characters (text codes that don't print, such as newline, tab, and bell)
    - digit - digits
    - graph - letters, digits, and punctuation
    - print - letters, digits, punctuation, and space
    - punct - punctuation marks
    - space - horizontal and vertical whitespace (space, tab, vertical tab, 
form feed)
    - upper - UPPERCASE letters
    - lower - lowercase letters
    - xdigit - hexidecimal digits (digits plus a-f and A-F)
- Ranges, lists, and named character classes may be combined - 
e.g., `[[[:digit:]]+-.,]`  `[[:digit:][:punct:]]`  `[0-9_*]`
- To invert a character class, add a carat `^` character as the first character after the opening square bracket: `[^[:digit:]]` matches any non-digit  character, and `[^:]` matches any character that is not a colon.
- To include a literal carat, place it at the end of the character class.
- To include a literal dash or closing square bracket, place it at the start of the character class.
- Two important caveat to consider:
    - Named character classes will match symbols from any alphabet. For example, `[[:alpha:]]` will match alphabetic characters from any language, and `[[:digit:]]` will match *any* digit symbols, including symbols such as `۱۲۳۴۵۶۷۸۹߀߁߂߃߄߅߆߇߈߉०१२३४५६७८९٠`
    - The "collation sequence" of characters determines the order of characters for sorting and comparision purposes. This may affect what is included in ranges used within bracket expressions. For example, in some collation sequences, capital letters may be interspersed between lowercase letters (`aAbBcCdD...zZ`), so the bracket expression `[a-z]` will include all of the uppercase letters except for `Z`. On Linux systems, the `LC_COLLATE` environment variable controls the collation sequence (see the manpages for `locale(1)`, `locale(5)`, `locale(7)`, and `charmap(5)`). 

## 4. Repetition

- A repeat count can be placed in curly brackets. It applies to the previous element:  `x{3}` matches `xxx`
- A repeat can be a range, written as *min,max* in curly brackets: `x{2,5}` will match `xx`, `xxx`, `xxxx`, or `xxxxx`
- The maximum value in a range can be omitted: `x{2,}` will match two or more `x` characters in a row
- There are short forms for some commonly-used ranges:
  - `*` is the same as `{0,}` (zero or more)
  - `+` is the same as `{1,}` (one or more)
  - `?` is the same as `{0,1}` (zero or one)

## 5. Alternation

- The vertical bar indicates alternation &mdash; either the expression on the left or the right can be matched: `hot|cold` will match `hot` or `cold`

## 6. Grouping

- Elements placed in parenthesis are treated as a group, and can be repeated:
`(na)* batman` will match `nananana batman` and `nananananananana batman`
- Grouping may also be used to limit alternation: `(fire|green)house` will match `firehouse` or `greenhouse`

## 7. Anchors

- Anchors match *locations*, not characters.
- A carat symbol will match the start of a line: `^[[:upper:]]` will match lines that start with an uppercase letter.
- A dollar sign will match the end of a line: `[[:punct:]]$` will match
lines that end with a punctuation mark.
- The two anchors may be used together: `cat` will match the word `cat` anywhere on a line, but `^cat$` will only match lines that contain *just* the word `cat` and nothing else. Similarly, `^[0-9.]$` will match lines that are made up of only digits and dot characters, and `^...$` or `^.{3}$` will only match lines that contain exactly three characters.
