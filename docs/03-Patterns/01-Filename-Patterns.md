# Filename Patterns 

Linux and Windows systems both allow ambiguous filenames, which use
*wildcard* symbols to enable filename matching. The process of
converting an ambiguous filename, or filename pattern, into a list of
matching filenames is called *globbing* or *filename expansion*.

On a Linux system, globbing is performed by the shell. This means that
all arguments are subject to globbing, whether they\'re intended to be a
filename argument or not.

On a Windows system, ambiguous filenames are converted into a list of
filenames by the command or application. This means that arguments that
are not filenames are not subject to filename expansion. However, it
also means that applications must contain additional code to perform
globbing.

## Wildcard Symbols 

|Symbol|Meaning in Linux|Meaning in Windows|
|:---  |:---            |:---              |
|*|Matches zero or more characters|Matches zero or more characters|
|?|Matches one character|Matches one character, unless at the end of the filename or immediately before the dot preceeding the extension  in which case it matches zero or one character|
|<nowiki>[</nowiki>//list//<nowiki>]</nowiki> or <nowiki>[</nowiki>//range//<nowiki>]</nowiki>|Matches any one of the characters within the brackets (note that it matches exactly **one** of the characters)|//Not applicable//|


## Examples

|Pattern|Matches on Linux|Does not match on Linux|Matches on Windows|Does not match on Windows|
|:---   |:---            |:---                   |:---              |:---                     |
|*.html|first.html blue.html|RED.HTML purple.htm|Blue.html blue.html RED.HTML|purple.htm|
|a*|a aa aaa alpha argonaut|Alpha banana|a aa aaa alpha Alpha|banana|
|b*e|blue bite|red green blot|blue bite|red green blot|
|c<nowiki>[oa]</nowiki>t|cat cot|coat| |cat cot coat //(Not applicable)//|
|d?e|due doe|duo Doe date|due doe Doe|duo date|
|a??|aaa abc|aa abcd|aaa abc aa|abcd|

Therefore the command 

```plain
del *.pdf
```

on Windows, or

```plain
rm *.pdf
``` 

on Linux will remove all files in the current directory that have the
extension *.pdf*

You can combine absolute, relative, or relative-to-home pathnames with
patterns. For example, in the command:

```plain
 del \Users\jdoe\Documents\*.txt
```
the pattern \\Users\\jdoe\\Documents\\\*.txt* will match all files with
a *txt* extension in the *\\Users\\jdoe\\Documents\\* directory, and the
*del* command will then attempt to delete all of the matching files.

On Linux, you can also use patterns to match directory names:

```plain
 rm /home/chris/ops102/*/info.pdf
```

This will delete any files named *info.pdf* within any subdirectory of
*/home/chris/ops102/*
