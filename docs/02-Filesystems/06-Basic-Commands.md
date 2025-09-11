# Basic Commands for Dealing with Files and Directories 

Here are some basic commands for creating and removing files and
directories, changing and displaying the current directory, and
displaying a tree diagram of a directory hierarchy. We will look at
other commands in future topics.

| Description | Linux Command | Windows Command | Notes |
|:---         |:---          |:---              |:---   |
| Make a Directory | mkdir *directory* | mkdir *directory* | | 
| Remove a Directory (Must be empty)| rmdir *directory* | rmdir *directory*| | 
| Change (Working) Directory | cd *directory* | cd *directory* | | 
| Print Current Working Directory | pwd | cd | | 
| Change to Home Directory | cd | | | 
| List Contents of Directory | ls<br />ls -l | dir | Linux: -l option displays long listing (including permissions, ownership, size, modification date/time)| 
| Create an Empty File | touch *file* | copy nul *file* | |
| Remove/Delete a File | rm *file* | del *file* | | 
| Display a Tree Diagram starting at Current Directory | tree | tree<br />tree /f | Windows: /f causes tree to display files (otherwise only directories
are shown) | 
| Copy a file | cp *sourcefile* *destinationfile* | copy *sourcefile* *destinationfile* | | 
| Move or rename a file | mv *currentfilename* *newfilename* | move *currentfilename* *newfilename* | | 
| Display the text contents of a file | cat *file* | type *file* | Note: Using these commands on a file that contains non-text data may look very strange. |
