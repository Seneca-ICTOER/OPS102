# Common Simple Commands 

Here are some basic commands useful for managing the filesystem and
performing basic tasks:

| Linux | Windows | Description |
|:---   |:---     |:---         |
|ls|dir|Lists the contents of a directory -- by default, the current directory, or the directories specified as arguments (or a specific file, if specified).|
|echo|echo|Places a message on the screen (the message is given as positional arguments)|
|cal|  |Displays a simple calendar|
|date|date /t<br />time /t|Tells you the current date (or date/time)|
|who|quser|Displays information about the logged in user(s)|
|whoami|whoami|Displays the name of the current user|
|clear|cls|Clears the screen (terminal). Note: in the Bash shell, you can also clear the screen during command entry by typing Ctrl+L|
|tree|tree|Displays a "tree view" of the filesystem hierarchy starting at the current directory (or the given directory, if an argument is provided).|
|mkdir|mkdir|Make a directory/folder|
|rmdir|rmdir|Remove a directory/folder|
|rm|del|Removes/deletes one or more files. Specify ''-rf'' to recursively force delete a directory and its contents on Linux, or ''/s'' to recursively delete a directory and its contents on Windows.|
|  |X:|(Where X is a drive letter) Switches to the selected drive.|
|cd|cd|Changes to the given directory, if one is given. If no directory is given, displays the current directory (Windows) or changes to your home directory (Linux). On Windows, a drive designator may be provided, in which case the current directory will be set on the indicated drive.|
|pwd|cd|Prints the current working directory.|
|cp|copy|Copy one or more files to a new name/location.|
|mv|move|Moves a file from one directory to another.|
|mv|ren<br />rename|Renames a file (on Linux, the filename and location are considered to be the same thing)|
|cat|type|Dumps the contents of a text file on the terminal (if there is a lot of text, the display will scroll; if the file is a non-text file, the results are undefined!)|
|more<br />less|more|Displays a file one screen at a time. (Linux: the less command is a more powerful version of the ''more'' command, which allows things like scrolling backwards)|
|cut| |Selects specific columns from a text file|
|sort|sort|Sorts a text file|
|diff|comp<br />fc|Shows the differences between (text) files|
|uniq| |Displays identical consequtive lines only once|
|tr| |Translates/replaces/deletes occurrences of characters|
|grep|find|Searches files for text|
|find| |Searches for files|
|touch|copy NUL: //filename//|Creates an empty file (Linux: if the file exists, ''touch'' will just update the date/time of modification).|
